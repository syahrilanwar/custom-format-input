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
<style>
.cfi {
  position: relative;
  width: 100%;
}

.cfi-input {
  border: 0.06rem solid #ccc;
  padding: 0.25rem 0.25rem 0.25rem 0.25rem;
  border-radius: 0.35rem;
  display: flex;
  width: auto;
}

.cfi-input-container {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  gap: 0.25rem;
  padding: 0.15rem 0.25rem 0.15rem 0.25rem;
}

.cfi-input-container-data {
  display: flex;
  background-color: #e0e7ff;
  border: 0.06rem solid #c7d2fe;
  border-radius: 0.25rem;
  font-size: 0.75rem;
  padding: 0.15rem 0.3rem 0.15rem 0.5rem;
}

.cfi-input-container-data div {
  margin: auto;
}

.cfi-input-container-data button {
  margin: auto;
  cursor: pointer;
  display: flex;
  margin-left: 0.75rem;
  padding: 0;
  border: none;
  background-color: transparent;
}

.cfi-input-container-data button:hover {
  color: #dc2626;
}

.cfi-input-btn-option {
  display: flex;
  justify-content: center;
  align-items: center;
  width: fit-content;
  font-size: 0.75rem;
  padding: 0.15rem 0.6rem 0.15rem 0.6rem;
  cursor: pointer;
}

.cfi-input-option-container {
  margin-top: 0.5rem;
  position: absolute;
  border: 0.06rem solid #ccc;
  font-size: 0.75rem;
  border-radius: 0.35rem;
  background-color: #f9f9f9;
  width: calc(100% - 0.065rem);
  z-index: 1;
  padding: 0.35rem 0rem 0.35rem 0rem;
}

.cfi-input-option-container-data {
  max-height: 12.5rem;
  overflow-y: auto;
}

.cfi-input-option-container-data::-webkit-scrollbar {
  width: 0.375rem;
}

.cfi-input-option-container-data::-webkit-scrollbar-track {
  background: #f1f1f1;
}

.cfi-input-option-container-data::-webkit-scrollbar-thumb {
  border-radius: 2rem;
  background: #9ca3af;
}

.cfi-input-option-container-data::-webkit-scrollbar-thumb:hover {
  background: #4b5563;
}

.cfi-input-option-container-data div {
  font-size: 0.75rem;
  padding: 0.25rem 0.5rem 0.25rem 0.5rem;
}

.cfi-input-option-container-data div:hover {
  background-color: #e0e7ff;
  cursor: pointer;
}

.cfi-input-option-container-create-data {
  font-size: 0.75rem;
  padding: 0.25rem 0.5rem 0.65rem 0.5rem;
  display: flex;
  gap: 0.5rem;
  border-bottom: 0.06rem solid #ccc;
}

.cfi-input-option-container-create-data input {
  border: 0.06rem solid #ccccccc4;
  padding: 0.25rem 0.5rem 0.25rem 0.5rem;
  border-radius: 0.25rem;
  font-size: 0.75rem;
  width: 100%;
}

.cfi-input-option-container-create-data input:focus {
  outline: 0.006rem solid #60a5fa;
}

.cfi-input-option-container-create-data button {
  border: 0.06rem solid #ccccccc4;
  padding: 0.25rem 0.5rem 0.25rem 0.5rem;
  font-size: 0.75rem;
  border-radius: 0.35rem;
}

.cfi-input-option-container-create-data button:hover {
  border: 0.06rem solid#c7d2fe;
  background-color: #e0e7ff;
}
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
