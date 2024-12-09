<script>
    import { createEventDispatcher, onMount } from "svelte";
    const dispatch = createEventDispatcher();

    let showHand = false;
    let buttonHover = false;

    onMount(() => {
        // Toggle the visibility of the hand and simulate a click every 10 seconds
        setInterval(() => {
            showHand = true;
            buttonHover = true;
            setTimeout(() => {
                showHand = false;
                buttonHover = false;
            }, 1000); // Show hand and simulate hover for 1 second
        }, 10000); // Repeat every 10 seconds
    });

    function handleSOSClick() {
        dispatch("navigateToHelpMenu");
    }
</script>

<style>
    body {
        margin: 0;
        padding: 0;
        background-image: url('/public/woodWall.jpg'); /* Ensure the path is correct */
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }

    .poster-frame {
        width: 780px;
        height: 970px;
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
        background-image: url('/public/Hygiene.jpg'); /* Ensure this path works */
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
        width: 100px;
        height: 40px;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 16px;
        font-weight: bold;
        cursor: pointer;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        transition: transform 0.2s ease-in-out;
    }

    .sos-button:hover,
    .sos-button.hover {
        transform: scale(1.1); /* Make button larger on hover or simulated click */
    }

    .hand {
        position: absolute;
        bottom: 20px; /* Start above the SOS button */
        right: 20px;
        width: 50px;
        height: 50px;
        background-image: url('/public/handClick.png'); /* Replace with your hand icon path */
        background-size: contain;
        background-repeat: no-repeat;
        visibility: hidden; /* Hidden by default */
        opacity: 0; /* Invisible by default */
        transition: opacity 0.3s ease-in-out, visibility 0.3s ease-in-out;
        animation: none;
    }

    .hand.show {
        visibility: visible; /* Show when toggled */
        opacity: 1;
        animation: click 0.5s ease-in-out; /* Simulate hand click */
    }

    @keyframes click {
        0% {
            transform: translateY(0);
        }
        50% {
            transform: translateY(20px); /* Move down to click the button */
        }
        100% {
            transform: translateY(0); /* Move back up */
        }
    }
</style>

<div class="poster-frame">
    <div class="poster">
        <!-- Add interactive content or elements inside the poster if needed -->
    </div>
    <button
        class="sos-button {buttonHover ? 'hover' : ''}"
        on:click={handleSOSClick}
    >
        S O S
    </button>
    <div class="hand {showHand ? 'show' : ''}"></div>
</div>
