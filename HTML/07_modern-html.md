<!-- 

- data-* Attributes :
 --------------------
- data-* attributes allow you to store custom data directly on HTML elements.
- They are useful when JavaScript needs some information associated with an HTML element.

    <button data-user-id="101" data-role="admin">
        View User
    </button>

    - Accessing data-* using JavaScript :

    const button = document.querySelector("#btn");
    console.log(button.dataset.userId);
    console.log(button.dataset.role);

- Setting data : button.dataset.status = "active"; (data-status="active")
- Removing data : delete button.dataset.status;


- <details> :
 ------------
- <details> creates a native expandable/collapsible section.
- Usually you use it with <summary>.

        <details>
            <summary>What is HTML?</summary>

            <p>
                HTML is the standard markup language for creating web pages.
            </p>
        </details>

        ▶ What is HTML?

        ▼ What is HTML?

        HTML is the standard markup language...

- Open by default :

        <details open>
            <summary>HTML Information</summary>

            <p>This section is open initially.</p>
        </details>


- <summary> :
  -----------
- <summary> provides the visible label for a <details> element.
- <summary> is normally used as the first child of <details>:

        <details>
            ├── <summary> ← clickable heading
            └── content
        </details>


- <dialog> :
 ----------
- <dialog> represents a dialog box/modal.

        <dialog id="myDialog">
            <h2>Delete Account?</h2>
            <p>Are you sure you want to delete your account?</p>
            <button>Cancel</button>
            <button>Delete</button>
        </dialog>

- Opening a dialog With JavaScript:

        const dialog = document.querySelector("#myDialog");
        dialog.showModal();

- dialog.show(); Opens a non-modal dialog. The user can generally still interact with the rest of the page.

- dialog.showModal(); Opens a modal dialog. The dialog becomes the active interaction layer and the rest of the document is normally inert.

- dialog.close(); (Closing).  You can also give it a return value: dialog.close("confirmed"); -> console.log(dialog.returnValue); gives confirmed.

        <dialog id="dialog">
            <h2>Welcome</h2>
            <p>Welcome to our website.</p>
            <button id="closeBtn">Close</button>
        </dialog>

        <button id="openBtn">Open Dialog</button>

        <script>
            const dialog = document.querySelector("#dialog");

            document.querySelector("#openBtn").addEventListener("click", () => {
                dialog.showModal();
            });

            document.querySelector("#closeBtn").addEventListener("click", () => {
                dialog.close();
            });
        </script>


- <template> :
 -------------
- <template> contains HTML that is not rendered immediately.
- You won't immediately see the card on the page.
- The template acts like a reusable HTML blueprint.

    <template id="userTemplate">
        <div class="user-card">
            <h2>User Name</h2>
            <p>User Email</p>
        </div>
    </template>

- Imagine you need to generate 100 user cards.
- Instead of constructing HTML manually in JavaScript:
- you can define the structure in HTML. Then clone it with JavaScript.

        <template id="cardTemplate">
            <article class="card">
                <h2></h2>
                <p></p>
            </article>
        </template>

        Example :

        <template id="cardTemplate">
            <article class="card">
                <h2 class="name"></h2>
                <p class="email"></p>
            </article>
        >
        <div id="container"></div>

        const template = document.querySelector("#cardTemplate");
        const container = document.querySelector("#container");
        const card = template.content.cloneNode(true);
        card.querySelector(".name").textContent = "Rahul";
        card.querySelector(".email").textContent = "rahul@example.com";
        container.appendChild(card);

        <template>
            ↓
        HTML blueprint
            ↓
        cloneNode()
            ↓
        actual DOM


- <picture> :
 ------------
- <picture> is used when you need art direction or different image sources depending on conditions.

        <picture>
            <source media="(max-width: 600px)" srcset="mobile.jpg">

            <img src="desktop.jpg" alt="Mountain landscape">
        </picture>

        The browser can choose:
        - Mobile screen  → mobile.jpg
        - Desktop screen → desktop.jpg


- srcset :
  --------
- srcset allows you to provide multiple versions of an image so the browser can choose an appropriate one.

        <img
            src="image-800.jpg"
            srcset="
                image-400.jpg 400w,
                image-800.jpg 800w,
                image-1200.jpg 1200w
            "
            alt="Mountain"
        >

        - 400w = image resource is 400 CSS pixels wide


- <canvas> :
 ---------
- <canvas> provides a drawing surface that JavaScript can manipulate.
- Canvas itself doesn't automatically draw things. JavaScript does the drawing.

        <canvas id="myCanvas" width="500" height="300">
            Your browser does not support canvas.
        </canvas>

        <script>
            const canvas = document.querySelector("#canvas");
            const ctx = canvas.getContext("2d");

            ctx.fillRect(50, 50, 150, 80);
        </script>

        - getContext("2d") gives you a 2D drawing context.


- SVG :
  -----
- Scalable Vector Graphics
- SVG is an XML-based markup language for describing vector graphics.
- You can write SVG directly inside HTML.

        <svg width="200" height="200">
            <circle
                cx="100"
                cy="100"
                r="50"
                fill="blue"
            />
        </svg>

- <path> : <path> is one of the most powerful SVG elements.
- is used to define complex shapes.

        <path d="M 10 10 L 100 100" />



 -->