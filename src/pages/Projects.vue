<template>
  <Layout>
    <h1>Projects</h1>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Error doloremque omnis 
    animi, eligendi magni a voluptatum, vitae, consequuntur rerum illum odit fugit
     assumenda rem dolores inventore iste reprehenderit maxime! Iusto.</p>
     <hr>
     <div class="grid">
    <div v-for="edge in $page.projects.edges" :key="edge.node.id" class="column">
    {{ edge.node.slug }}
       <b-card
    :title=edge.node.title
    :img-src=edge.node.cover.file.url
    img-alt="Image"
    img-top
    tag="article"
    
    class="mb-2"
  >
 

    <b-button :href=edge.node.slug variant="danger">View</b-button>
  </b-card>
    </div>
   </div>
  </Layout>


</template>

<page-query>
query {
  projects: allContentfulProject {
    edges {
      node {
        id
        title
        description
        slug
        date (format: "DD MM YYYY")
        cover{
          file{
            url
          }
        }
      }
    }
  }
  
}
</page-query>

<script>
import Navbar from '~/components/Navbar.vue'
import Item from '~/components/Item.vue'
export default {
  metaInfo: {
    title: 'Projectos'
  },
  components:{
    Navbar,
    Item
  }
  
}
</script>

<style lang="css" scoped>
.grid{
    display: grid;
    grid-template-columns: repeat(2,1fr);
    gap:1rem;
}



.column img{
    height: 300px;
    width: 100%;
    object-fit: cover;
    object-position: center;
}
</style>