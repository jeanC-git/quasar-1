<template>
  <div class="q-px-lg q-pb-md">
    <q-timeline :layout="layout" class="secondary">
      <q-timeline-entry heading>Productos Apay</q-timeline-entry>
      <q-timeline-entry
        v-for="item in data"
        :key="item.id"
        :title="item.nombre"
        :subtitle="'Precio: '+item.precio"
        :avatar="item.foto"
        :body="item.descripcion"
      ></q-timeline-entry>
    </q-timeline>
  </div>
</template>



<script>
export default {
  computed: {
    layout() {
      return this.$q.screen.lt.sm
        ? "dense"
        : this.$q.screen.lt.md
        ? "comfortable"
        : "loose";
    }
  },
  data() {
    return {
      arrayTimeline: [
        {
          title: "Event Title Heading",
          entries: [
            {
              title: "Event title 1",
              subtitle: "subtitle 1",
              side: "left",
              avatar: "https://cdn.quasar.dev/img/avatar5.jpg",

              text:
                "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
            },
            {
              title: "Event title 2",
              subtitle: "subtitle 1",
              side: "right",
              icon: "mdi-code-tags",
              text:
                "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
            }
          ]
        },
        {
          title: "Event Title Heading 2",
          entries: [
            {
              title: "Event title 2 1",
              subtitle: " subtitle 2 1",
              side: "left",
              icon: "done_all",
              text:
                "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
            }
          ]
        }
      ],
      data: []
    };
  },
  created() {
    this.getApiData();
  },
  methods: {
    getApiData() {
      let vue = this;
      vue.$axios
        .get("http://apay.somadevoos.com/api/apiProducto")
        .then(response => {
          vue.data = response.data.data;
        });
    }
  }
};
</script>
