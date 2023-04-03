<script>
import Item from './Item.vue'
import axios from 'axios'

export default {
  name: 'Content',
  components: {
    Item
  },
  data () {
    return {
      data: null,
      isLoading: true,
      hasError: false
    }
  },
  mounted () {
    axios
        .get('https://api.github.com/users/joellesenne/repos', {
          headers: {
            'Accept': 'application/vnd.github.mercy-preview+json'
          }
        })
        .then(response => {
          this.data = this.filterProjects(response.data)
        })
        .catch(error => {
          console.log(error)
          this.hasError = true
        })
        .finally(() => {
          this.isLoading = false
        })
  },
  methods: {
    filterProjects (projects) {
      const projectNames = ['portfolio', 'projects', 'blog', 'lab', 'cv-resume', 'photos', 'dotfiles', 'joellesenne']
      return projects.filter(project => projectNames.includes(project.name))
    }
  }
}
</script>
<template>
  <article v-if="isLoading === true">
    <p>Loading...</p>
  </article>
  <article v-if="hasError === true">
    <p>Error</p>
  </article>

    <article class="grid" v-else>
      <section class="col" v-for="project in data" v-bind:key="project.id">
        <Item
            :title="project.name"
            :description="project.description"
            :urlLink="project.html_url"
            :tags="project.topics"
            :homepage="project.homepage"
            :language="project.language">
        </Item>
      </section>
    </article>

</template>

<style>
article {
  padding-top: 2rem;
}

.grid {
  display: grid;
  grid-template-columns: 1fr;
  grid-gap: 1rem;
}

@media screen and (min-width: 768px) {
  .grid {
    grid-template-columns: 1fr 1fr;
    grid-gap: 2rem;
  }
}

@media screen and (min-width: 640px) {
  .grid {
    grid-template-columns: 1fr;
    grid-gap: 2rem;
  }
}

.col {
  padding: 1rem;
  background-color: #2c3e50;
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
}

.col h2 {
  text-transform: uppercase;
  font-weight: 600;
  font-size: 1.5rem;
  letter-spacing: 0.025em;
}

.col p {
  margin-bottom: .5rem;
  font-size: 1rem;
}
</style>