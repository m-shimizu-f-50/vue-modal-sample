<template>
  <v-app>
    <v-card class="ma-4">
      <v-data-table :items="bookDate" :headers="headers" hide-default-footer>
        <template v-slot:[`item.edit`]="{ item }">
          <v-btn small color="success"> 編集 </v-btn>
        </template>
      </v-data-table>
    </v-card>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      headers: [
        {
          text: "ID",
          value: "id",
        },
        { text: "タイトル", value: "title" },
        { text: "内容", value: "content" },
        {
          text: "",
          value: "edit",
          sortable: false,
        },
      ],
      bookDate: [
        {
          id: 1,
          title: "ナルト",
          content: "面白い",
        },
        {
          id: 2,
          title: "鋼の錬金術師",
          content: "面白い",
        },
        {
          id: 3,
          title: "ワールドトリガー",
          content: "面白い",
        },
      ],
    };
  },
};
</script>

<style>
</style>