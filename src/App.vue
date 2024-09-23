<template>
  <div class="form_card">
    <div class="container">
      <h1>Feedback Form</h1>
      <p>
        We would love to hear your thoughts, suggestions, concerns or problems
        with anything so we can improve!
      </p>
    </div>
    <hr />
    <form @submit.prevent.enter="checkPass()" autocomplete="off">
      <div class="container">
        <label for="" class="feedback_form_label"> Feedback Type </label>

        <div class="radio_group">
          <div class="radio">
            <input
              id="comments_radio"
              value="Comments"
              v-model="picked"
              type="radio"
            />

            <label for="comments_radio">Comments</label>
          </div>

          <div class="radio">
            <input
              id="suggestions_radio"
              value="Suggestions"
              v-model="picked"
              type="radio"
            />

            <label for="suggestions_radio">Suggestions</label>
          </div>

          <div class="radio">
            <input
              id="questions_radio"
              value="Questions"
              v-model="picked"
              type="radio"
            />

            <label for="questions_radio">Questions</label>
          </div>
        </div>

        <label for="desc_area" class="description_label">
          Describe Your Feedback: <span style="color: red">*</span></label
        >
        <textarea
          spellcheck="false"
          name=""
          id="desc_area"
          cols="70"
          rows="10"
          required
        ></textarea>

        <div class="row">
          <div class="column">
            <label for="f_name" title="Please enter your first name"
              >FirstName<span style="color: red">*</span></label
            >
            <input id="f_name" type="text" v-model.trim="firstName" required />
            <p>First Name</p>
          </div>
          <div class="column">
            <label for="l_name">Last Name</label>
            <input id="l_name" type="text" v-model.trim="lastName" />
            <p>Last Name</p>
          </div>
        </div>

        <div class="row">
          <div class="column">
            <label for="email">E-mail<span style="color: red">*</span></label>
            <input id="email" type="email" v-model.trim="email" required />
            <p>example@example.com</p>
          </div>

          <div class="column">
            <label for="password"
              >Password<span style="color: red">*</span></label
            >
            <input
              autocomplete="off"
              id="password"
              type="password"
              v-model.trim="password"
              required
            />
            <p :style="{ color: pass_subtitle_color }">At least 6 characters</p>
          </div>
        </div>
      </div>

      <hr />

      <div class="center_tag">
        <button @click.enter="checkPass()">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      picked: "Comments",
      password: null,
      email: null,
      pass_subtitle_color: "#57647e",
    };
  },
  computed: {},
  methods: {
    checkPass() {
      this.pass_subtitle_color = this.password.length < 6 ? "red" : "#57647e";
    },
  },
};
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  background-color: rgba(128, 128, 128, 0.329);
  width: 100vw;
}

.container {
  padding: 0 50px;
}

.column {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  gap: 10px;
}

.center_tag {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
}

input[type="text"],
input[type="email"],
input[type="password"],
textarea {
  width: 100%;
  padding: 5px;
  font-size: 16px;
  border-radius: 5px;
  border: 1px solid #ccc;
  margin-bottom: 5px;
  resize: vertical;
  outline: none;
  border-color: #16aa52;
}

.radio {
  display: flex;
  align-items: first baseline;
  justify-content: center;
  gap: 3px;
}

#app {
  font-family: Arial, sans-serif;
  background-color: transparent;
  display: flex;
  align-items: center;
  justify-content: center;
  .form_card {
    width: 700px;
    margin: 50px auto;
    border-radius: 3px;
    padding: 50px 0;
    background-color: #f8f9fa;
    box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.1);

    h1 {
      font-size: 2em;
      color: #2c3345;
      margin-bottom: 5px;
      word-break: break-word;
      font-weight: 600;
      line-height: 1.25;
    }

    p {
      font-size: 1em;
      font-family: Arial, Helvetica, sans-serif;
      color: #57647e;
      margin-bottom: 40px;
      font-weight: 500;
      line-height: 1.6;
      word-break: break-word;
    }

    hr {
      margin-bottom: 30px;
      border: 0;
      height: 0;
      border-top: 1.5px solid #d7d8e1;
      border-bottom: 1.5px solid rgba(255, 255, 255, 0.3);
    }

    .radio_group {
      display: flex;
      align-items: baseline;
      justify-content: flex-start;
      gap: 120px;
      margin-bottom: 40px;
    }

    form {
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: flex-start;

      hr {
        margin-bottom: 40px;
        border: 0;
        height: 0;
        border-top: 1.5px solid #d7d8e1;
        border-bottom: 1.5px solid rgba(255, 255, 255, 0.3);
        width: 100%;
      }

      .feedback_form_label {
        display: block;
        margin-bottom: 15px;
      }

      .description_label {
        display: block;
        margin-bottom: 15px;
      }

      textarea {
        margin-bottom: 40px;
        text-decoration: none;
      }

      .row {
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        gap: 30px;
        margin-bottom: 20px;
        .column {
          width: 100%;
          p {
            font-size: 0.8em;
            color: #57647e;
          }
        }
      }

      button {
        font-size: 1em;
        min-width: 180px;
        padding: 10px 15px;
        background-color: #18bd5b;
        border-color: #18bd5b;
        color: white;
        border: 1px solid;
        font-family: inherit;
        font-weight: 500;
        padding: 0.75rem;
        outline: 0;
        border-radius: 4px;
        cursor: pointer;
      }

      button:hover {
        background-color: #16aa52;
      }
    }
  }
}
</style>
