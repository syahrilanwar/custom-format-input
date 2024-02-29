<script>
export default {
  data() {
    return {
      showOption: true,
      newOption: null,
      items: [
        "TRANSACTION_CODE",
        "BRANCH_STORE_CODE",
        "DEPARTMENT_CODE",
        "PROJECT_CODE",
        "CUSTOMER_CODE",
        "DD",
        "MM",
        "YYYY",
        "NUMBER",
      ],
      options: [
        "TRANSACTION_CODE",
        "BRANCH_STORE_CODE",
        "DEPARTMENT_CODE",
        "PROJECT_CODE",
        "CUSTOMER_CODE",
        "DD",
        "MM",
        "YYYY",
        "NUMBER",
      ],
    };
  },
  methods: {
    deleteOption(index) {
      this.items.splice(index, 1);
    },
    addOption(option) {
      this.items.push(option);
    },
    createOption(option) {
      this.items.push(option);
    },
  },
};
</script>
<style src="./style/custom_format_input.css">
</style>
<template>
  <div>
    <div class="cfi">
      <div class="cfi-input">
        <div class="cfi-input-container">
          <div
            class="cfi-input-container-data"
            v-for="(item, index) in items"
            :key="index"
          >
            <div>{{ item }}</div>
            <button @click="deleteOption(index)">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="icon icon-tabler icon-tabler-xbox-x"
                width="12"
                height="12"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                fill="none"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <path stroke="none" d="M0 0h24v24H0z" fill="none" />
                <path
                  d="M12 21a9 9 0 0 0 9 -9a9 9 0 0 0 -9 -9a9 9 0 0 0 -9 9a9 9 0 0 0 9 9z"
                />
                <path d="M9 8l6 8" />
                <path d="M15 8l-6 8" />
              </svg>
            </button>
          </div>
        </div>
        <div @click="showOption = !showOption" class="cfi-input-btn-option">
          <svg
            v-if="!showOption"
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="20"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            fill="none"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <path stroke="none" d="M0 0h24v24H0z" fill="none" />
            <path d="M6 9l6 6l6 -6" />
          </svg>
          <svg
            v-if="showOption"
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="20"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            fill="none"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <path stroke="none" d="M0 0h24v24H0z" fill="none" />
            <path d="M6 15l6 -6l6 6" />
          </svg>
        </div>
      </div>
      <div class="cfi-input-option-container" v-if="showOption">
        <div class="cfi-input-option-container-create-data">
          <input type="text" v-model="newOption" />
          <button v-if="newOption" @click="createOption(newOption)">
            Create
          </button>
        </div>
        <div class="cfi-input-option-container-data">
          <div
            @click="addOption(option)"
            v-for="(option, idx) in options"
            :key="idx"
          >
            {{ option }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
