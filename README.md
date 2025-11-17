# Deno Serverless Proxy

A serverless proxy for Deno Deploy that allows you to proxy requests to any URL.

## 🚀 Deploy to Deno Deploy

### Option 1: Deploy via Dashboard

1. Go to [Deno Deploy Dashboard](https://dash.deno.com/new)
2. Select "Deploy from GitHub" or "Deploy from local"
3. Choose this repository or upload the `main.ts` file
4. Deployment will run automatically

### Option 2: Deploy via CLI

```bash
# Install Deno Deploy CLI (deployctl)
deno install --allow-read --allow-write --allow-env --allow-net --allow-run --no-check -r -f https://deno.land/x/deploy/deployctl.ts

# Deploy to Deno Deploy
deployctl deploy --project=your-project-name main.ts
```

## 📖 Usage

After deployment, you can access the proxy with this format:

```
https://your-project-name.deno.dev/[TARGET_URL]
```

### Usage Examples

**Proxy a website:**
```
https://quiet-wasp-17.deno.dev/https://example.com
```

**Proxy an API:**
```
https://quiet-wasp-17.deno.dev/https://api.github.com/users/denoland
```

**With query parameters:**
```
https://quiet-wasp-17.deno.dev/https://api.example.com/data?param=value&key=123
```

## ✨ Features

- ✅ Supports all HTTP methods (GET, POST, PUT, DELETE, etc.)
- ✅ Forwards headers and request body
- ✅ Supports query parameters
- ✅ CORS enabled by default
- ✅ Proper error handling
- ✅ Simple "Hello World" homepage

## 🧪 Local Testing

Run the server locally for testing:

```bash
# Using Deno task
deno task dev

# Or directly
deno run --allow-net --allow-env main.ts
```

Then access:
```
http://localhost:8000/https://example.com
```

## 🔒 Security Notes

This proxy is open and can access any URL. For production use:

1. Consider adding authentication
2. Implement rate limiting
3. Create a whitelist of allowed domains
4. Monitor usage to prevent abuse

## 📝 Example Requests with curl

**GET Request:**
```bash
curl https://quiet-wasp-17.deno.dev/https://api.github.com/zen
```

**POST Request:**
```bash
curl -X POST https://quiet-wasp-17.deno.dev/https://httpbin.org/post \
  -H "Content-Type: application/json" \
  -d '{"key":"value"}'
```

## 🛠️ Customization

You can modify `main.ts` to:
- Add authentication
- Restrict allowed domains
- Add caching
- Log requests
- Implement rate limiting

## 📄 License

MIT
