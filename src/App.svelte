<script lang="ts">
  let textValue: string;

  const validateTildes = (text: string) => {
    const regex = /[áéíóúÁÉÍÓÚ]/;
    if (regex.test(text)) return true;
    return false;
  };

  const validateSpecialCharacters = (text: string) => {
    const regex = /[!@#$%^&*()_+\-=[\]{};':"\\|,.<>\/?]/;
    if (regex.test(text)) return true;
    return false;
  };

  const validateCapitalLetters = (text: string) => {
    const regex = /[A-Z]/;
    if (regex.test(text)) return true;
    return false;
  };

  const replaceWord = (word: string) => {
    word = word.replace(/a/g, "mj");
    word = word.replace(/e/g, "jki");
    word = word.replace(/i/g, "liki");
    word = word.replace(/o/g, "zam");
    word = word.replace(/u/g, "gfo");
    return word;
  };

  const restoreWord = (word: string) => {
    word = word.replace(/gfo/g, "u");
    word = word.replace(/zam/g, "o");
    word = word.replace(/liki/g, "i");
    word = word.replace(/jki/g, "e");
    word = word.replace(/mj/g, "a");
    return word;
  };

  const buttonEncript = (e: Event) => {
    e.preventDefault();

    if (validateTildes(textValue)) {
      alert("The accents are not allowed");
      textValue = "";
      return;
    }

    if (validateSpecialCharacters(textValue)) {
      alert("The special characters are not allowed");
      textValue = "";
      return;
    }

    if (validateCapitalLetters(textValue)) {
      alert("Captital latters are not allowed");
      textValue = "";
      return;
    }

    const wordMod = replaceWord(textValue);
    textValue = wordMod;
    return;
  };

  const buttonDecript = (e: Event) => {
    e.preventDefault();
    textValue = restoreWord(textValue);
  };
</script>

<div
  class="relative flex min-h-screen flex-col justify-center bg-teal-500 bg-opacity-90 py-6 sm:py-12"
>
  <div
    class="relative bg-white px-6 pb-9 pt-10 shadow-xl ring-1 ring-gray-900/5 sm:mx-auto sm:max-w-lg sm:rounded-lg sn:px-10"
  >
    <div class="mx-auto max-w-md">
      <div class="text-center">
        <h1 class="text-2xl text-gray-400">Encript/Decript</h1>
      </div>

      <div class="my-2 rounded-md border-2">
        <input
          bind:value={textValue}
          type="text"
          name=""
          id=""
          class="h-48 w-full focus:outline-none text-center text-gray-500 break-words"
        />
      </div>

      <div class="flex space-x-2 text-center text-white transition-all">
        <button
          on:click={buttonEncript}
          class="w-full bg-green-300 hover:bg-green-400 py-2">Encript</button
        >
        <button
          on:click={buttonDecript}
          class="w-full bg-purple-300 hover:bg-purple-400 py-2">Decript</button
        >
      </div>

      <div class="mt-2 bg-slate-50 py-2 text-center text-gray-400">
        <p>Please don't use, capital latter or strange symbols</p>
      </div>

      <div class="flex justify-center space-x-2 pt-3 text-center">
        <a href="https://github.com/vitalspace" target="_blank"
          ><img
            src="https://www.svgrepo.com/show/497210/instagram.svg"
            width="35"
            alt="instagram img"
          /></a
        >
        <a href="https://github.com/vitalspace" target="_blank"
          ><img
            src="https://www.svgrepo.com/show/507717/github-square.svg"
            width="35"
            alt="github img"
          /></a
        >
        <a href="https://github.com/vitalspace" target="_blank"
          ><img
            src="https://www.svgrepo.com/show/494209/linkedin.svg"
            width="35"
            alt="linkeding img"
          /></a
        >
      </div>
    </div>
  </div>
</div>
