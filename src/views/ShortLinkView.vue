<script lang="ts">
export default {
    data: function () {
        return {
            url: "",
            token: '161f899846a11dbb84d8c5d3209b50ce2579bb6d',
            error: "",
            groupID: '',
            showError: false,
            isLoading: false,
            errorTextBox: null as any,
            resultTextBox: null as any,
            justCopied: false,
        }
    },
    methods: {
        shortenUrl: async function () {
            this.errorTextBox = document.getElementById('error') as HTMLElement;
            this.resultTextBox = document.getElementById('result') as HTMLElement;
            this.resultTextBox.innerHTML = "";
            this.errorTextBox.innerHTML = "";
            this.showError = false;
            this.isLoading = true;
            const _this = this;
            //gets the input
            const input = document.getElementById('url_input') as HTMLInputElement | null;
            let validInput = "";
            if (input != null) {
                validInput = input.value;
            } else {
                this.error = "input was null";
            }
            //sets up and sends request
            const options = {
                method: "POST",
                headers: {
                    "Authorization": `Bearer ${this.token}`,
                    "Content-Type": "application/json"
                },
                body: JSON.stringify({ "long_url": validInput, "domain": "bit.ly", "group_id": this.groupID })
            };
            await fetch('https://api-ssl.bitly.com/v4/shorten', options)
                .then(response => response.json())
                .then(data => {
                    console.info(data.message, data.desription, data.resource);
                    //checks if it's an error based on messages recieved
                    if (data.message != null) {
                        _this.error = data.message;
                        _this.showError = true;
                        _this.isLoading = false;
                        return;
                    }
                    this.url = data.link;
                    //if there isn't an error print the link
                    if (!this.showError) {
                        this.resultTextBox.innerHTML = this.url;
                    }
                    this.isLoading = false;
                })
                .catch(error => {
                    this.showError = true;
                    this.error = error;
                });
            //otherwise open the error box
            if (this.showError) {
                this.resultTextBox.innerHTML = "Error occured";
                this.errorTextBox.innerHTML = this.error;
            }
        },
        copy: function () {
            navigator.clipboard.writeText(this.url);
        },
        copiedPopup: function () {
            const copy_button: HTMLElement = document.getElementById('copy_button') as HTMLElement
            copy_button.innerHTML = "Copied";
            copy_button.classList.add('copied');
            this.justCopied = true;

            setTimeout(() => {
                this.justCopied = false;
                copy_button.innerHTML = "Copy";
                copy_button.classList.remove('copied');
            }, 2500);
        }
    }
}
</script>

<template>
    <div class="wrapper">
        <h1>URL shortener</h1>
        <div class="u_input">
            <form v-on:submit.prevent="shortenUrl()">
                <input id="url_input" placeholder="https://example.com" />
                <button type="submit" id="shorten_button">Shorten URL</button>
            </form>
        </div>
        <div class="loading" v-show="isLoading">
            <img src="../images/loading.png" />
        </div>
        <div class="u_output">
            <textarea readonly rows="1" id="result" placeholder="new URL" />
            <textarea readonly rows="1" id="error" v-show="showError" />
            <button @click="copy(); copiedPopup();" id="copy_button" v-show="!showError">
                Copy
                <div class="copied" v-show="justCopied">
                    <span>Link Copied!</span>
                </div>
            </button>
        </div>
    </div>
    <div v-if="isLoading" style="position: absolute; bottom: 0;"><a href="https://www.flaticon.com/free-icons/loading"
            title="loading icons">Loading icons created by Freepik - Flaticon</a></div>
</template>

<style scoped lang="scss">
.wrapper {
    transform: scale(1.7);
    background-color: var(--color-background-mute);
    width: fit-content;
    padding: 0 .3em .3em .3em;
    border: .4em solid var(--color-border);
    margin: 0 auto;
    margin-top: 8em;
    display: flex;
    justify-content: center;
    flex-direction: column;
    border-radius: .5em;
    width: 30%;
    box-shadow: var(--wrapper-box-shadow);

    *:not(img, .copied) {
        width: 100%;
    }
}

button {
    background-color: var(--vt-c-divider-dark-2);
    border: .1em solid black;
    border-radius: 0 0 1em 1em;
}

.copied {
    background-color: var(--vt-c-green);
    bottom: 1em;
    width: 100%;
    display: flex;
    justify-content: center;
    border: none;

    span {
        text-align: center;
    }
}

.loading {
    display: flex;
    justify-content: center;

    img {
        width: 1.5em;
        aspect-ratio: 1 / 1;
        animation: load_icon 1s infinite linear;
        position: absolute;
    }
}

form {
    display: flex;
    justify-content: center;
    flex-direction: column;

    input {
        text-align: center;
        border-radius: 1em 1em 0 0;
        border: .1em solid black;
        border-bottom: none;
        padding: .2em;
    }

    button {
        aspect-ratio: 1 / .1;
        border-radius: 0 0 1em 1em;
    }
}

@keyframes load_icon {
    from {
        transform: rotate(0deg);
    }

    to {
        transform: rotate(359deg);
    }
}

textarea {
    resize: none;
    padding: 1em;
    text-align: center;
}

#error {
    display: block;
    background-color: var(--vt-c-error);
    color: var(--vt-c-white-soft);
}

#copy_button {
    display: block;
    width: 100%;
    height: 3em;
}

.u_output {
    margin-top: 1.6em;
}
</style>