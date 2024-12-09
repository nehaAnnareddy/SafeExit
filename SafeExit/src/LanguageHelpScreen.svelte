<!--
  Help Screen Component
  ---------------------
  - Displays safety actions: send location, report activity, access resources, and receive help.
  - Includes "Call 911" with confirmation popup and a "Back to Help Menu" button.
  - Bottom section links to human trafficking and domestic violence resources.
-->
<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
  
    let showPopup = false;
  
    function togglePopup() {
      showPopup = !showPopup;
    }
  
    function call911() {
      alert("Calling 911..."); 
      showPopup = false;
    }
  </script>
  
  <style>
    .help-screen {
        width: 730px;
        height: 920px;
        display: flex;
        flex-direction: column;
        align-items: center;
        background-image: linear-gradient(rgba(150, 150, 150, 0.202), rgba(78, 78, 78, 0.221)), url('/HelpBG.png');
        background-size: cover; 
        background-position: center; 
        border-radius: 20px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        position: relative;
        padding: 40px 40px;
        padding-bottom: 80px;
        image-rendering: auto; 
    }

  
    .top-section {
      display: flex;
      justify-content: space-between;
      align-items: center;
      width: 100%;

    }
  
    .shield {
        width: 150px;
        height: 150px;
        background: url('../public/Shield.png') no-repeat center;
        background-size: contain;
        position: relative; 
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .shield-text {
        position: absolute; 
        font-size: 20px; 
        font-weight: bold;
        color: black; 
        text-align: center;
        padding: 5px;
        line-height: 1.4; 
        white-space: normal; 
        max-width: 80%; 
        word-wrap: break-word; 
    }


    .send-location-box,
    .single-action-box,
    .dual-box-item,
    .icon-text-box {
        background-color: rgba(255, 255, 255, 0.58); 
        border-radius: 20px;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        font-weight: bold;
        text-align: center;
        color: #555;
        transition: background-color 0.3s ease;
    }

    .send-location-box div,
    .single-action-box div,
    .dual-box-item div,
    .icon-text-box div {
        color: #000;
        z-index: 1; 
    }


    .dual-box-item img,
    .icon-text-box img {
        z-index: 1; 
        position: relative;
    }


    .send-location-box:hover,
    .single-action-box:hover,
    .dual-box-item:hover,
    .icon-text-box:hover {
        background-color: rgba(255, 255, 255, 0.85); 
    }

    .red-circle {
      width: 120px;
      height: 120px;
      background-color: rgba(255, 0, 0, 0.279);
      color: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 20px;
      font-weight: bold;
      cursor: pointer;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
      transition: background-color 0.3s ease;
    }
    
    .red-circle:hover{
        background-color: rgba(180, 0, 0, 0.579);
    }
    .content {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 30px;
      width: 100%;
      margin-top: 20px;
    }
  
    .content:last-child {
        margin-top: 10px; 
        }

    .left-column {
        display: flex;
        flex-direction: column;
        gap: 20px;
    }

    .right-column {
        display: flex;
        flex-direction: column;
        gap: 20px;
    }


    .send-location-box {
        font-size: 20px; 
        background-color: rgba(255, 255, 255, 0.58); 
        height: 305px;
        border-radius: 20px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        cursor: pointer;
        font-weight: bold;
        color: #555;
        text-align: center;
    }

    .send-location-box img {
        max-width: 70%; 
        max-height: 70%; 
        object-fit: contain; 
        margin-bottom: 10px; 
    }


    .single-action-box {
        font-size: 20px; 
        min-height: 60px;
        background-color: rgba(255, 255, 255, 0.58); 
        border-radius: 20px;
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        cursor: pointer;
        font-weight: bold;
        color: #555;
        text-align: center;
        padding: 10px;
    }


    .dual-box-item {
        font-size: 18px;
        flex: 1; 
        aspect-ratio: 1;
        background-color: rgba(255, 255, 255, 0.58); 
        border-radius: 20px;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        cursor: pointer;
        text-align: center;
        padding: 5px;
        display: flex;
        flex-direction: column;
        align-items: center;
        font-weight: bold;
        color: #555;
    }

    .dual-box-item img {
        width: 50px;
        height: 50px;
        margin-bottom: 20px;
        margin-top: 10px;
    }


    .icon-text-box {
        background-color: rgba(255, 255, 255, 0.58);
        font-size: 18px;
        display: flex;
        align-items: center;
        gap: 10px;
        padding: 10px;
        border-radius: 20px;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        cursor: pointer;
        font-weight: bold;
        color: #555;
    }

    .icon-text-box img {
        width: 30px;
        height: 30px;
    }


    .content {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 40px; 
    }


    .dual-box {
        display: flex;
        gap: 20px;
        width: 100%;
    }
  
    .image-box {
        height: 140px; 
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #f4f4f4;
        border-radius: 20px;
        overflow: hidden;
        position: relative;
        height: 280px; 
        width: 100%; 
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        transition: transform 0.3s ease; 
    }

    .image-box:hover {
        transform: scale(1.05); 
    }

    .image-box img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .image-box .overlay-text {
        position: absolute;
        bottom: 5px;
        left: 50%;
        transform: translateX(-50%);
        color: white;
        font-size: 22px;
        font-weight: bold;
        padding: 10px 20px;
        border-radius: 10px;
        text-align: center;
        width: 90%; 
        max-width: 95%; 
        box-sizing: border-box; 
    }
    
    .popup {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 10;
    }
  
    .popup-content {
        background: rgba(255, 255, 255, 0.844);
        padding: 20px;
        border-radius: 10px;
        text-align: center;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    }
  
    .popup-buttons {
        display: flex;
        justify-content: space-around;
        margin-top: 10px;
    }
  
    .popup-button {
        background-color: #9a2c2cc9;
        color: white;
        border: none;
        border-radius: 5px;
        padding: 10px 20px;
        cursor: pointer;
    }
  
    .popup-button.cancel {
        background-color: gray;
    }

    a {
        text-decoration: none;
    }

    .back-button {
        margin-top: 30px;
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
        justify-content: center;
        position: center;
    }

    .back-button:hover {
        background-color: rgb(82, 66, 85);
        color: white; 
    }

  </style>
  
  <div class="help-screen">
    
    <!-- Top Section -->
    <div class="top-section">
        <div class="shield">
            <div class="shield-text">Help is<br>Here!</div>
          </div>
          
          
      <div class="red-circle" on:click={togglePopup}>Call 911</div>
    </div>
  
    <!-- Content Section -->
    <div class="content" style="margin-top: 20px;">
        <!-- Left Column -->
        <div class="left-column">
            <div class="send-location-box">
            <img src="/LocationAlert.png" alt="Location Icon">
            <div>Send Location Alert</div>
            </div>
            <div class="single-action-box">
            <div>Report Suspicious Activity</div>
            </div>
        </div>

    <!-- Right Column -->
    <div class="right-column">
        <div class="single-action-box">
        <div>I AM A VICTIM</div>
        </div>
        <div class="dual-box">
        <div class="dual-box-item">
            <img src="/Message.png" alt="Text Icon">
            <div>Text</div>
            <div>233-2733 </div>
        </div>
        <div class="dual-box-item">
            <img src="/Phone.png" alt="Call Icon">
            <div>Call</div>
            <div>888-373-7888</div>
        </div>
        </div>
        <a href="https://victimconnect.org/resources/search-resources/" target="_blank" rel="noopener noreferrer">
            <div class="icon-text-box">
            <img src="/Map.png" alt="Map Icon">
            <div>Resource Map</div>
            </div>
        </a>
        <div class="icon-text-box">
        <img src="/Help.png" alt="Help Icon">
        <div>Receive Help</div>
        </div>
    </div>
    </div>
  
    <!-- Bottom Section -->
    <div class="content" style="margin-top: 30px;">
        <a href="https://humantraffickinghotline.org/en" target="_blank" rel="noopener noreferrer">
        <div class="image-box">
            <img src="/image.png" alt="Human Trafficking">
            <div class="overlay-text">Human Trafficking</div>
          </div>
        </a>
        <a href="https://www.thehotline.org/" target="_blank" rel="noopener noreferrer">
          <div class="image-box">
            <img src="/image1.png" alt="Domestic Violence">
            <div class="overlay-text">Domestic Violence</div>
          </div>
        </a>
    </div>

    <div>
        <button class='back-button' on:click={() => dispatch('backToHelpMenu')}>Back to Help Menu</button>
      </div>
  
    <!-- Popup for 911 -->
    {#if showPopup}
      <div class="popup">
        <div class="popup-content">
          <p>Do you want to call 911?</p>
          <div class="popup-buttons">
            <button class="popup-button cancel" on:click={togglePopup}>Back</button>
            <button class="popup-button" on:click={call911}>Yes</button>
          </div>
        </div>
      </div>
    {/if}
  </div>
  