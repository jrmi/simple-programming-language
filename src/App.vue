<template>
   <div id="app">

      <!--b-navbar toggleable fixed="true" sticky="true" type="inverse" variant="success">
         <b-nav-toggle target="nav_collapse"></b-nav-toggle>
         <b-link class="navbar-brand" to="#">
            <span>Simple Programming Language</span>
         </b-link>
         <b-nav is-nav-bar class="ml-auto">
            <div class="btn-group">
               <button type="button" class="btn btn-success" v-bind:class="{ active: isSandboxCurrent }" v-on:click="setSandboxCurrent">Sandbox</button>
               <button type="button" class="btn btn-success" v-bind:class="{ active: isTutorialCurrent }" v-on:click="setTutorialCurrent">Tutorial</button>
               <button type="button" class="btn btn-success" v-bind:class="{ active: isReferenceCurrent }" v-on:click="setReferenceCurrent">Reference</button>
               <button type="button" class="btn btn-success" v-bind:class="{ active: isHomeCurrent }" v-on:click="setHomeCurrent">Home</button>
            </div>
         </b-nav>
      </b-navbar-->

      <!--router-view></router-view-->
      <keep-alive>
         <component v-bind:is="currentView" v-on:changeview="setCurrentView"></component>
      </keep-alive>

   </div>
</template>

<script>
   import sandbox from '@/components/Sandbox'
   import tutorial from '@/components/Tutorial'
   import reference from '@/components/Reference'
   import home from '@/components/Home'

   export default {
      name: 'app',
      components: {
         Sandbox: sandbox,
         Tutorial: tutorial,
         Reference: reference,
         Home: home,
      },
      data () {
         return {
            currentView: sandbox,
         }
      },
      mounted: function() {
         console.log('app mounted')
      },
      computed: {
         isSandboxCurrent: function() {
            return this.currentView === sandbox
         },
         isTutorialCurrent: function() {
            return this.currentView === tutorial
         },
         isReferenceCurrent: function() {
            return this.currentView === reference
         },
         isHomeCurrent: function() {
            return this.currentView === home
         },
      },
      methods: {
         setCurrentView: function(viewName) {
            if (viewName === 'sandbox') {
               this.currentView = sandbox
            } else if (viewName === 'tutorial') {
               this.currentView = tutorial
            } else if (viewName === 'reference') {
               this.currentView = reference
            } else if (viewName === 'home') {
               this.currentView = home
            }
         },

         setSandboxCurrent: function() {
            this.currentView = sandbox
         },
         setTutorialCurrent: function() {
            this.currentView = tutorial
         },
         setReferenceCurrent: function() {
            this.currentView = reference
         },
         setHomeCurrent: function() {
            this.currentView = home
         },
      },
   }
</script>

<style>

.CodeMirror {
  /* Set height, width, borders, and global font properties here */
  font-family: monospace;
  /*height: 300px;*/
  height: 100%;
  color: black;
}

html, body {
  width: 100%;
  height: 100%;
}

#app {
  width: 100%;
  height: 100%;

  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;

  display: flex;
  flex-direction: column;  
  justify-content: flex-start;

  align-items: stretch;
  align-content: stretch;
}

.a {
  color: #aedcae;
}

</style>
