# Here is the way to handle array input in Python FastAPI.

```javascript
const formData = new FormData();
formData.append("title", "My Blog Title");
formData.append("content", "This is the content of the blog.");
formData.append("category", "Tech");
formData.append("image", fileInput.files[0]);

// Assuming tags is an array of strings like ["python", "fastapi", "webdev"]
const tags = ["python", "fastapi", "webdev"];
tags.forEach(tag => formData.append("tags", tag));

// Send the formData using fetch or axios
fetch("/api/blog", {
    method: "POST",
    body: formData,
}).then(response => {
    // Handle the response
});
```

```python
from fastapi import APIRouter, Form, File, UploadFile
from typing import Optional, List

router = APIRouter()

@router.post("/blog")
async def create_blog(
    title: str = Form(...),
    content: str = Form(...),
    category: str = Form(...),
    tags: Optional[List[str]] = Form(default=[]),
    image: Optional[UploadFile] = File(None),
):
    print("Received tags:", tags)  # Debugging: Check what FastAPI is receiving
    return {
        "title": title,
        "content": content,
        "category": category,
        "tags": tags,
        "image_filename": image.filename if image else None,
    }
```
