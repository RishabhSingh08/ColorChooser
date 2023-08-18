<script>
  var bgColor = "#ffffff";
  var userColor = "";

  function getColor() {
    bgColor = "#" + Math.random().toString(16).slice(2, 8);
    document.body.style.backgroundColor = bgColor;
  }

  function isValidHexColor(color) {
    var dummyElement = document.createElement("div");
    dummyElement.style.color = color;
    return dummyElement.style.color !== "";
  }

  const changeBGToUserColor = () => {
    const inputElement = document.querySelector(".color-input");

    if (isValidHexColor("#" + userColor)) {
      document.body.style.backgroundColor = "#" + userColor;
      bgColor = "#" + userColor;
      inputElement.classList.remove("border-red-500");
    } else {
      inputElement.classList.add("border-red-500");
      inputElement.classList.add("border-4");
    }
  };
</script>

<div
  class="flex flex-col items-center justify-center h-screen text-center w-100"
>
  <div
    class="p-8 rounded text-white text-2xl shadow-2xl backdrop-blur-xl"
    style="background-color: rgba(200, 200, 200, 0.5);"
  >
    <h1 class="font-bold text-6xl">
      {bgColor}
    </h1>

    <button
      on:click={getColor}
      style="background-color: rgba(255, 255, 255, 0.4);"
      class="p-2 rounded shadow-inner mt-3 w-10"
    >
      <img
        src="https://upload.wikimedia.org/wikipedia/commons/b/bc/Refresh_icon.png"
        alt=""
      />
    </button>

    <form action="javascript:void(0);">
      <div class="mt-5">
        # <input
          type="text"
          class="text-black w-32 rounded p-2 text-center border focus:border-blue-500 transition-colors duration-300 color-input"
          bind:value={userColor}
        />
        <button on:click={changeBGToUserColor} />
      </div>
    </form>
  </div>
</div>
