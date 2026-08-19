# HTML-CSS-intervyu-2
Elementni ota-ona (parent) ichida markazlash uchun eng mashhur usullar:

Usul 1: Flexbox (Eng keng tarqalgan)

CSS
.parent { display: flex; justify-content: center; align-items: center; height: 100vh; }
Usul 2: CSS Grid

CSS
.parent { display: grid; place-items: center; height: 100vh; }
Usul 3: Absolute Positioning (Transform)

CSS
.child { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); }
Usul 4: Margin Auto (Display block elementlar uchun)

CSS
.parent { display: flex; } /* yoki grid */
.child { margin: auto; }
Usul 5: Inline-block (Eski usul)

CSS
.parent { text-align: center; }
.parent::before { content: ""; display: inline-block; height: 100%; vertical-align: middle; }
.child { display: inline-block; vertical-align: middle; }
Kontent kam bo'lganda ham footer doimo sahifa tubida qolishi uchun eng yaxshi usul Flexbox'dir:

CSS
body { display: flex; flex-direction: column; min-height: 100vh; margin: 0; }
main { flex: 1; } /* Kontent maydonini kengaytirib, footerni pastga itaradi */
footer { flex-shrink: 0; }
Grid bu layout uchun eng mukammal vositadir:

CSS
.container {
    display: grid;
    grid-template-areas:
        "header header header"
        "sidebar-left content sidebar-right"
        "footer footer footer";
    grid-template-columns: 200px 1fr 200px;
    min-height: 100vh;
}
.header { grid-area: header; }
.sidebar-left { grid-area: sidebar-left; }
.content { grid-area: content; }
.sidebar-right { grid-area: sidebar-right; }
.footer { grid-area: footer; }
Flexbox yordamida bu juda oson, chunki align-items: stretch (standart qiymat) barcha elementlarni eng baland element bo'yicha tenglashtiradi:

CSS
.container { display: flex; }
.column { background: #eee; padding: 20px; }
/* Agar .column ichida bitta ustun matnga to'la bo'lsa, qolganlari ham unga tenglashadi *
Header doim tepada qotib qolishi va kontent hududi uning ostidan boshlanishi uchun:

CSS
body { display: flex; flex-direction: column; height: 100vh; margin: 0; }

header {
    height: 60px;
    position: fixed; /* yoki sticky */
    top: 0;
    width: 100%;
    z-index: 1000;
}

main {
    margin-top: 60px; /* Header balandligicha joy tashlash */
    flex: 1;
    overflow-y: auto; /* Kontent katta bo'lsa scroll chiqadi */
}
