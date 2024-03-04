<script>
export default {
  props: {
    value: Array,
    options: Array,
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      showOption: false,
      newValue: null,
      parseValue: [],
      filteredOptions: this.options,
      focusOption: false,
    };
  },
  mounted() {
    this.parseValue = this.value;
    document.addEventListener("click", this.handleClickOutside);
    this.$emit("update-value", this.parseValue);
  },
  methods: {
    deleteOption(index) {
      if (!this.disabled) {
        this.parseValue.splice(index, 1);
      }
    },
    addValue(option) {
      if (!this.disabled) {
        this.parseValue.push(option);
      }
    },
    createValue(option) {
      if (!this.disabled) {
        if (option) {
          this.newValue = null;
          this.parseValue.push(option);
          this.filteredOptions = this.options;
        }
      }
    },
    handleClickOutside(event) {
      if (!this.disabled) {
        if (
          this.$refs.customFormatInput &&
          !this.$refs.customFormatInput.contains(event.target)
        ) {
          this.showOption = false;
        }
      }
    },
    beforeDestroy() {
      if (!this.disabled) {
        document.removeEventListener("click", this.handleClickOutside);
      }
    },
    inputEvent() {
      if (!this.disabled) {
        const inputElement = this.$refs.newValue;
        inputElement.style.width = inputElement.scrollWidth + "px";
        // filter
        if (this.newValue) {
          this.filteredOptions = this.options.filter((option) =>
            option.toLowerCase().includes(this.newValue.toLowerCase())
          );
        } else {
          this.filteredOptions = this.options;
        }
      }
    },
  },
};
</script>
<style>
.cfi {
  position: relative;
  width: 100%;
  min-width: 200px;
  line-height: normal;
}

.cfi-input {
  border: 0.06rem solid #ccc;
  padding: 0.225rem 0.25rem 0.225rem 0.25rem;
  border-radius: 0.35rem;
  display: flex;
  width: auto;
}

.cfi-input .disabled {
  opacity: 0.7;
  pointer-events: none;
}

.cfi-input-container {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  gap: 0.25rem;
  padding: 0.25rem 0.25rem 0.25rem 0.25rem;
}

.cfi-input-container input {
  border: none;
  outline: none;
  width: auto;
  max-width: 100%;
}

.cfi-input-container input[type="text"] {
  border: none;
  outline: none;
}

.cfi-input-container.disabled input[type="text"] {
  background-color: transparent;
  color: #777;
  cursor: not-allowed;
}

.cfi-input-container-data {
  display: flex;
  background-color: #e0e7ff;
  border: 0.06rem solid #c7d2fe;
  border-radius: 0.25rem;
  font-size: 0.65rem;
  padding: 0.1rem 0.3rem 0.1rem 0.5rem;
}

.cfi-input-container-data div {
  margin: auto;
}

.cfi-input-container-data button {
  margin: auto;
  cursor: pointer;
  display: flex;
  margin-left: 0.3rem;
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
  background-color: #ffffff;
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
  padding: 0.5rem 0.5rem 0.5rem 0.5rem;
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
</style>
<template>
  <div class="cfi" ref="customFormatInput">
    <div class="cfi-input" :class="{ disabled: disabled }">
      <div
        class="cfi-input-container"
        :class="{ disabled: disabled }"
        @click.prevent="$refs.newValue.focus()"
      >
        <div
          class="cfi-input-container-data"
          v-for="(item, index) in parseValue"
          :key="index"
        >
          <div>{{ item }}</div>
          <button
            :disabled="disabled"
            type="button"
            @click.prevent="
              deleteOption(index);
              $event.stopPropagation();
            "
            @mousedown.stop
          >
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
        <input
          type="text"
          ref="newValue"
          :disabled="disabled"
          @focus="showOption = true"
          v-model="newValue"
          @input="
            inputEvent();
            showOption = true;
          "
          @keyup.prevent.enter="createValue(newValue)"
        />
      </div>
      <div
        @click.prevent="showOption = !disabled ? !showOption : false"
        class="cfi-input-btn-option"
      >
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
      <div class="cfi-input-option-container-data">
        <div
          @click.prevent="
            addValue(option);
            $refs.newValue.focus();
          "
          v-for="(option, idx) in filteredOptions"
          :key="idx"
        >
          {{ option }}
        </div>
        <div
          @click.prevent="
            createValue(newValue);
            $refs.newValue.focus();
          "
          v-if="filteredOptions.length == 0"
        >
          {{ newValue }}
        </div>
      </div>
    </div>
  </div>
</template>
