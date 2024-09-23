<template>
  <div class="form_card">
    <h1>Feedback Form</h1>
    <p>
      We would love to hear your thoughts, suggestions, concerns or problems
      with anything so we can improve!
    </p>
    <hr />
    <form @submit.prevent="">
      <label for=""> Feedback Type </label>

      <div class="radio_group">
        <input
          id="comments_radio"
          value="Comments"
          v-model="picked"
          type="radio"
        />

        <label for="comments_radio">Comments</label>

        <input
          id="suggestions_radio"
          value="Suggestions"
          v-model="picked"
          type="radio"
        />

        <label for="suggestions_radio">Suggestions</label>

        <input
          id="questions_radio"
          value="Questions"
          v-model="picked"
          type="radio"
        />

        <label for="questions_radio">Questions</label>
      </div>

      <label for="desc_area">
        Describe Your Feedback:<span style="color: red">*</span></label
      >
      <textarea name="" id="desc_area" cols="70" rows="10" required></textarea>

      <div class="row">
        <label for="f_name" title="Please enter your first name"
          >First Name<span style="color: red">*</span></label
        >
        <input
          id="f_name"
          type="text"
          v-model.trim="firstName"
          required
          placeholder="First Name"
        />

        <input
          id="l_name"
          type="text"
          v-model.trim="lastName"
          placeholder="Last Name"
        />
      </div>

      <label for="email">Email<span style="color: red">*</span></label>
      <input
        id="email"
        type="email"
        v-model.trim="email"
        required
        placeholder="Email"
      />

      <button>Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      picked: null,
    };
  },
  computed: {},
  methods: {},
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
}

#app {
  font-family: Arial, sans-serif;
  margin: 0 350px;
  padding: 30px 30px;
  background-color: white;

  .form_card {
    max-width: 100vw;
    border-radius: 10px;
    background-color: #f8f9fa;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    position: relative;

    h1 {
      font-size: 2em;
      color: #000;
      margin-bottom: 10px;
    }

    p {
      font-size: 1em;
      color: #666666a6;
      margin-bottom: 20px;
      font-weight: 500;
    }

    hr {
      margin: 20px 0;
    }

    .radio_group {
      display: flex;
      align-items: baseline;
      justify-content: flex-start;

      gap: 5px;
    }

    form {
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: flex-start;

      label {
        display: block;
        margin-bottom: 5px;
      }

      input[type="text"],
      input[type="email"],
      textarea {
        width: 100%;
        padding: 5px;
        font-size: 16px;
        border-radius: 5px;
        border: 1px solid #ccc;
        margin-bottom: 10px;
        resize: none;
        border-color: #16aa52;
        outline-color: red;
      }

      input[type="radio"] {
        margin-right: 10px;
      }

      button {
        background-color: #007bff;
        color: white;
        border: none;
        padding: 10px 20px;
        border-radius: 5px;
        cursor: pointer;
      }

      button:disabled {
        background-color: #ccc;
      }

      .row {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 10px;
        margin-bottom: 20px;

        input[type="text"] {
          width: 100%;
        }

        input[type="email"] {
          width: 100%;
        }
      }

      hr {
        background-color: #666666a6;
        position: absolute;
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
