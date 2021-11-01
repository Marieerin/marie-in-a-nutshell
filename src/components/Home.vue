<template>
  <div>
    <!-- Hero Section -->
    <div class="hero">
      <h1> 
        Marie 
        <span>O'Shaughnessy</span>
      </h1>
      <p class="lead">Front End Developer and Artist</p>
    </div>

    <!-- Intro Section -->
    <div id="intro" class="wrapper">
      <div class="popUp">
        <h2>Welcome!</h2>
        <!-- v-for maps through projectInformation:
          - print out all of the project link & text
          - everything is inline in a span 
        -->
        <p>
          Check out a few snapshots of my work. I have worked with Figma, 
          <span v-for="(project, projects) in projectInformation">
            <a :href="project.link" :id="project.targetName">{{ project.content }} </a>
          </span>
          In addition I have experience with logo design and responsive web design. For more projects please checkout my <a href="https://github.com/Marieerin">GitHub</a>!
        </p>

        <!-- Popovers -->
        <!-- these are used to render images giving a preview to the project links above -->
        <b-popover :target="projectInformation[0].targetName" triggers="hover" placement="bottom">
          <img src="../assets/fomTree.png" />
        </b-popover>
        <b-popover :target="projectInformation[1].targetName" triggers="hover" placement="bottom">
          <img src="../assets/recipease.png" />
        </b-popover>
        <b-popover :target="projectInformation[2].targetName" triggers="hover" placement="bottom">
          <img src="../assets/nlEats.png" />
        </b-popover>
        <b-popover :target="projectInformation[3].targetName" triggers="hover" placement="bottom">
          <img src="../assets/sunshine.png" />
        </b-popover>
        <b-popover :target="projectInformation[4].targetName" triggers="hover" placement="bottom">
          <img src="../assets/postIt.png" />
        </b-popover>
        <b-popover :target="projectInformation[5].targetName" triggers="hover" placement="bottom">
          <img src="../assets/tarotUniverse.png" />
        </b-popover>
        <b-popover :target="projectInformation[6].targetName" triggers="hover" placement="bottom"> 
          <img src="../assets/portfolio.png"/>
        </b-popover>
      </div>
    </div>
    <div id="projects" class="wrapper">
    </div>
  </div>
</template>
<script>
  import popoverAndTarget from '@/components/popoverAndTarget'
  export default {
  data () {
    return {
      projectInformation: [
        {
          link: "https://www.linkedin.com/company/fomtree/about/", 
          targetName:"popover-target-1", 
          image:"../assets/fomTree.png",
          content:"React.js, Chakra UI,"
        },
        {
          link: "https://marie-and-george-project-four.github.io/recipease/", 
          targetName:"popover-target-2", 
          image:"",
          content:"jQuery, RESTful APIs,"
        },
        {
          link: "https://nleats.com/", 
          targetName:"popover-target-3", 
          image:"WordPress,",
          content:""
        },
        {
          link: "https://marieerin.github.io/marie-oshaughnessy-project-2/index.html", 
          targetName:"popover-target-4", 
          image:"",
          content:"Sass,"
        },
        {
          link: "https://marieerin.github.io/marie-oshaughnessy-project-5/", 
          targetName:"popover-target-5", 
          image:"",
          content:"Firebase, JS6,"
        },
        {
          link: "https://marieerin.github.io/tarot-universe-react-version/", 
          targetName:"popover-target-6", 
          image:"",
          content:"CSS3,"
        },
        {
          link: "https://marieerin.github.io/tarot-universe-react-version/", 
          targetName:"popover-target-7", 
          image:"",
          content:"and HTML5."
        },
      ]
    }
  },
  components: {
    popoverAndTarget
  },
  }
</script>