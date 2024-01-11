<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Real-time Text Analyzer(APIwiz)</title>
  <style>
    body {
      font-family: 'Times New Roman', Times, serif
    }

    #textarea {
      width: 100%;
      height: 150px;
    }

    #results {
      margin-top: 10px;
    }
  </style>
</head>
<body>

  <h1>Real-time Text Analyzer(APIwiz)</h1>
  
  <textarea id="textarea" placeholder="Enter your text here..." oninput="analyzeText()"></textarea>

  <div id="results">
    <p>Number of Characters: <span id="charCount">0</span></p>
    <p>Number of Words: <span id="wordCount">0</span></p>
    <p>Number of Sentences: <span id="sentenceCount">0</span></p>
    <p>Number of Paragraphs: <span id="paragraphCount">0</span></p>
    <p>Number of Spaces: <span id="spaceCount">0</span></p>
    <p>Number of Punctuations: <span id="punctuationCount">0</span></p>
  </div>

  <script>
    function analyzeText() {
      //input text
      var text = document.getElementById("textarea").value;

      // Calculatation
      var charCount = text.length;
      var wordCount = text.split(/\s+/).filter(function (word) {
        return word.length > 0;
      }).length;
      var sentenceCount = text.split(/[.!?]+/).filter(function (sentence) {
        return sentence.length > 0;
      }).length;
      var paragraphCount = text.split('\n').filter(function (paragraph) {
        return paragraph.trim().length > 0;
      }).length;
      var spaceCount = text.split(' ').length - 1;
      var punctuationCount = text.replace(/[^\.\?!]/g, "").length;

      // Update the UI
      document.getElementById("charCount").innerText = charCount;
      document.getElementById("wordCount").innerText = wordCount;
      document.getElementById("sentenceCount").innerText = sentenceCount;
      document.getElementById("paragraphCount").innerText = paragraphCount;
      document.getElementById("spaceCount").innerText = spaceCount;
      document.getElementById("punctuationCount").innerText = punctuationCount;
    }
  </script>

</body>
</html>

