<script setup>
const user = useUserStore()

// Function to handle file upload
const handleFileUpload = (event) => {
  const file = event.target.files[0]
  if (file) {
    readFileContent(file)
  }
}

// Function to read the content of the uploaded file
const readFileContent = async (file) => {
  try {
    const content = await readFileAsync(file)
    // debugger
    user.value = JSON.parse(content)
  } catch (error) {
    console.error('Error reading file:', error)
  }
}

// Helper function to read file content asynchronously
const readFileAsync = (file) => {
  return new Promise((resolve, reject) => {
    const reader = new FileReader()
    reader.onload = (event) => resolve(event.target.result)
    reader.onerror = (error) => reject(error)
    reader.readAsText(file)
  })
}
</script>

<template>
  <div>
    <div
      class="flex flex-col items-center justify-center min-h-screen bg-gray-100 p-4"
    >
      <div class="w-full max-w-xs">
        <div class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
          <div class="mb-4">
            <label
              class="peer-disabled:cursor-not-allowed peer-disabled:opacity-70 block text-gray-700 text-sm font-bold mb-2"
              for="username"
            >
              Upload File
            </label>
            <input
              class="flex h-10 border-input bg-background text-sm ring-offset-background file:border-0 file:bg-transparent file:text-sm file:font-medium placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50 shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
              id="jsonFile"
              type="file"
              @change="handleFileUpload"
            />
          </div>

          <div class="mb-6 text-xs">
            <p>
              * Download the Sample JSON file, add your own data and upload it.
            </p>
            <p>
              * Or Copy the contents of the JSON file with your own data and add
              it as an Environment Variable named: <span>USER_DETAILS</span>.
            </p>
          </div>

          <div>
            <a
              class="inline-block align-baseline font-bold text-sm text-blue-500 hover:text-blue-800 transition-colors"
              href="/sample.json"
            >
              Download Sample File
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
