<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="utf-8">
  <title>The Magical Cat Button</title>
</head>

<body>
  <button id="cat-button">magical cat button</button>
  <div id="images">
  </div>
  <script src="http://code.jquery.com/jquery-2.1.3.min.js"></script>
  <script type="text/javascript">
    // Assigning a function once user clicks button
    $("#cat-button").on("click", function() {

      // Links Cat API to code
      var queryURL = "http://api.giphy.com/v1/gifs/random?api_key=dc6zaTOxFJmzC&tag=cats";

      // Referencing external data and linking
      $.ajax({
        url: queryURL,
        method: "GET"
      })

      //  When done (Line 21-25), put stuff in response
      .done(function(response) {

        // Pulling the image from the json object
        var imageUrl = response.data.image_original_url;

        // Creating a variable to hold an image element  (Jquery self closes tag)
        var catImage = $("<img>");

        // Assing the source attribute to the image you created (Alt is for screen reading/assessibility)
        catImage.attr("src", imageUrl);
        catImage.attr("alt", "cat image");

        //
        $("#images").prepend(catImage);
      });
    });
  </script>
</body>

</html>
