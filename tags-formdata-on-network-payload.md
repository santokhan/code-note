# Network Payload for FormData for multiple tags

### JavaScript Example

```javascript
const formData = new FormData();
formData.append('tags', 'tag1,tag2,tag3');

fetch('https://your-backend-endpoint.com/submit', {
  method: 'POST',
  body: formData
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

### Network Payload

In the Network tab of the browser's developer tools, you would see:

```
--boundary
Content-Disposition: form-data; name="tags"

tag1,tag2,tag3
--boundary--
```

Here, the `tags` field is sent as a single string with comma-separated values.
