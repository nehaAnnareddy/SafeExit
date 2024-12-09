<script>
    import { createEventDispatcher, onMount } from "svelte";
    const dispatch = createEventDispatcher();
  
    const languages = [
      "I need help",
      "Necesito ayuda",
      "من به کمک نیاز دارم",
      "ខ្ញុំត្រូវការជំនួយ",
      "도움이 필요해요",
      "أنا بحاجة إلى مساعدة",
      "J’ai besoin d’aide",
      "Ich brauche Hilfe",
      "Ho bisogno di aiuto",
      "Мне нужна помощь",
      "助けが必要です",
      "我需要帮助",
      "मुझे मदद की ज़रूरत है",
      "Eu preciso de ajuda",
      "Εγώ χρειάζομαι βοήθεια"
    ];
  
    let visibleLanguages = [];
    let currentIndex = 0;
  
    onMount(() => {
      // Initialize visible languages
      visibleLanguages = languages.slice(0, 6);
  
      // Automatically scroll every 3 seconds
      const interval = setInterval(() => {
        scrollLanguages();
      }, 3000);
  
      return () => clearInterval(interval); // Cleanup interval on unmount
    });
  
    function scrollLanguages() {
      currentIndex = (currentIndex + 1) % languages.length;
  
      // Update visible languages with a cyclic scroll
      visibleLanguages = [
        ...languages.slice(currentIndex, currentIndex + 6),
        ...languages.slice(0, Math.max(0, (currentIndex + 6) - languages.length))
      ];
    }

    function selectLanguage(language) {
    dispatch("languageSelected", language); // Dispatch the selected language
  }

  </script>
  
  <style>
    .poster-frame {
      width: 780px;
      height: 970px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      background-color: white;
      border-radius: 20px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
      overflow: hidden;
      position: relative;
      padding: 20px 30px;
    }
  
    .poster-content {
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-image: linear-gradient(rgba(85, 85, 85, 0.2), rgba(95, 95, 95, 0.2)), url('/HelpBG.png');
        background-size: cover;
        background-position: center;
        border-radius: 10px;
        text-align: center;
        filter: brightness(1.2) contrast(1.1);
        }

  
    h1 {
      font-size: 24px;
      font-weight: bold;
      margin: 20px 0;
      color: #333;
    }
  
    .language-list {
      width: 90%;
      height: 70%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      overflow: hidden; /* Prevent scrolling */
      padding: 10px 0;
      position: relative;
    }
  
    .language-item {
      padding: 15px 20px;
      background-color: rgba(255, 255, 255, 0.3); /* Less opaque background */
      border-radius: 25px;
      text-align: center;
      font-size: 18px;
      font-weight: bold;
      color: #555;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      transition: transform 0.2s ease, background-color 0.2s ease;
      cursor: pointer;
      opacity: 1;
      transform: translateY(0);
      animation: scrollUp 3s linear infinite;
    }
  
    .language-item:hover {
      background-color: rgba(255, 255, 255, 0.9); /* Slightly brighter on hover */
    }
  
    .back-button {
      margin-top: 20px;
      padding: 10px 20px;
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 25px;
      font-size: 16px;
      cursor: pointer;
      transition: background-color 0.2s ease;
    }
  
    .back-button:hover {
      background-color: #0056b3;
    }
  
  </style>
  
  <div class="poster-frame">
    <div class="poster-content">
      <h1>Do you need help?</h1>
      <div class="language-list">
        {#each visibleLanguages as language (language)}
        <div
          class="language-item"
          on:click={() => selectLanguage(language)}
        >
          {language}
        </div>
      {/each}
      </div>
      <button class="back-button" on:click={() => dispatch("backToPoster")}>
        Back to Poster
      </button>
    </div>
  </div>
  