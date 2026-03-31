<h1>Wedding Gift Registry System</h1>

<p>Welcome to our wedding gift registry! Here, you can find a variety of gifts that we would love to receive. Feel free to search through the gifts and find the perfect one!</p>

<h2>Search Gifts</h2>
<input type="text" id="search-box" placeholder="Search for gifts..." onkeyup="searchGifts()">

<ul id="gift-list"></ul>

<script>
const gifts = []; // This will hold the gift data from presentes.json

function loadGifts() {
    fetch('presentes.json')
        .then(response => response.json())
        .then(data => {
            gifts.push(...data);
            displayGifts(gifts);
        });
}

function displayGifts(giftArray) {
    const giftList = document.getElementById('gift-list');
    giftList.innerHTML = '';
    giftArray.forEach(gift => {
        const li = document.createElement('li');
        li.textContent = gift.name;
        giftList.appendChild(li);
    });
}

function searchGifts() {
    const query = document.getElementById('search-box').value.toLowerCase();
    const filteredGifts = gifts.filter(gift => gift.name.toLowerCase().includes(query));
    displayGifts(filteredGifts);
}

loadGifts();
</script>

<h2>PIX QR Code</h2>
<p>Use this PIX key to make your contributions:</p>
<p><strong>Chave PIX: 104..863.459-04</strong></p>
<img id="qr-code" alt="PIX QR Code" src="./generate_qr_code.php?key=104..863.459-04">
