# Viewing a ReactJS Vite Project Output on a Mobile Device

To view the output of a ReactJS project created with Vite on a mobile device, you need to ensure that your development server is accessible over your local network. Follow these steps to achieve this:

## 1. Find Your Local IP Address

- **On Windows**: Open Command Prompt and type `ipconfig`. Look for the IPv4 Address under your active network connection.
- **On Mac/Linux**: Open Terminal and type `ifconfig` or `ip addr show`. Look for the IP address associated with your active network connection.

## 2. Modify Vite Configuration (if needed)

By default, Vite should bind to `localhost`, which is not accessible from other devices on your network. You need to modify it to bind to your local IP address. In your `vite.config.js` or `vite.config.ts` file, you can specify the host.

```javascript
// vite.config.js
import { defineConfig } from "vite";
export default defineConfig({
  server: {
    host: "0.0.0.0",
  },
});
```

3. **Restart the Vite development server:**
   ```bash
   npm run dev
   ```

## 4. Run Your IP address On Mobile device

You will see Vite Project output.
