<template>
  <navbar :pages="pages" :setActiveIndex="setActiveIndex"></navbar>
  <page-viewer :selectedPage="pages[activePageIndex]"></page-viewer>
  <create-page :formSubmitted="formSubmitted"></create-page>
</template>

<script>
import PageViewer from "./components/PageViewer.vue";
import Navbar from "./components/Navbar.vue";
import CreatePage from "./components/CreatePage.vue";

export default {
  components: { PageViewer, Navbar, CreatePage },

  created() {
    this.pages = !!this.pages && this.pages.filter((item) => item.isPublished);
  },

  data() {
    return {
      activePageIndex: 0,
      pages: [
        {
          link: { text: "Home", url: "index.html" },
          pageTitle: "Home Page",
          content: "This from Home page",
          isPublished: true,
        },
        {
          link: { text: "About", url: "about.html" },
          pageTitle: "About Page",
          content: "This from About page",
          isPublished: false,
        },
        {
          link: { text: "Contact", url: "contact.html" },
          pageTitle: "Contact Page",
          content: "This from Contact page",
          isPublished: true,
        },
      ],
    };
  },
  methods: {
    setActiveIndex(index) {
      this.activePageIndex = index;
    },

    formSubmitted(formObject) {
      this.pages.push(formObject);
    },
  },
};
</script>
