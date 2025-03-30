<div class="main-box">
    <div>
        <a href="https://qzy.104.myftpupload.com/" class="link">
            <img src="https://raw.githubusercontent.com/Ishant2608/Wordpress-Project/refs/heads/main/Jicama%20Cafe%20and%20Desserts.jpg" width="250px" class="image">
            <p><b>Jicama Cafe and Desserts</b></p>
        </a> 
    </div>

    <div>
        <a href="https://znf.5a7.myftpupload.com/" class="link">
            <img src="https://raw.githubusercontent.com/Ishant2608/Wordpress-Project/refs/heads/main/Monster%20Dog.jpg" width="250px" class="image">
            <p><b>Monster Dog</b></p>
        </a>
    </div>
</div>

<!-- Popup Modal -->
<div id="popup" class="popup">
    <span class="close">&times;</span>
    <img id="popup-img">
</div>

<style>
.main-box {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    margin: auto;
    text-align: center;
}
.main-box div img {
    width: 100%;
    height: 600px;
    object-fit: cover;
    object-position: top;
    border-radius: 10px;
}
.popup {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.8);
    justify-content: center;
    align-items: center;
}
.popup img {
    max-width: 100%;
    max-height: 80%;
}
.popup .close {
    position: absolute;
    top: 20px;
    right: 30px;
    font-size: 30px;
    color: white;
    cursor: pointer;
}
</style>

<script>
    document.addEventListener("DOMContentLoaded", function () {
        const links = document.querySelectorAll(".link");
    
        links.forEach(link => {
            const url = link.href;
            const img = link.querySelector("img");
    
            fetch(url, { method: 'HEAD' })
                .then(response => {
                    if (!response.ok) {
                        throw new Error("404");
                    }
                })
                .catch(() => {
                    // If URL is broken (404), override click event
                    link.addEventListener("click", function (event) {
                        event.preventDefault();  // Prevent redirection
                        showPopup(img.src);
                    });
                });
        });
    });
    
    function showPopup(imgSrc) {
        const popup = document.getElementById("popup");
        const popupImg = document.getElementById("popup-img");
        popupImg.src = imgSrc;
        popup.style.display = "flex";
    
        document.querySelector(".close").addEventListener("click", function () {
            popup.style.display = "none";
        });
    }
    </script>
