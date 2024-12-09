<!--
  SOS Poster Component
  ---------------------
  - Displays a poster background with an interactive "SOS" button.
  - Periodically highlights the button with a "hand" animation to draw attention.
  - Clicking the "SOS" button navigates to the help menu via dispatch.
-->
<script>
    import { createEventDispatcher, onMount } from "svelte";
    const dispatch = createEventDispatcher();

    let showHand = false;
    let buttonHover = false;

    onMount(() => {
        setInterval(() => {
            showHand = true;
            buttonHover = true;
            setTimeout(() => {
                showHand = false;
                buttonHover = false;
            }, 1000); 
        }, 10000); 
    });

    function handleSOSClick() {
        dispatch("navigateToHelpMenu");
    }
</script>

<style>
    body {
        margin: 0;
        padding: 0;
        background-image: url('/public/woodWall.jpg');
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }

    .poster-frame {
        width: 790px;
        height: 980px;
        display: flex;
        border-radius: 2%;
        justify-content: center;
        align-items: center;
        background-color: white;
        border: 5px solid #ddd;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        position: relative;
    }

    .poster {
        width: 100%;
        height: 100%;
        background-image: url('/public/Hygiene.jpg'); 
        background-size: cover;
        background-position: center;
        border-radius: 10px;
    }

    .sos-button {
        position: absolute;
        bottom: 20px;
        right: 20px;
        background-color: #882733;
        color: #ffffff;
        border: 2px solid #d43c4f;
        border-radius: 20px;
        width: 150px;
        height: 80px;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 16px;
        font-weight: bold;
        cursor: pointer;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        transition: transform 0.2s ease-in-out;
        font-size: 24px;
    }

    .sos-button:hover,
    .sos-button.hover {
        transform: scale(1.1); 
    }

    .hand {
        position: absolute;
        bottom: 20px;
        right: 20px;
        width: 50px;
        height: 50px;
        background-image: url('/public/handClick.png'); 
        background-size: contain;
        background-repeat: no-repeat;
        visibility: hidden;
        opacity: 0; 
        transition: opacity 0.3s ease-in-out, visibility 0.3s ease-in-out;
        animation: none;
    }

    .hand.show {
        visibility: visible; 
        opacity: 1;
        animation: click 0.5s ease-in-out; 
    }

    @keyframes click {
        0% {
            transform: translateY(0);
        }
        50% {
            transform: translateY(20px); 
        }
        100% {
            transform: translateY(0); 
        }
    }
</style>

<div class="poster-frame">
    <div class="poster">
    </div>
    <button
        class="sos-button {buttonHover ? 'hover' : ''}"
        on:click={handleSOSClick}
    >
        S O S
    </button>
    <div class="hand {showHand ? 'show' : ''}"></div>
</div>
