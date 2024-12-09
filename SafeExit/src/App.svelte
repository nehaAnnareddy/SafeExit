<script>
  import PosterInterface from './PosterInterface.svelte';
  import HelpMenu from './HelpMenu.svelte';
  import LanguageHelpScreen from './LanguageHelpScreen.svelte'; // New screen component

  let currentScreen = 'poster'; // Default screen
  let selectedLanguage = ''; // Track the selected language

  function navigateTo(screen, language = '') {
    currentScreen = screen;
    if (language) selectedLanguage = language; // Set the selected language
  }
</script>

<main>
  {#if currentScreen === 'poster'}
    <PosterInterface on:navigateToHelpMenu={() => navigateTo('help')} />
  {:else if currentScreen === 'help'}
    <HelpMenu
      on:backToPoster={() => navigateTo('poster')}
      on:languageSelected={(event) => navigateTo('languageHelp', event.detail)}
    />
  {:else if currentScreen === 'languageHelp'}
    <LanguageHelpScreen
      language={selectedLanguage}
      on:backToHelpMenu={() => navigateTo('help')}
    />
  {/if}
</main>
