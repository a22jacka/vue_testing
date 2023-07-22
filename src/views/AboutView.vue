<script lang="ts">
export default {
  data: function() {
    return {
      //variables
      variable: 0 as any,
    }
  },
  methods: {
    //functions
    test: function() {
      return 0;
    }
  },
  mounted: function() {
    //called on start
    console.log("here");
  }
};
</script>

<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h2>The export default statement (most used)</h2>
    <div class="code">      
      <code>
        <span class="blue">export default</span> <span class="yellow">{</span><br>
        &nbsp;&nbsp;data: <span class="blue">function</span><span class="purple">() {</span><br>
        &nbsp;&nbsp;&nbsp;&nbsp;<span class="blue">return {</span><br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="green">//variables</span><br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;variable: 0 <span class="blue">as</span> any,<br>
        &nbsp;&nbsp;&nbsp;&nbsp;<span class="blue">}</span><br>
        &nbsp;&nbsp;<span class="purple">}</span>,<br>
        &nbsp;&nbsp;methods: <span class="purple">{</span><br>
        &nbsp;&nbsp;&nbsp;&nbsp;<span class="green">//functions</span><br>
        &nbsp;&nbsp;&nbsp;&nbsp;test: <span class="blue">function() {<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return</span> 0;<br>
        &nbsp;&nbsp;&nbsp;&nbsp;<span class="blue">}</span><br>
        &nbsp;&nbsp;<span class="purple">}</span>,<br>
        &nbsp;&nbsp;mounted: <span class="blue">function</span><span class="purple">() {</span><br>
        &nbsp;&nbsp;&nbsp;&nbsp;<span class="green">//called on start</span><br>
        &nbsp;&nbsp;&nbsp;&nbsp;console.log<span class="blue">(</span><span class="red">"started"</span><span class="blue">)</span>;<br>
        &nbsp;&nbsp;<span class="purple">}</span><br>
        <span class="yellow">}</span>;
      </code>
    </div>
    <div class="if">if v-if is false, the element literally doesn't exist, use v-show as alternative</div>
  </div>
</template>

<style scoped lang="scss">
@use '../assets/base.css';
.code {
  background-color: var(--color-background-mute);
  width: fit-content;
  padding: .3em;
  border: .4em solid var(--color-border);
  margin-left: 1em;
  border-radius: .7em;
  box-shadow: var(--wrapper-box-shadow);

  .blue { color: rgba(44, 122, 214, 1); }
  .yellow { color: rgba(255, 180, 23, 1); }
  .red { color: rgba(206, 145, 120, 1); }
  .purple { color: rgba(206, 112, 179, 1); }
  .green { color: rgba(54, 120, 85, 1); }
}

@media (max-width: 500px) {
  .code {
    margin: 0 auto;
  }
}
</style>
