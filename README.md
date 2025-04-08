<div id="status" class="result"></div>

document.getElementById('status').textContent = "Processing...";
const response = await fetch('http://localhost:5000/upload', {
  method: 'POST',
  body: formData
});
document.getElementById('status').textContent = "";
try {
  const response = await fetch('http://localhost:5000/upload', {
    method: 'POST',
    body: formData
  });
  const result = await response.json();
  if (result.imageUrl) {
    document.getElementById('preview').innerHTML = `<img src="${result.imageUrl}" alt="Preview Image" />`;
  } else {
    document.getElementById('preview').textContent = 'Error: No image returned.';
  }
} catch (error) {
  document.getElementById('preview').textContent = 'Error uploading image.';
}
document.querySelector('input[type="file"]').addEventListener('change', function(event) {
  const file = event.target.files[0];
  if (file) {
    const reader = new FileReader();
    reader.onload = function(e) {
      document.getElementById('preview').innerHTML = `<img src="${e.target.result}" alt="Selected Image" />`;
    };
    reader.readAsDataURL(file);
  }
});

<!--
  This project was created with the help of ChatGPT by OpenAI.
  ChatGPT assisted in generating and improving the frontend code for image style transfer.
-->
### Acknowledgments

This project was developed with assistance from ChatGPT by OpenAI, used to generate and refine frontend code for image upload and style transfer functionality.
