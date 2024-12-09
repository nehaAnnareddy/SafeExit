<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
  
    let showPopup = false;
  
    function togglePopup() {
      showPopup = !showPopup;
    }
  
    function call911() {
      alert("Calling 911..."); // Replace with actual functionality
      showPopup = false;
    }
  </script>
  
  <style>
  .help-screen {
    width: 780px;
    height: 970px;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-image: url('/HelpBG.png');
    border-radius: 20px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    position: relative;
    padding: 20px 30px; /* Added more padding on sides */
    overflow: hidden;
  }
  
    .top-section {
      display: flex;
      justify-content: space-between;
      align-items: center;
      width: 100%;
      padding: 10px;
    }
  
    .shield {
      width: 120px;
      height: 120px;
      background: url('/public/shield.png') no-repeat center;
      background-size: contain;
    }
  
    .red-circle {
      width: 100px;
      height: 100px;
      background-color: red;
      color: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 18px;
      font-weight: bold;
      cursor: pointer;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    }
  
    .content {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 30px;
      width: 100%;
      margin-top: 20px;
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

/* Send Location Alert (Square Box) */
.send-location-box {

  background-color: #f4f4f4;
  
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
  max-width: 70%; /* Prevents the image from taking up too much space */
  max-height: 70%; /* Ensures the image is proportional */
  object-fit: contain; /* Maintains aspect ratio */
  margin-bottom: 5px; /* Adds a slight gap between the image and text */
}


/* Report Suspicious Activity & I Am A Victim (Single Action Box) */
.single-action-box {
  min-height: 60px;
  background-color: #f4f4f4;
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

/* Text & Call (Dual Box Items) */
.dual-box-item {
  flex: 1; /* Ensure equal size */
  aspect-ratio: 1;
  background-color: #f4f4f4;
  border-radius: 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  text-align: center;
  padding: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  font-weight: bold;
  color: #555;
}

.dual-box-item img {
  width: 30px;
  height: 30px;
  margin-bottom: 5px;
}

/* Resource Map & Receive Help (Icon-Text Box) */
.icon-text-box {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px;
  background-color: #f4f4f4;
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

/* Gaps Between Boxes */
.content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px; /* Wider gap between boxes */
}

.image-box {
  height: 140px; /* Reduced height */
}

    .icon1-left {
        display: flex;
        align-items: center;
        justify-content: flex-start;
        gap: 10px;
        padding: 20px;
    }

    .icon1-left img {
        width: 40px;
        height: 40px;
    }

    .center-box img {
        width: 40px;
        height: 40px;
        margin-bottom: 10px;
    }

    .button-box2 img {
        width: 40px;
        height: 40px;
    }

    .dual-box {
      display: flex;
      gap: 20px;
      width: 100%;
    }
  
    .image-box {
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      align-items: center;
      background-color: #f4f4f4;
      border-radius: 20px;
      overflow: hidden;
      position: relative;
      height: 280px;
      font-size: 18px;
      font-weight: bold;
      color: white;
      text-align: center;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }
  
    .image-box img {
      width: 100%;
      height: auto;
      object-fit: cover;
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
      background: white;
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
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      padding: 10px 20px;
      cursor: pointer;
    }
  
    .popup-button.cancel {
      background-color: gray;
    }
  </style>
  
  <div class="help-screen">
    <!-- Top Section -->
    <div class="top-section">
      <div class="shield"></div>
      <div class="red-circle" on:click={togglePopup}>Call 911</div>
    </div>
  
 <!-- Content Section -->
  <div class="content">
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
        <div>233-2733 (Be Free)</div>
      </div>
      <div class="dual-box-item">
        <img src="/Phone.png" alt="Call Icon">
        <div>Call</div>
        <div>1-888-373-7888</div>
      </div>
    </div>
    <div class="icon-text-box">
      <img src="/Map.png" alt="Map Icon">
      <div>Resource Map</div>
    </div>
    <div class="icon-text-box">
      <img src="/Help.png" alt="Help Icon">
      <div>Receive Help</div>
    </div>
 </div>
 </div>
  
    <!-- Bottom Section -->
    <div class="content" style="margin-top: auto;">
      <div class="image-box">
        <img src="/image.png" alt="Human Trafficking">
        <div>Human Trafficking</div>
      </div>
      <div class="image-box">
        <img src="/image1.png" alt="Domestic Violence">
        <div>Domestic Violence</div>
      </div>
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
  