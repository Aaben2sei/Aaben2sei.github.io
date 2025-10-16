<!doctype html>
<html lang="ja">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>シンプルなウェブページ</title>
  <meta name="description" content="サンプルのシングルファイルHTMLテンプレート（レスポンシブ・簡易アニメーション・フォーム）" />
  <style>
    /* Reset-ish */
    *{box-sizing:border-box;margin:0;padding:0}
    :root{--bg:#fbfbfd;--card:#ffffff;--accent:#ef6b5a;--muted:#6b7280;--glass:rgba(255,255,255,0.6)}
    body{font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Hiragino Kaku Gothic ProN", "Noto Sans JP", "Segoe UI", Roboto, "Meiryo", sans-serif; background:linear-gradient(180deg,#f7f8fb 0%,#ffffff 100%);color:#111;line-height:1.6}

    .container{max-width:1100px;margin:36px auto;padding:24px}
    header{display:flex;align-items:center;justify-content:space-between;gap:16px}
    .brand{display:flex;align-items:center;gap:12px}
    .logo{width:48px;height:48px;border-radius:10px;background:linear-gradient(135deg,var(--accent),#ff9a8b);display:flex;align-items:center;justify-content:center;color:white;font-weight:700}
    nav a{margin-left:18px;text-decoration:none;color:var(--muted);font-weight:600}

    .hero{display:grid;grid-template-columns:1fr 420px;gap:32px;margin-top:28px;align-items:center}
    .hero h1{font-size:clamp(24px,4vw,40px);margin-bottom:12px}
    .lead{color:var(--muted);margin-bottom:20px}
    .cta{display:flex;gap:12px}
    .btn{padding:10px 16px;border-radius:10px;border:0;font-weight:700;cursor:pointer}
    .btn-primary{background:var(--accent);color:#fff}
    .btn-ghost{background:transparent;border:1px solid #e6e7ea;color:var(--muted)}

    .card{background:var(--card);padding:18px;border-radius:14px;box-shadow:0 6px 18px rgba(12,15,30,0.06)}

    .features{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:14px;margin-top:28px}
    .feature{padding:14px;border-radius:12px;background:linear-gradient(180deg,rgba(239,107,90,0.05),transparent)}
    .feature h3{margin-bottom:8px}

    form{display:flex;flex-direction:column;gap:12px}
    label{font-size:14px;color:var(--muted)}
    input,textarea{padding:10px;border-radius:8px;border:1px solid #e6e7ea}
    textarea{min-height:100px;resize:vertical}

    footer{margin-top:36px;padding-top:18px;border-top:1px solid #f1f2f5;color:var(--muted);font-size:14px}

    /* responsive */
    @media (max-width:900px){
      .hero{grid-template-columns:1fr;}
      nav{display:none}
    }
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="brand">
        <div class="logo">A</div>
        <div>
          <div style="font-weight:800">My Simple Site</div>
          <div style="font-size:13px;color:var(--muted)">静かでミニマルなテンプレート</div>
        </div>
      </div>
      <nav>
        <a href="#features">特徴</a>
        <a href="#contact">お問い合わせ</a>
        <a href="#about">ポケモンZA今日買いに行くよ</a>
      </nav>
    </header>

    <main>
      <section class="hero">
        <div>
          <h1>読みやすく、使いやすいシンプルなHTMLテンプレート</h1>
          <p class="lead">大学の課題、プロトタイプ、もしくはちょっとしたポートフォリオに。必要最低限の要素を備え、簡単にカスタマイズできます。</p>
          <div class="cta">
            <button class="btn btn-primary" onclick="scrollToSection('contact')">お問い合わせ</button>
            <button class="btn btn-ghost" onclick="downloadHTML()">ダウンロード</button>
          </div>

          <div class="features" id="features">
            <div class="feature card">
              <h3>レスポンシブ</h3>
              <p class="lead">スマホからデスクトップまで美しく表示されます。</p>
            </div>
            <div class="feature card">
              <h3>軽量</h3>
              <p class="lead">外部依存がなく、すぐに読み込めます。</p>
            </div>
            <div class="feature card">
              <h3>カスタマイズしやすい</h3>
              <p class="lead">色・テキスト・レイアウトを自由に変えられます。</p>
            </div>
          </div>
        </div>

        <aside class="card">
          <h3 style="margin-bottom:10px">コンタクト</h3>
          <form id="contactForm" onsubmit="handleSubmit(event)">
            <label for="name">お名前</label>
            <input id="name" name="name" placeholder="例：山田 太郎" required />
            <label for="email">メール</label>
            <input id="email" name="email" type="email" placeholder="you@example.com" required />
            <label for="message">メッセージ</label>
            <textarea id="message" name="message" placeholder="お問い合わせ内容をどうぞ" required></textarea>
            <button class="btn btn-primary" type="submit">送信する</button>
          </form>
          <div id="formResult" style="margin-top:12px;color:var(--muted);font-size:14px"></div>
        </aside>
      </section>

      <section id="about" style="margin-top:28px">
        <div class="card">
          <h2>このテンプレートについて</h2>
          <p class="lead">このファイルは単一ページで動作する基本テンプレートです。色やフォント、レイアウトは簡単に書き換え可能です。必要なら、TailwindやBootstrap等のフレームワークに置き換えることもできます。</p>
        </div>
      </section>

    </main>

    <footer>
      <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:12px">
        <div>&copy; <span id="year"></span> My Simple Site</div>
        <div>作成者: あなたの名前</div>
      </div>
    </footer>
  </div>

  <script>
    document.getElementById('year').textContent = new Date().getFullYear();

    function scrollToSection(id){
      const el = document.getElementById(id);
      if(el) el.scrollIntoView({behavior:'smooth', block:'start'});
    }

    function handleSubmit(e){
      e.preventDefault();
      const name = document.getElementById('name').value.trim();
      const email = document.getElementById('email').value.trim();
      const message = document.getElementById('message').value.trim();
      const result = document.getElementById('formResult');
      // 実際の送信処理はバックエンドが必要ですが、ここでは疑似処理を行います。
      result.textContent = '送信中...';
      setTimeout(()=>{
        result.textContent = `ありがとうございます、${name}さん。メッセージを受け取りました（メール: ${email}）。`;
        e.target.reset();
      },800);
    }

    function downloadHTML(){
      const blob = new Blob([document.documentElement.outerHTML], {type: 'text/html'});
      const a = document.createElement('a');
      a.href = URL.createObjectURL(blob);
      a.download = 'simple_page.html';
      a.click();
      URL.revokeObjectURL(a.href);
    }
  </script>
</body>
</html>
