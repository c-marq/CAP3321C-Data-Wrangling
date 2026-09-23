# Step-by-Step Guide: Build a No-Code Professional Headshot Generator

**Transform casual photos into professional headshots using Google AI Studio's Build mode**

*Updated September 23, 2026. Every button name, menu, model name, and link below was checked against the live Google AI Studio interface and Google's official documentation on this date.*

---

## What Changed Since the Last Version

| Then (2025) | Now (September 2026) |
|---|---|
| Nano Banana (`gemini-2.5-flash-image`) | **Nano Banana 2** (`gemini-3.1-flash-image`). The original Nano Banana **shuts down October 2, 2026**. |
| Left sidebar "Build" | Sidebar section **BUILD → New app** (or go straight to aistudio.google.com/apps) |
| "Deploy" button with a rocket icon | **Publish** button, top right |
| Cloud Run required a Google Cloud project with billing | New **Google Cloud Starter Tier**: publish up to 2 apps with **no billing account** |
| Default URL ending in `.run.app` | Optional custom URL like `your-app-name.ai.studio` |
| API key setup was manual | Your key is attached automatically as a server-side secret (`GEMINI_API_KEY`) |
| One suit-and-shirt outfit for everyone | **Identity Lock** in the prompt, plus an **outfit style picker** the user controls (see "Designing for Every User" in Step 3) |

---

## Read This First: What Is Free and What Is Not

This matters for anyone copying this project, so here it is up front.

| What you want to do | Cost | How |
|---|---|---|
| Build and preview apps in AI Studio Build mode | **Free** | Any Google account |
| Apps that use **text and vision** models (Gemini 3.8 Flash, Gemini 3.5 Flash-Lite) | **Free** (with daily rate limits) | Free tier API key, set up automatically |
| Apps that **generate images** with any Nano Banana model | **Paid** | Requires a paid API key. Google's pricing page lists every Nano Banana model as "Not available" on the free tier. |
| Generate a headshot yourself with Nano Banana 2 | **Free** (daily limits apply) | The **Gemini app** at gemini.google.com |
| Publish up to 2 apps to a public URL | **Free** | Google Cloud Starter Tier, no billing account |

> 💡 **WHY ARE WE DOING THIS?**
> Professor Marquez's in-class demo uses Nano Banana 2 on an instructor paid key so you can see the full image app working. **Students never need to pay.** Section "Student Free Path" below shows you two ways to get the same result for $0, and the Next Steps projects are designed to run entirely on free models.

---

## What You'll Build

A live web application that transforms casual selfies into professional corporate headshots using AI, published and accessible to anyone via a URL. Built entirely through "vibe coding": describing what you want in plain English.

**Time Required:** 20 to 30 minutes
**Cost:** Free to build. Image generation inside the app needs a paid key (see above).
**Coding Required:** None (AI generates all code for you)
**Tools Needed:** Google account, web browser, test photos

---

## Prerequisites

- A Google account (regular Gmail works fine)
- 3 to 5 portrait photos for testing (selfies, casual photos, etc.)
- Web browser (Chrome, Firefox, Safari, or Edge)
- Basic understanding of what makes a professional headshot

---

## Step 1: Open Google AI Studio and Go to Build Mode

> ✅ **DO THIS**
> 1. Open your web browser and go to **https://aistudio.google.com**
> 2. Sign in with your Google account
> 3. In the left sidebar, find the **BUILD** section and click **New app**
>    (Shortcut: go directly to **https://aistudio.google.com/apps**)
> 4. The first time you open Build mode, two welcome cards appear:
>    - "An updated flow for using Gemini in your apps" → click **Next**
>    - "Usage and costs" → click **Got it**
> 5. You should now see the heading **"Build your ideas with Gemini"** with a large prompt box

**The left sidebar today looks like this:**

| Section | Items |
|---|---|
| EXPLORE | Playground, History |
| BUILD | **New app**, My apps, Gallery |
| MANAGE | Dashboard, Documentation |

> 💡 **WHY ARE WE DOING THIS?**
> Build mode is Google's vibe coding environment. You describe an app in plain English and the AI agent writes the frontend, the server code, and the API connections for you. The Playground is different: it is for testing single prompts and model responses, not for building apps.

> ⚠️ **COMMON MISTAKE**
> Clicking **Playground** instead of **New app**. Playground is a chat for testing prompts. If you do not see "Build your ideas with Gemini," you are in the wrong place.

---

## Step 2: Get to Know the Build Screen

> ✅ **DO THIS**
> Look over the Build home screen before you type anything:
> - **Prompt box:** "Describe an app and let Gemini do the rest"
> - **➕ button** (bottom left of the box): attach files or **Import from GitHub**
> - **🎤 microphone:** dictate your prompt instead of typing
> - **I'm feeling lucky:** Gemini invents an app idea for you
> - **Suggestion chips** below the box. Scroll right with the arrow to see them all. Two matter for this project:
>   - **Create & edit images** ("Fast image generation & editing with Nano Banana 2")
>   - **Generate high-quality images** ("Studio-quality 4K images with Nano Banana Pro")
> - **⚙️ gear icon** (top right) opens **Advanced settings**:
>   - *Select model to use in Chat:* Default (Gemini 3.8 Flash). This is the model that writes your code.
>   - *Framework:* React
>   - *System instructions:* custom rules for your project
>   - *Usage:* shows whether you are on free tier requests, a paid key, or a Google AI subscription

> 💡 **WHY ARE WE DOING THIS?**
> Two different AI models are involved in every Build app. **Gemini 3.8 Flash** is the "developer" that writes your code (free). **Nano Banana 2** is the "photographer" your finished app calls to create the headshot (paid). Knowing which is which explains why building is free but running an image app is not.

---

## Quick Reference: The Playground's Run Settings

Before we build, it helps to know the controls on the right side of the **Playground** (EXPLORE → Playground). Build mode uses the same ideas behind the scenes.

| Setting | What it does | For this project |
|---|---|---|
| **Model** (top card) | Opens **Model selection**, with filters: All, Featured, Gemini, Live, Images, Video, Audio, Music, Agents, Gemma. Each card shows the model ID, what it's for, its price, and a **Paid** badge if it needs a paid key. | **Gemini 3.8 Flash** (`gemini-3.8-flash`) for text (free tier). Nano Banana models make images (paid in the API). |
| **System instructions** | A standing "job description" for the model. Choose **+ Create new instruction**, give it a Title, and write the rules. Instructions are saved in your browser (local storage). | "You are a professional headshot photographer and career coach..." (examples in class) |
| **Temperature** | How varied the answers are (shown on some models). Lower is more predictable, higher is more creative. | Leave the default. |
| **Thinking level** | How much the model reasons before answering: **Minimal, Low, Medium, High** (the levels offered vary by model). More thinking gives better answers to hard problems, but is slower and uses more tokens. | **Low** for quick rewrites, **Medium** (the 3.8 Flash default) for most work, **High** for planning an app or debugging |
| **Tools** | **Structured outputs** (return JSON), **Code execution** (runs Python), **Function calling** (connects to your own code), **Grounding with Google Search** (current facts from the web), **Grounding with Google Maps** (places), **URL context** (reads a web page you paste) | None are required for the headshot demo. Turn tools **off** unless you need them. URL context is handy for the portfolio project. |
| **Advanced settings** | **Media resolution** (Default, Low, Medium, High: how closely the model looks at images), **Safety settings**, **Add stop sequence**, **Output length** (maximum response size), **Top P** | Leave the defaults |
| **Get code** (top of the panel) | Shows the API code for your exact settings | Great bridge to our Python and Colab work |

> ⚠️ **COMMON MISTAKE**
> Leaving **Grounding with Google Search** on for every task. It can be on by default. Turn it off for creative writing or anything about *your own* content, so the model sticks to what you give it.

---

## Step 3: Write Your App Description Prompt

> ✅ **DO THIS**
> 1. Click in the prompt box ("Describe an app and let Gemini do the rest")
> 2. Paste the complete description below (Cmd+V on Mac, Ctrl+V on Windows)
> 3. Proofread it. As soon as there is text in the box, the button on the right changes from **I'm feeling lucky** to **Build ⌘ ↵**
> 4. Click **Build** (or press **Cmd+Enter** on Mac / **Ctrl+Enter** on Windows)

```
Build a professional headshot generator web app for college students and job seekers.

1. IMAGE UPLOAD: A clean drag-and-drop area for one photo (JPG or PNG, up to 10MB) with a preview of the uploaded photo. Helper text: "Upload a clear, well-lit photo where your face is visible."

2. STYLE CHOICES: After a photo is uploaded, show three simple controls before the transform button. Do not ask for or guess the person's gender. Let the user choose their own style.
   a) "Outfit style" (required, shown as selectable cards, with nothing pre-selected; keep the Transform button disabled until the user picks one):
      - Suit and tie: a tailored navy or charcoal suit jacket, crisp white collared shirt, and a solid silk tie
      - Suit, open collar: a tailored navy or charcoal suit jacket over a crisp white or light-blue collared shirt, top button open, no tie
      - Blazer and blouse: a tailored navy or charcoal blazer over a silk blouse in white, ivory, or soft blue
      - Blazer and simple top: a tailored blazer over a plain crew-neck or scoop-neck top
      - Dress with blazer: a structured sheath dress in navy, black, or charcoal with a tailored blazer
      - Business casual: a fine-knit sweater or a crisp button-down shirt, no jacket
      - Keep my outfit: keep the clothing from the original photo, just neaten it
   b) "Background" (default Neutral gray studio): Neutral gray studio, White studio, Light blue studio, Softly blurred modern office
   c) "Anything we should keep?" (optional text box). Placeholder: "e.g., my glasses, hijab, braids, beard, earrings"

3. AI TRANSFORMATION: When the user clicks "Transform to Professional Headshot", call Nano Banana 2 (model ID: gemini-3.1-flash-image) from the server with the uploaded photo. Output a 1:1 image at 2K resolution. Build the image prompt by filling the user's choices into this template:

"IDENTITY LOCK: This is an edit of the real person in the provided photo, not a new person. Preserve their exact facial features, face shape, skin tone, eye shape and color, eyebrows, age, gender presentation, hairstyle, hair length, hair texture and color, facial hair or lack of facial hair, makeup, and any glasses, head covering, or jewelry. Change only the clothing, lighting, background, and framing. Also keep: [ANYTHING WE SHOULD KEEP].

Subject and Composition: Create a photorealistic, high-resolution professional headshot of this person, framed from the chest up. Give them a confident, approachable expression with a subtle, genuine smile. Posture is upright and relaxed, with shoulders slightly angled toward the camera.

Attire: Dress the person in [OUTFIT STYLE DESCRIPTION]. The clothing is high-quality fabric, well-tailored, and fits this person's body naturally.

Studio Lighting: Soft key light with loop lighting to shape the face, gentle fill light to soften shadows, and a subtle rim light to separate the person from the background. Clear catchlights in the eyes.

Background: [BACKGROUND DESCRIPTION], clean and unobtrusive with a subtle gradient.

Photographic Specifications: Emulate a professional DSLR with an 85mm portrait lens at f/2.8. Eyes and face tack-sharp, background softly blurred. Natural skin texture, no plastic smoothing, no noise or artifacts."

4. USER INTERFACE: Professional design with a navy, gray, and white color scheme. Loading indicator with the message "Creating your headshot... (about 20 seconds)". Side-by-side before and after comparison. A "Download Headshot" button and a "Try Again" button that regenerates with the same choices. Mobile responsive.

5. ERRORS: If generation fails, show a friendly message and keep the user's photo and choices so they can try again without re-uploading.
```

> 💡 **WHY ARE WE DOING THIS?**
> This description tells the AI exactly what to build: the user flow, the exact model, the transformation prompt that defines photo quality, the design, and the error handling. Naming the **model ID** (`gemini-3.1-flash-image`) matters. If you only write "Nano Banana," the agent may pick an older model that is being shut down.

> ⚠️ **COMMON MISTAKE**
> Using the old model name `gemini-2.5-flash-image` from last year's version of this guide. That model **stops working on October 2, 2026**. Any app built with it will break on that date.

> ⚠️ **COMMON MISTAKE**
> A gray "ghost" suggestion sometimes appears at the end of your prompt with a **Tab** label. Ignore it. Pressing Tab accepts extra text you did not write.

### 🔍 Designing for Every User

Imagine writing this prompt the quick way: "Put the person in a dark suit jacket and a collared shirt, studio lighting, gray background." It might work great for the person who wrote it. Now imagine a whole class of different people using it. This is one of the best prompt engineering lessons in the whole project, so let's break it down like developers.

**What could go wrong with a one-size-fits-all prompt:**

1. **One default outfit for everyone.** The model may reshape the whole person to match the outfit, instead of dressing the person in the photo.
2. **Nothing protects identity.** A prompt that describes clothes, lights, and lenses in detail but says nothing about keeping the *person* lets faces and features drift. Google's own image editing guide says that to preserve critical details like a face, you must "describe them in great detail along with your edit request."
3. **One point of view.** A prompt quietly describes what its author would want. Every prompt carries the assumptions of whoever wrote it. That is bias, even when nobody intends it.

**How professional headshot apps handle this:** Some ask users to pick a gender (Canva offers female, male, or non-binary). Many others skip that question entirely and let users choose an **outfit style**, from dozens of options, instead.

**The design we chose (and why):**

| Fix | Where it lives | Why it works |
|---|---|---|
| **Identity Lock** paragraph at the top of the image prompt | The prompt | Tells the model to keep face, skin tone, hair, facial hair (or none), makeup, glasses, head coverings, **and gender presentation** exactly as they are in the photo, and to change only clothes, light, and background |
| **Outfit style picker** (suit and tie, blazer and blouse, dress with blazer, business casual, keep my outfit, and more) | The user interface | The user decides how they want to look. Nobody is forced into one "default" outfit. |
| **"Anything we should keep?"** text box | The user interface | Covers what a menu can't: hijab, braids, beard, a signature pair of glasses |
| **No gender question, no gender guessing** | The prompt | Asking can make people uncomfortable, and AI guessing can get it wrong. Matching the photo plus letting people pick their own style respects everyone. |

> 💡 **WHY ARE WE DOING THIS?**
> This is what "responsible AI" looks like in practice. The answer is not a better model. It is a better prompt and a better user experience, designed by thinking about **every** person who will use the app, not just the person building it.

> 🛑 **STOP AND CHECK**
> When you test your app in Step 5, test with photos of **different people**: different genders, skin tones, hairstyles, ages, and at least one person wearing glasses or a head covering. If any result changes who the person is, your prompt needs more work.

### 🎓 Student Free Path: Copy This App Without Paying

There is currently **no free Nano Banana model** in the Gemini API, so you cannot just swap one model name for another. Instead, pick one of these two free options.

**Option A (fastest): Make your headshot in the Gemini app.**
1. Go to **gemini.google.com** and sign in with any Google account
2. Upload your selfie
3. Paste the image prompt from Section 3 above (the part inside the quotation marks). Replace the three [BRACKETS] with your own choices, for example: "a tailored navy blazer over a silk blouse in ivory," "Neutral gray studio," and "my glasses."
4. Gemini uses **Nano Banana 2** on the free plan. Daily limits apply and reset each day.

**Option B (build your own free app): Replace Section 3 of the prompt.**
Build a "Headshot Prompt Coach" that uses a **free** model to write a custom headshot prompt for each person. Keep Sections 1, 2, 4, and 5 of the description above. Delete Section 3 and paste this in its place:

```
3. AI PROMPT COACH: Use Gemini 3.8 Flash (model ID: gemini-3.8-flash), which is available on the free tier. Do NOT use any image generation model. When the user clicks "Write My Headshot Prompt", send the photo and the user's style choices to the model and return:
   a) A short, kind assessment of the photo (lighting, framing, background, expression)
   b) A complete, ready-to-copy image prompt the user can paste into the free Gemini app (gemini.google.com). The prompt must start with an IDENTITY LOCK paragraph that preserves the person's exact face, skin tone, hair, facial hair or lack of it, makeup, glasses, head coverings, and gender presentation, and changes only clothing, lighting, background, and framing. Then include Subject and Composition, Attire (from the chosen outfit style), Studio Lighting, Background (from the chosen background), and Photographic Specifications.
   c) A "Copy prompt" button and a link that opens gemini.google.com in a new tab.
   Do not describe or guess the person's gender, race, or age in the assessment.
```

> 💡 **WHY ARE WE DOING THIS?**
> Option B is actually the heart of this course. Your app does not make the picture. It writes a **better prompt** than most people could write on their own, tailored to each person and career field. That is prompt engineering turned into a product, and it costs $0 to build and run.

> 🛑 **STOP AND CHECK**
> Before you click **Build**, confirm your prompt names a specific model ID. Instructor demo: `gemini-3.1-flash-image`. Student free version: `gemini-3.8-flash`.

---

## Step 4: Watch the AI Build Your Application

> ✅ **DO THIS**
> 1. After you click **Build**, the screen splits into two panels. The app title at the top center says **Untitled** until the agent names it.
> 2. **Left panel (Gemini chat):** shows the agent's plan, an **Action history** of every file it edits, and a summary when finished. The model and build time appear at the top (for example, "Gemini 3.8 Flash • Ran for 73s").
> 3. **Right panel:** the **Preview** tab shows your live app. Click the **`< >` Code** button to see the files.
> 4. Typical build time: **2 to 4 minutes** for this prompt (our test build took 200 seconds). While it runs, the chat shows each file as it's written, and the preview shows a "Loading your app / Enjoy these tips while you wait" carousel.
> 5. **When the build finishes, an "Upgrade to a paid API key" panel may appear** in the chat, along with a message asking you to select your API key. Nano Banana 2 needs a paid key. Click **Link a paid API key** → **Select key**. A **"Set Gemini API spend cap"** box follows: type a monthly limit (for example, $10) and click **Save**. The preview then loads your app.
> 6. If the preview stays on "Waiting for content," click the **↻ Reload the app** button in the preview toolbar, or refresh the browser page.

**What the AI creates (you can see these in the Code view):**

| File | What it does |
|---|---|
| `src/App.tsx`, `src/components/` | The React interface your users see |
| `server.ts` | Node.js server code that calls the Gemini API securely |
| `metadata.json` | Your app's name, description, and permissions |
| `package.json`, `vite.config.ts` | Project setup files |
| `.env.example` | Shows the `GEMINI_API_KEY` variable the app expects |

> 💡 **WHY ARE WE DOING THIS?**
> You are watching a full-stack application get written in real time: frontend, server, and API connection. Your API key is stored as a **server-side secret**, so it never appears in the browser where users could steal it. You can see it (masked) under **Settings (⚙️) → Secrets**.

> ⚠️ **COMMON MISTAKE**
> Closing the tab mid-build. Let the agent finish. If it reports an error, it usually fixes itself. If not, type "Fix any build issues with the current code" in the chat box.

> ⚠️ **COMMON MISTAKE**
> The chat shows **"Canceled"** and **"An internal error occurred."** with a **Retry** button. Click **Retry** once. If it fails again, open **⚙️ → Select model to use in Chat** and pick a different model (for example, Gemini 3.7 Flash), then click **Retry**. If *every* request fails, including a simple Playground chat, the problem is your account's usage source, not your prompt. See Troubleshooting.

---

## Step 5: Test Your Application in the Preview Window

> ✅ **DO THIS**
> 1. In the **Preview** tab, drag a test photo into the upload area (or click to browse)
> 2. Confirm the photo preview displays
> 3. Pick an **Outfit style**, a **Background**, and (optional) type something in **Anything we should keep?**
> 4. Click **Transform to Professional Headshot**
> 5. Wait 15 to 30 seconds while the loading indicator runs
> 6. Review the result, then test **Download Headshot** and **Try Again**
> 7. Use the device toggle at the top of the preview to check the mobile layout

**What to examine in the results:**

- Does the person still look like themselves? (Identity preservation is the #1 quality test. In our September 23 test, an AI-generated woman's photo with **Blazer and blouse** and **Neutral gray studio** selected came back as the same woman: same face, hair, and smile, in a navy blazer over a white top. It took under 30 seconds.)
- Is the upload process intuitive?
- Are loading states clear?
- Does the side-by-side comparison work?
- Can you download the final image?

> ⚠️ **COMMON MISTAKE**
> Image generation fails with a quota or "paid key required" message. That means your account is on free tier requests, and Nano Banana is paid only. **Instructor fix:** click **⚙️ → Usage** and select a paid API key. **Student fix:** use the Student Free Path in Step 3.

> 🛑 **STOP AND CHECK**
> Test at least 3 photos, including one tricky case: low light, a group photo, or a photo where the face is partly hidden. Note how the app handles each one.

---

## Step 6: Refine Your Application

> ✅ **DO THIS**
> Type changes in the chat box at the bottom left: **"Make changes, add new features, ask for anything"**. Then click the **↑ send arrow**. (In this box, **Enter** only adds a new line. It does not send.)
>
> **Improve transformation quality:**
> - "Make the professional attire look more natural and less artificially added"
> - "Make sure the person's face, skin tone, and hair are preserved exactly"
>
> **Improve the interface:**
> - Click the **annotation (pencil) icon** in the top right of the preview, highlight any part of your app, and describe the change you want
> - "Make the upload area larger and more prominent"
> - "Add a before/after slider instead of side-by-side comparison"
>
> **Add features:**
> - "Add a dropdown to choose background color: neutral gray, white, or light blue"
> - "Show a message if the photo doesn't contain a clear face"

> 💡 **WHY ARE WE DOING THIS?**
> Vibe coding is iterative. The agent remembers your whole project, so you can change one thing without breaking the rest. After each change, a **Checkpoint** appears in the chat with **View changes** and **Restore**, so you can always roll back.
>
> You can also edit code yourself. Click **`< >` Code**, open a file, and type. A bar appears at the bottom: **"Unsaved changes | View changes | Discard | Save."** Click **Save**. You'll see "Successfully saved changes," and the chat logs it as a **Manual edit**.

> ⚠️ **COMMON MISTAKE**
> Asking for five changes at once. Make one change, test it, then make the next. If something breaks, you will know exactly which change caused it and can click **Restore**.

---

## Step 7: Name, Describe, and Share Your App

> ✅ **DO THIS**
> 1. Your app name appears at the top center of the screen. To change it, type in the chat: *"Rename the app to Professional Headshot Generator and set the description to: Transform casual photos into professional headshots using AI."* (The agent updates `metadata.json`.)
> 2. To share a private test link, click **Share** (top right). The Share panel shows:
>    - **General access:** starts as "Restricted: Only people you specify can access"
>    - **People and groups with access:** type email addresses to invite testers
>    - **Settings:** "Default to fullscreen" and "Include your Gemini chat history"
>    - **Copy link** button
> 3. Read the note at the bottom of the Share panel carefully

> ⚠️ **COMMON MISTAKE**
> Sharing an image app without reading the warning. The Share panel says: *"Your app is using a pay-per-request Gemini API key. You may incur costs from users you share your app with."* Every image your testers create is billed to **your** key. Share image apps only with a small test group, or set a spend cap first (Step 11).

> 💡 **WHY ARE WE DOING THIS?**
> People you share with can use the app and also see and copy its code. That is great for classmates learning from each other. For a public, polished version, use **Publish** in Step 8.

---

## Step 8: Publish Your Application

The old "Deploy" rocket button is now **Publish**. There are two paths.

### Path A: Starter Tier (free, no billing account). Best for students.

> ✅ **DO THIS**
> 1. Click **Publish** in the top right corner
> 2. Read "What does publishing look like?" (chat history and code stay private; the app gets a public URL) and click **Get started**
> 3. Optional: enter a **Custom URL** such as `maria-portfolio.ai.studio`, or accept the suggested one
> 4. Click **Publish App**
> 5. Wait 1 to 3 minutes. AI Studio shows your live URL when it is done.

**Starter Tier limits:** up to **2 published apps**, deployed in a single region, no Google Cloud project or credit card required.

### Path B: Standard deployment (billing account). Instructor path.

> ✅ **DO THIS**
> 1. Click **Publish** → **Get started**
> 2. **Step 1: Confirm project and billing.** Choose the Google Cloud project where the app will live (for example, "Headshot Project") and confirm it shows a green check next to the billing account
> 3. Click **Continue** and follow the remaining steps (URL, then **Publish App**)

> 💡 **WHY ARE WE DOING THIS?**
> Publishing packages your app into a container on Google Cloud Run, gives it HTTPS, and scales it automatically from 1 user to thousands. That used to take DevOps expertise. Now it takes a few clicks.

> ⚠️ **COMMON MISTAKE**
> Publishing an **image** app publicly without thinking about cost. A published app uses **your** API key for every visitor's Gemini calls. A published text-only app on free models is fine. A published Nano Banana app can run up charges if it goes viral. Set a spend cap before publishing (Step 11).

> 🛑 **STOP AND CHECK**
> You have a live URL ending in `.ai.studio` or `.run.app`. Open it before moving on.

---

## Step 9: Test Your Live App

> ✅ **DO THIS**
> 1. Copy your live URL
> 2. Open a new **incognito/private** window and paste it
> 3. Test the full first-time visitor experience: load time, clarity, upload, transform, download
> 4. Open the URL on your phone and test upload and layout
> 5. Try 3 to 5 different photos

> 💡 **WHY ARE WE DOING THIS?**
> Incognito shows exactly what a new visitor sees: no cache, no sign-in, no saved settings. The live app runs on different infrastructure than the preview, so problems can show up here that never appeared in Build mode.

> ⚠️ **COMMON MISTAKE**
> A visitor sees **"403 Access Restricted."** According to Google's docs, this is usually a privacy browser extension (such as Privacy Badger) blocking the app, or a build issue. Try disabling the extension, or ask the agent to "fix any build issues with the current code" and publish again.

---

## Step 10: Share Your App and Gather Feedback

> ✅ **DO THIS**
> 1. Take screenshots: the upload screen, a before/after comparison, and the download button
> 2. Write a short post or email

**Example LinkedIn Post:**
```
I just built an AI-powered professional headshot generator without writing a single line of code.

I described the app in plain English in Google AI Studio's Build mode, and Gemini wrote the whole thing. It uses Nano Banana 2 to turn a casual selfie into a studio-quality headshot.

[Your App URL]

The biggest lesson: the quality of the app came down to the quality of my prompt.

#AI #PromptEngineering #MiamiDadeCollege
```

**Ask for specific feedback:**

- "Does the result still look like you?"
- "What would make this more useful?"
- "Would you actually use this for your LinkedIn photo?"

> 💡 **WHY ARE WE DOING THIS?**
> Building is half the value. The other half comes from real people using it and telling you what to improve. A shipped project with real feedback is also a much stronger portfolio piece than a tutorial you followed.

---

## Step 11: Monitor Usage and Control Costs

> ✅ **DO THIS**
> 1. In AI Studio, click **Dashboard** in the left sidebar (under MANAGE). You will see:
>    - **API Keys:** each key, its project, and its **Billing Tier** (for example, "Free tier" or "Tier 1 · Postpay")
>    - **Usage** and **Rate Limit:** how many requests you are making and your limits
>    - **Spend:** click **Create a spend cap** to set a monthly maximum (for example, $5 or $10)
>    - **Billing:** your billing account, costs this month, and any action-required notices
> 2. Standard deployments only: in the Google Cloud Console (console.cloud.google.com), go to **Cloud Run → your service → Metrics** for request counts, errors, and response times
> 3. When a class demo is over, consider **unpublishing** the app so it stops accepting traffic

> ⚠️ **COMMON MISTAKE**
> Ignoring the yellow banner at the top of the Dashboard. Google is moving Gemini API billing accounts to **prepay**. If you see a notice like "switch to prepay and buy credits by [date]," act on it before that date, or your paid API requests will fail until you buy credits.

> ⚠️ **COMMON MISTAKE**
> Assuming Google Cloud's $300 free trial credit covers AI Studio. According to Google's billing FAQ, those Welcome credits **cannot** be used to pay for AI Studio usage.

> 💡 **WHY ARE WE DOING THIS?**
> A spend cap is your safety net. If a shared link gets passed around or someone abuses your app, the cap stops charges before they surprise you.

---

## Step 12: Iterate Based on Feedback

> ✅ **DO THIS**
>
> **If users report quality issues:**
> 1. Open your app from **My apps**
> 2. Ask the agent to update the transformation prompt with the specific feedback (or edit it yourself in the Code view)
> 3. Test in Preview, then click **Publish** again to update the live app
>
> **If users request features:**
> - "Can I choose a background color?" → *"Add a dropdown to select background color: neutral gray, white, or light blue"*
> - "Can I get a LinkedIn-sized version?" → *"Add a button to crop the result to a square 400x400px image"*
> - "I'm not in a corporate field" → *"Add options for different professions: corporate, tech, healthcare, creative, education"*
>
> **To keep your code safe and portable:**
> - **Settings (⚙️) → GitHub:** create or link a repository and sync changes both ways
> - **Export** (top right of the Code view): download your app as a ZIP file

> 💡 **WHY ARE WE DOING THIS?**
> Real users find problems and ideas you never would. Version 2 is almost always better than version 1 because of what you learned from them.

---

## Understanding What You Built (Technical Deep Dive)

**Frontend (React)**
- Component-based web interface generated by the agent
- Drag-and-drop upload, image preview, loading states, download
- Responsive layout for desktop, tablet, and mobile

**Backend (Node.js server)**
- `server.ts` makes all Gemini API calls on the server side
- Your `GEMINI_API_KEY` is injected as a secret and is never sent to the browser
- Error handling for failed or slow requests

**AI Models**
- **Gemini 3.8 Flash** wrote your code (free)
- **Nano Banana 2** (`gemini-3.1-flash-image`) generates the headshot (paid: $0.067 per 1K image and $0.101 per 2K image on Google's pricing page as of September 23, 2026; check the pricing page for current rates)
- Every generated image carries an invisible **SynthID** watermark identifying it as AI-generated

**Hosting (Google Cloud Run)**
- Your app runs in a container that scales automatically and scales to zero when idle
- HTTPS is set up for you
- Starter Tier: no billing account, up to 2 apps. Standard: billed by usage, with a monthly free allowance (see the Cloud Run pricing page).

---

## Troubleshooting Common Issues

### Issue: "My app stopped working in October 2026"

**Cause:** It uses `gemini-2.5-flash-image`, which shuts down October 2, 2026.
**Solution:** Type in the chat: *"Update the image model to gemini-3.1-flash-image (Nano Banana 2)."* Test, then publish again.

---

### Issue: "Every request fails with 'permission denied' or 'An internal error occurred'"

**Cause:** This hits Build, app chat edits, and even a one-line Playground chat, so the problem is not your prompt. It's the account's **usage source** (free tier, a paid key, or a Google AI subscription), or a temporary Google-side problem.
**Solution:**
- Click **Retry** once, then try a different chat model (**⚙️ → Select model to use in Chat**)
- Check **aistudio.google.com/status** for incidents
- Open **⚙️ → Usage** and switch to a different source (for example, from a Google AI subscription to a paid API key, or back to free tier)
- Sign out and back in, or try an incognito window

---

### Issue: "My old app is read-only or asks me to 'Upgrade your app'"

**Cause:** Apps made before the 2026 Build update are marked **Legacy** and stored in Google Drive. They open read-only.
**Solution:** When prompted, **Upgrade your app to the new AI Studio Build experience** → **Confirm**. Leave "Delete this original app file from my Google Drive" unchecked to keep a backup copy.

---

### Issue: "Image generation fails or says I need a paid key"

**Cause:** Nano Banana models are not available on the free tier.
**Solution:**
- Instructors: **⚙️ → Usage** → select a paid API key
- Students: use the Student Free Path in Step 3 (Gemini app, or the Prompt Coach version)

---

### Issue: "Build mode isn't generating what I asked for"

**Cause:** The description is vague or missing key details.
**Solution:** Make sure your description includes the app's purpose, the user workflow, the exact model ID, and UI requirements. See "Prompt Engineering Is the Real Skill" below.

---

### Issue: "Shared or published link shows 403 Access Restricted"

**Cause:** A privacy browser extension or a build issue.
**Solution:** Disable extensions like Privacy Badger, or ask the agent to "fix any build issues with the current code" and reshare.

---

### Issue: "Transformations are slow or time out"

**Solution:**
- Ask the agent to *"compress images before sending them to the API"*
- Ask for *"1K resolution output"* instead of 2K or 4K
- Try **Nano Banana 2 Lite** (`gemini-3.1-flash-lite-image`), Google's fastest and cheapest image model, if quality is acceptable

---

### Issue: "The person doesn't look like themselves"

**Solution:**
- Add to the transformation prompt: *"Preserve the person's exact facial features, skin tone, hair texture, and identity. Change only the clothing, lighting, and background."*
- Use a clear, well-lit, front-facing source photo

---

### Issue: "Can't find the Deploy button"

**Cause:** It was renamed.
**Solution:** Click **Publish** in the top right corner of your app.

---

### Issue: "Publishing fails with a billing or permission error"

**Solution:**
- Students: use the Starter Tier path (no billing account needed). You can publish up to 2 apps. Unpublish one if you already have 2.
- Instructors on standard deployment: confirm the project shows a green check next to your billing account in **Step 1: Confirm project and billing**

---

## Prompt Engineering Is the Real Skill

Here is the most important lesson of this whole project: **the app is only as good as the prompt that describes it.** Two students can use the exact same tool and get wildly different apps. The difference is the prompt.

In our Delta framework, this is **Description**: clearly telling AI what you want, in enough detail that it cannot guess wrong.

### The Workflow: Draft Your Prompt Before You Open AI Studio

Spend 15 to 20 minutes building your prompt in **whatever free AI assistant you're most comfortable with**: Claude, Gemini, Microsoft Copilot, or ChatGPT. Then paste the finished prompt into AI Studio.

> ✅ **DO THIS**
> Copy this "prompt coach" template into your AI assistant and fill in the brackets:

```
You are an expert product designer and prompt engineer who has worked with hiring managers in [YOUR TARGET FIELD, e.g., healthcare IT / data analytics / hospitality management].

I want to build a web app in Google AI Studio's Build mode using a free Gemini model (gemini-3.8-flash). The app should: [ONE OR TWO SENTENCES ABOUT YOUR IDEA].

The people who will use it are: [WHO, e.g., recruiters looking at my profile / small business owners in Miami / nursing students].

Help me write a complete app description prompt. Before you write it, ask me up to 5 questions about my goals, my audience, and what would impress an employer in my field. Then write the prompt with these sections:
1. App purpose (one sentence)
2. Features, numbered
3. Exactly which AI model to use and what it should do
4. User interface and design (colors, layout, mobile)
5. User experience (instructions, loading messages, error messages)

Do not use any paid image generation models.
```

> 💡 **WHY ARE WE DOING THIS?**
> Letting the AI **interview you first** pulls out details you would never think to include. A recruiter in healthcare cares about different things than one in software, and your prompt should sound like it was written by someone who knows that field.

> 🛑 **STOP AND CHECK**
> Before you paste your prompt into AI Studio, check it against this list:
> - [ ] It says who the app is for
> - [ ] Every feature is numbered and specific
> - [ ] It names a **free** model ID (`gemini-3.8-flash`)
> - [ ] It describes the look (colors, layout, mobile)
> - [ ] It includes loading and error messages
> - [ ] Someone in your target field would read it and say "yes, that's useful"

---

## Next Steps: Expand Your Skills

Every project below is marked **FREE** (runs on free Gemini models) or **PAID** (needs an image model). Use the prompt coach workflow above to customize any of them for your career field.

### Project Idea 1: Virtual Profile / Career Portfolio App ⭐ FREE

**Why this matters:** Employers want proof, not just a resume. A virtual portfolio puts your class projects, your work outside school, and your skills in **one link** you can add to LinkedIn, your resume, and every job application. Building it with AI also *shows* an in-demand skill.

**What strong student portfolios have in common.** We studied two portfolios built by MDC Data Analytics students. Both earned attention from employers, and both follow the same pattern:

| Section | What it contains | Example from the MDC samples |
|---|---|---|
| **Hero** | Name, program, and a 2 to 3 sentence value statement, plus a "View My Work" button | "Completing a Bachelor's in Data Analytics... I enjoy transforming messy datasets into meaningful business insights." |
| **Links bar** | LinkedIn, GitHub, Tableau Public (or your field's equivalent) | Icons at the top of the page |
| **Projects, grouped** | Projects sorted by category or by tool | "Data Science / Data Analysis / Artificial Intelligence" or "Tableau / Python / Power BI / Applications" |
| **Project cards** | **Objective → Approach → Key Findings → Tools → Deliverables** | An NBA analysis that found "strong defense is the primary predictor of success" |
| **Honest credit** | What *you* did vs. what teammates did | "Part 1 was completed by me, Part 2 by a fellow student" |
| **About Me** | Education, interests, the roles you're targeting | "Seeking entry-level Data Analyst or Junior Data Scientist roles" |
| **Resume + Contact** | Downloadable resume and a professional email | "Get in touch at..." |

> 💡 **WHY ARE WE DOING THIS?**
> A portfolio website doesn't need AI to *run*. It just shows your content. That means we can build and publish it for **$0**: the free Gemini 3.8 Flash model writes the code, and the Starter Tier hosts it for free. The AI feature we add at the end (an "Ask about my work" assistant) also runs on the free model.

#### Step A: Gather your content first (15 to 20 minutes, in any AI assistant)

This is where the real work happens. Open **Claude, Gemini, Copilot, or ChatGPT** (whichever free one you like) and paste this:

```
You are a career coach and hiring manager who reviews portfolios for [TARGET ROLE, e.g., entry-level Data Analyst] positions in South Florida.

Interview me, one question at a time (maximum 10 questions), to collect everything I need for a professional portfolio website:
- my program, graduation date, and the role I'm targeting
- 3 to 5 projects (school or outside work): the problem, the data or materials, the tools I used, what I personally did, the results, and a link if I have one
- work, volunteer, or freelance experience that shows real-world skills
- my technical and soft skills
- my LinkedIn, GitHub, and other profile links

After the interview, write:
1. A 2 to 3 sentence hero statement in my voice (confident, no buzzwords, no "I am passionate")
2. Each project as a card: Title, Objective, Approach, Key Findings (with numbers where possible), Tools, My Role
3. A short About Me paragraph
4. A skills list grouped by category

Only use facts I give you. If something is missing, ask me instead of inventing it.
```

> ⚠️ **COMMON MISTAKE**
> Letting the AI invent results. Employers **will** ask about every project in an interview. If a number or a claim isn't true, delete it. The last line of the prompt above ("Only use facts I give you") is there for a reason.

#### Step B: Build the portfolio app in AI Studio

Go to **BUILD → New app** and paste this description. Replace everything in [BRACKETS], and paste your content from Step A where it says so.

```
Build a personal portfolio website for a college student applying to [TARGET ROLE] roles.

DESIGN: Clean, modern, and professional. Color scheme: [e.g., navy, white, and teal]. Mobile responsive. Easy for a recruiter to scan in 30 seconds.

SECTIONS (in this order):
1. HERO: My name, my program and graduation date, my hero statement, and a "View My Work" button that scrolls to Projects. Show a placeholder circle for my professional headshot that I can replace later.
2. LINKS BAR: Icon buttons for LinkedIn, GitHub, and [Tableau Public / Behance / other] that open in a new tab.
3. PROJECTS: Filter buttons by category ([e.g., Data Analysis, Data Science, AI Applications]). Each project is a card showing Title, Objective, Approach, Key Findings, Tools (as tags), and My Role. Clicking a card opens a detail view with a link to the project.
4. EXPERIENCE: Work, volunteer, and freelance experience as a short timeline.
5. SKILLS: Grouped skill tags.
6. ABOUT ME: My About Me paragraph and the roles I'm targeting.
7. RESUME AND CONTACT: A "Download Resume" button and a contact section with my professional email.

CONTENT: Use exactly the content below. Do not invent projects, numbers, employers, or skills.
[PASTE YOUR CONTENT FROM STEP A HERE]

Do not use any paid models. This site should not call any AI model yet.
```

#### Step C (optional): Add an "Ask About My Work" assistant for free

After the site works, add one feature through the chat box:

```
Add a small "Ask about my work" chat button in the bottom corner. Use Gemini 3.8 Flash (model ID: gemini-3.8-flash), which is on the free tier, called from the server. It should only answer questions using the content on this website, in a professional first-person voice. If it doesn't know, it should say "Great question. Please reach out to me directly" and show my email. Keep answers under 80 words.
```

> 🛑 **STOP AND CHECK**
> Before you publish, read every word on your site out loud. Is it true? Does it sound like you? Would you be comfortable if a hiring manager asked you about any line? Then publish with **Publish → Get started → Publish App** (Starter Tier, free) and put the link on your LinkedIn and resume.

**Swap-in lines for different career fields.** Replace the first line of the Step B prompt with one of these:

| Field | First line of your Step B prompt |
|---|---|
| Data Analytics | "...applying to entry-level Data Analyst or Business Intelligence roles. Emphasize dashboards, SQL, and business impact." |
| Software Development | "...applying to Junior Software Developer roles. Add a live demo link and a GitHub repo link on every project card." |
| Cybersecurity | "...applying to SOC Analyst or IT Security roles. Include a Certifications section (for example, Security+) above Projects." |
| Healthcare / Health IT | "...applying to Health Information or Clinical Data roles. Add a note that all project data was de-identified." |
| Business / Marketing | "...applying to Marketing Analyst or Business roles. Show results as before-and-after metrics (engagement, sales, reach)." |
| Creative / Design | "...applying to UX or Graphic Design roles. Make Projects a visual image grid with a case-study page for each piece." |

---

### Project Idea 2: Resume Reviewer with AI Feedback ⭐ FREE

**App description to use:**
```
Create a resume analysis app using Gemini 3.8 Flash (model ID: gemini-3.8-flash). Users upload their resume as a PDF and select their target job title. Gemini analyzes the resume and returns specific improvement suggestions for impact, clarity, and ATS (applicant tracking system) keyword optimization for that job title. Display results as a scored checklist with a "before and after" rewrite of the three weakest bullet points. Include a "Copy improved bullets" button.
```

**Why this matters:** Combines document processing with AI analysis and teaches you to work with PDFs and structured feedback. It's also a tool you and your classmates will actually use.

---

### Project Idea 3: Social Media Caption Generator ⭐ FREE

**App description to use:**
```
Create a social media caption generator using Gemini 3.8 Flash (model ID: gemini-3.8-flash). Users upload an image and select a platform (Instagram, LinkedIn, TikTok, X). Gemini analyzes the image and generates three platform-optimized caption variants with relevant hashtags. Add a toggle to generate captions in English, Spanish, or both.
```

**Why this matters:** Combines vision AI with text generation. The bilingual toggle makes it genuinely useful for South Florida businesses and creators.

---

### Project Idea 4: Voice-to-Task Manager ⭐ FREE

**App description to use:**
```
Build a voice-controlled task manager using the Gemini Live API. Users speak tasks like "Add dentist appointment tomorrow at 2pm" and the app extracts task name, date, time, and priority. Display tasks grouped by date with edit and delete options. Request microphone permission with a clear explanation of why it's needed.
```

**Why this matters:** Introduces voice interaction and structured data extraction. More complex than image apps, and a strong portfolio piece.

---

### Project Idea 5: Real Estate Photo Stager 💲 PAID (image generation)

**App description to use:**
```
Build a virtual staging app for real estate using Nano Banana 2 (model ID: gemini-3.1-flash-image). Upload photos of empty rooms and transform them into furnished, professionally staged spaces. Include style options: modern, traditional, minimalist, and coastal Miami.
```

**Free alternative:** Build it as a "Staging Prompt Coach" with Gemini 3.8 Flash that writes a staging prompt for each room photo, then paste that prompt into the free Gemini app.

**Why this matters:** Real estate staging is expensive. Virtual staging is a real business use case.

---

## Additional Resources

*All links checked September 23, 2026.*

**Official Documentation**
- Google AI Studio: https://aistudio.google.com
- Build Mode (New app): https://aistudio.google.com/apps
- Build Mode documentation: https://ai.google.dev/gemini-api/docs/aistudio-build-mode
- Publishing / deploying from AI Studio: https://ai.google.dev/gemini-api/docs/aistudio-deploying
- Google Cloud Starter Tier: https://docs.cloud.google.com/docs/starter-tier
- Nano Banana image generation: https://ai.google.dev/gemini-api/docs/image-generation
- Gemini API pricing (what's free vs. paid): https://ai.google.dev/gemini-api/docs/pricing
- Gemini API billing FAQ: https://ai.google.dev/gemini-api/docs/billing
- Model deprecation schedule: https://ai.google.dev/gemini-api/docs/deprecations
- Cloud Run documentation: https://cloud.google.com/run/docs
- Cloud Run pricing: https://cloud.google.com/run/pricing

**Learning Resources**
- Prompt design strategies: https://ai.google.dev/gemini-api/docs/prompting-strategies
- How to design better-looking apps in AI Studio: https://aistudio.google.com/learn/ai-ui-design-google-ai-studio
- Codelab: Deploy from AI Studio to Cloud Run: https://codelabs.developers.google.com/deploy-from-aistudio-to-run
- AI Studio App Gallery (remix ideas): https://aistudio.google.com/apps?source=showcase

**Free Image Generation**
- Gemini app: https://gemini.google.com
- Nano Banana 2 in the Gemini app: https://gemini.google/overview/image-generation/
- Gemini app limits by plan: https://support.google.com/gemini/answer/16275805

**Community**
- Google AI Developers Forum: https://discuss.ai.google.dev

---

## Success Checklist

**✅ Setup Phase**
- [ ] Signed in to Google AI Studio
- [ ] Found **BUILD → New app** and the "Build your ideas with Gemini" screen
- [ ] Checked **⚙️ → Usage** to see whether you're on free tier or a paid key

**✅ Building Phase**
- [ ] Wrote a complete app description with a specific model ID
- [ ] Generated the app and reviewed the files in the Code view
- [ ] Tested in Preview with at least 3 photos

**✅ Quality Assurance**
- [ ] Results preserve the person's identity
- [ ] Mobile layout works
- [ ] Loading and error messages are clear
- [ ] Refined at least once through chat or annotation mode

**✅ Publishing Phase**
- [ ] Published with **Publish** (Starter Tier or standard)
- [ ] Tested the live URL in incognito and on a phone
- [ ] Set a spend cap if the app uses a paid model

**✅ Understanding**
- [ ] Can explain the difference between the model that writes the code and the model the app calls
- [ ] Can explain which Gemini models are free and which are paid
- [ ] Can explain why prompt quality determines app quality

---

## Final Thoughts

You just went from "I can't build apps" to "I published a live AI application." That shift in identity matters more than the specific app you built.

**What you accomplished:**

1. **Learned vibe coding:** you can describe an app idea and have AI build it
2. **Understood AI integration:** you know the difference between code-writing models and the models your app calls
3. **Published to production:** your app runs on the same cloud infrastructure Fortune 500 companies use
4. **Practiced prompt engineering:** the skill that transfers to every AI tool you will ever use

**The pattern works for any application:**

1. Identify a problem people actually have
2. **Spend real time on the prompt.** Draft it with your favorite AI assistant, from the perspective of your career field.
3. Let AI generate the implementation
4. Test with real users
5. Iterate based on feedback
6. Publish and share

The tools will keep changing. Model names will change again next year. The skill of describing exactly what you want, clearly and specifically, will not.

**Keep building. Keep learning. Keep creating value.**

---

*This guide was created to empower students, professionals, and anyone curious about AI to become builders. Share it freely, modify it for your needs, and most importantly: use it to create something that helps people.*

— Carlos Marquez, Professor of Applied AI and Data Analytics, Miami Dade College

