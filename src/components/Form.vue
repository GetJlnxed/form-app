<template lang="pug">
.form
  form(v-on:submit.prevent="submit", v-if="!submited")
    h2 Форма заявки...
    p.wrapper.wrapper--column
      label(for="name")
        | ФИО
        span *
      input(type="text", name="name", v-model="name")
    p.wrapper.wrapper--column
      label(for="e-mail")
        | e-mail
        span *
      input(type="text", name="e-mail", v-model="eMail")
    p.wrapper.wrapper--column
      label(for="phone")
        | Телефон
        span *
      input(type="text", name="phone", v-model="phone")
    p.wrapper.wrapper--column
      label(for="comment") Комментарий
      textarea(name="comment", v-model="comment")
    p.wrapper.wrapper--row
      input(type="checkbox", name="check", v-model="check")
      label(for="check")
        | Согласие на обработку данных
        span *
    input(type="submit", value="Отправить")
    p * - Обязательные поля
  h2(v-if="submited") Заявка отправлена
</template>

<script>
export default {
  name: "form",
  data() {
    return {
      name: "",
      eMail: "",
      phone: "",
      comment: "",
      check: false,
      submited: false,
    };
  },
  methods: {
    submit: function (e) {
      e.preventDefautl;
      const isvalid = this.checkValid();
      isvalid
        ? (this.submited = true)
        : alert("Нужно заполнить все обязательные поля");
    },
    checkValid: function () {
      if (!this.name || !this.eMail || !this.phone || !this.check) {
        return false;
      } else {
        return true;
      }
    },
  },
};
</script>

<style scoped>
.wrapper {
  display: flex;
}

.wrapper--column {
  flex-flow: column nowrap;
}

.wrapper--row {
  flex-flow: row nowrap;
}

.form {
  display: flex;
  flex-flow: column nowrap;
  justify-content: center;
  align-items: center;
}
</style>