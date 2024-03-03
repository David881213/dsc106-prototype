<script>
  let cipherTable = [
    // ... your cipher table data
  ];
  let transpositionKey = "84327615"; // The transposition key from the image.

  let plaintext = 'this is the prototype';
  let cipher = 'GXFGXGAFAFVVADXAAXAVFADAXFXVADVVAVDV';
  let keyword = '84327615'
  let solution = '';
  let feedbackMessage = '';
  let question = 'Try if you can decrpit the cipher!!'

  // Function to check the solution.
  function checkSolution() {
    // Convert both to lowercase and trim whitespace before comparing
    let formattedSolution = solution.replace(/\s+/g, '').toLowerCase();
    let formattedPlaintext = plaintext.replace(/\s+/g, '').toLowerCase();

    if (formattedSolution === formattedPlaintext) {
      feedbackMessage = 'Correct! Congratulations!!';
    } else {
      feedbackMessage = 'Wrong, try again.';
    }
  }

  // Example function to handle form submission.
  function handleSubmit() {
    checkSolution();
  }

  let showPlaintext = false;

  function togglePlaintext() {
    showPlaintext = !showPlaintext;
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400&display=swap');

  .container {
    display: flex;
    align-items: flex-start; /* Aligns items to the top */
    justify-content: space-between;
    padding: 20px; /* Adds padding around the container */
  }
  
  .form-container {
    flex-grow: 1; /* Allows the form container to grow */
    margin-right: 20px; /* Adds space between the form and the image */
  }

  form {
    margin-bottom: 20px; /* Adds space below the form */
  }

  .image-container {
    flex-basis: 45%; /* Sets the base size of the image container */
    text-align: right;
  }
  
  img {
    width: 100%; /* Sets the image width to take full width of its container */
    height: auto;
  }

  .open-sans-my-text-style {
    font-family: "Open Sans", sans-serif;
    font-optical-sizing: auto;
    font-weight: 400; /* Regular weight */
    font-style: normal;
    font-variation-settings: "wdth" 100;
  }

  .Cipher {
    font-size: 1.5em;
    font-weight: 600; /* Sets the font-weight to SemiBold */
    font-family: 'IBM Plex Sans', sans-serif; /* Sets the font-family */
    color: white;
    margin-top: 20px;
  }
</style>

<div class="container">
  <div class="form-container open-sans-my-text-style">

    <h2> {question}</h2>
    
    <!-- Display plaintext -->
    <h3>Cipher: {cipher}</h3>
    <h3>Key: {keyword}</h3>

    <!-- The form where the user can enter the solution -->
    <form on:submit|preventDefault={handleSubmit}>
      <label for="solution-input">Enter your solution:</label>
      <input id="solution-input" type="text" bind:value={solution} placeholder="Enter solution">
      <button type="submit">Check</button>
    </form>
    <!-- Display feedback message -->
    {#if feedbackMessage}
      <p>{feedbackMessage}</p>
    {/if}

    <button on:click={togglePlaintext}>
      {showPlaintext ? 'Hide Solution' : 'Show Solution'}
    </button>

    {#if showPlaintext}
      <p>Plaintext: {plaintext}</p>
    {/if}
    
  </div>

  <div class="image-container">
    <img src="ADFGVX1.png" alt="Cipher Table">
  </div>
</div>