<template>
  <div>
    <h1>{{ formTitle }}</h1>
    <form @submit.prevent="handleSubmit">
      <label for="pageTitle">Page Title:</label>
      <input type="text" id="pageTitle" v-model="pageTitle" /><br />
      <label for="content">Content:</label><br />
      <textarea id="content" v-model="content" rows="4" cols="50"></textarea
      ><br />
      <label for="linkText">Link Text:</label>
      <input type="text" id="linkText" v-model="linkText" /><br />
      <label for="url">URL:</label>
      <input type="text" id="url" v-model="url" /><br />
      <label for="isPublished">Published:</label>
      <input type="checkbox" id="isPublished" v-model="isPublished" /><br />
      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  props: {
    formSubmitted: {
      type: Function,
      required: true,
    },
  },
  data() {
    return {
      formTitle: "Page Creator",

      pageTitle: "",
      content: "",
      linkText: "",
      url: "",
      isPublished: true,
    };
  },
  methods: {
    handleSubmit() {
      const formData = {
        pageTitle: this.pageTitle,
        content: this.content,
        link: { text: this.linkText, url: this.url },
        isPublished: this.isPublished,
      };
      if (!this.pageTitle || !this.content) {
        alert("please fill all the required data");
      } else {
        this.formSubmitted(formData);
        clearForm();
      }
    },
    clearForm() {
      this.pageTitle = "";
      this.content = "";
      this.linkText = "";
      this.url = "";
      this.isPublished = true;
    },
  },
};
</script>
