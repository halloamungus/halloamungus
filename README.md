<!DOCTYPE html>
<html>
  <head>
    <title>Meine Webseite zum Senden</title>
    <meta charset="UTF-8" />
  </head>
  <body>
    <h1>Text senden</h1>
    <form id="sendeFormular">
      <label>Text:</label><br/>
      <input type="text" id="text" /><br/>
      <label>Wie oft senden (max 1000):</label><br/>
      <input type="number" id="anzahl" min="1" max="1000" value="1" /><br/>
      <label>Nummer (WhatsApp):</label><br/>
      <input type="text" id="nummer" placeholder="+491234567890" /><br/>
      <button type="button" onclick="senden()">Senden</button>
    </form>
    <script>
      function senden() {
        const text = document.getElementById('text').value;
        const anzahl = parseInt(document.getElementById('anzahl').value, 10);
        const nummer = document.getElementById('nummer').value;

        if (anzahl > 1000) {
          alert('Maximal 1000 x senden!');
          return;
        }

        for (let i = 0; i < anzahl; i++) {
          // WhatsApp-Link generieren
          const link = `https://wa.me/${nummer.replace(/\D/g,'')}?text=${encodeURIComponent(text)}`;
          window.open(link, '_blank');
        }
      }
    </script>
  </body>
</html>
