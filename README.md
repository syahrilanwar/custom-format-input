## Custom Format Input Vue

### Quick Installation with NPM

#### Installation

1. **Prepare Your Environment:**
   Make sure Node.js and NPM are installed on your machine. [Download and install from here](https://nodejs.org/).

2. **Install Custom Format Input Vue:**
   Use the NPM command to install.

   ```bash
   npm install custom-format-input-vue
   ```

#### Usage

1. **Import Custom Format Input Vue:**
   Import the Custom Format Input Vue into your project.

   ```javascript
    import Vue from "vue";
    import CustomFormatInputVue from "custom-format-input-vue";
    Vue.use(CustomFormatInputVue);
   ```

2. **Use Components:**
   Use the components you need in your project.

   ```html
   <template>
      <custom-format-input-vue
         :value="value"
         :options="options"
         @update-value="updateValue"
      />
    </template>

    <script>
    export default {
      data() {
        return {
          value: [],
          options: [
            "Option 1",
            "Option 2",
            "Option 3",
          ],
        };
      },
      methods: {
        updateValue(newValue) {
          this.value = newValue;
        },
      },
    };
    </script>
   ```

### Contribution

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.

### License

Licensed under [XYZ license]. See [LICENSE.md](LICENSE.md) for more details.

### Contact

Reach out to me at [syahrilanwar.dev@gmail.com] for questions or feedback.