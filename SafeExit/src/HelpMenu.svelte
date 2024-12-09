<!--
  Language Selection Component
  ----------------------------
  - Displays a list of languages users can select from, which scrolls automatically every 3 seconds.
  - Highlights the current set of languages
  - Allows users to select a specific language by clicking on it.
-->

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
      visibleLanguages = languages.slice(0, 6);
  
      // Automatically scroll every 3 seconds
      const interval = setInterval(() => {
        scrollLanguages();
      }, 3000);
  
      return () => clearInterval(interval);
    });
  
    function scrollLanguages() {
      currentIndex = (currentIndex + 1) % languages.length;
  
      // Update visible languages with a scroll
      visibleLanguages = [
        ...languages.slice(currentIndex, currentIndex + 6),
        ...languages.slice(0, Math.max(0, (currentIndex + 6) - languages.length))
      ];
    }

    function selectLanguage(language) {
    dispatch("languageSelected", language);
  }

  </script>
  
  <style>
    .poster-frame {
        width: 810px;
        height: 1000px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: white;
        border-radius: 20px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        overflow: hidden;
        position: relative;
    }
  
    .poster-content {
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-image: linear-gradient(rgba(90, 90, 90, 0.202), rgba(78, 78, 78, 0.221)), url('/HelpBG.png');
        background-size: cover;
        background-position: center;
        border-radius: 10px;
        text-align: center;
        filter: brightness(1.2) contrast(1.1);
        }

  
    h1 {
        font-size: 28px;
        font-weight: bold;
        margin: 20px 0px;
        color: #333;
        margin-bottom: 40px;
    }
  
    .language-list {
        width: 90%;
        height: 70%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        overflow: hidden;
        padding: 10px 0;
        position: relative;
    }
  
    .language-item {
        padding: 15px 20px;
        background-color: rgba(255, 255, 255, 0.3);
        border-radius: 25px;
        text-align: center;
        font-size: 18px;
        font-weight: bold;
        color: #000;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        transition: transform 0.2s ease, background-color 0.2s ease;
        cursor: pointer;
        opacity: 1; 
        transform: translateY(0);
        animation: scrollUp 3s linear infinite;
    }


    .language-item:hover {
        background-color: rgba(255, 255, 255, 0.9); 
        color: #000; 
    }

    .back-button {
        margin-top: 40px;
        width: 120px;
        height: 30px;
        padding: 10px 20px;
        background-color: rgb(131, 106, 136); 
        color: white; 
        font-weight: bold;
        border: none;
        border-radius: 15px;
        font-size: 16px;
        cursor: pointer;
        transition: background-color 0.2s ease;
    }

    .back-button:hover {
        background-color: rgb(82, 66, 85);
        color: white; 
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
      <div>
      <button class="back-button" on:click={() => dispatch("backToPoster")}>
        Back to Poster
      </button>
    </div>
    </div>
  </div>
  