<template>
  <div class="wrapper">
    <header class="main-head">The header</header>
    <nav class="main-nav">
      <MainNav>
      </MainNav>
    </nav>
    <article class="content">
      <h1>
        Main article area
      </h1>
      <p>
        In this layout, we display the areas in source order for any screen less that 500 pixels wide. We go to a two column layout, and then to a three column layout by redefining the grid, and the placement of items on the grid.
      </p>
    </article>
    <aside class="side">Sidebar</aside>
    <div class="date">Advertising</div>
    <footer class="title-area">The footer</footer>
  </div>
</template>

<script>
import MainNav from '@/navs/MainNav'

export default {
  name: 'CSSGrid',
  components: {
    MainNav
  },
  props: {
    text: String
  }
}
</script>

<style scoped>
.main-head {
  grid-area: header;
}
.content {
  grid-area: content;
}
.main-nav {
  grid-area: nav;
}
.side {
  grid-area: sidebar;
}
.date {
  grid-area: date;
}
.title-area {
  grid-area: footer;
}

.wrapper {
  display: grid;
  grid-gap: 20px;
  grid-template-areas:
    "header"
    "date"
    "nav"
    "content"
    "sidebar"
    "footer";
}

@media (min-width: 500px) {
  .wrapper {
    grid-template-columns: 3fr 1fr;
    grid-template-areas:
      "header  date"
      "nav     nav"
      "sidebar content"
      "time      footer";
  }
  nav ul {
    display: flex;
    justify-content: space-between;
  }
}

@media (min-width: 700px) {
  .wrapper {
    grid-template-columns: 1fr 4fr 1fr;
    grid-template-areas:
      "header header  header"
      "nav    content sidebar"
      "nav    content date"
      "footer footer  footer"
   }
   nav ul {
     flex-direction: column;
   }
}
</style>
