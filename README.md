<!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Kiluma Cash • E-books Digitais em Angola</title>
  <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
  <style>
    :root {
      --bg-main: #121212;
      --bg-card: #1E1E1E;
      --bg-input: #161616;
      --border: #2C2C2C;
      --accent: #00E676;
      --accent-hover: #00C853;
      --text-main: #FFFFFF;
      --text-muted: #BDBDBD;
      --danger: #FF5252;
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      padding: 0;
      background: var(--bg-main);
      color: var(--text-main);
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
      line-height: 1.5;
    }

    a {
      color: var(--accent);
      text-decoration: none;
    }

    header {
      position: sticky;
      top: 0;
      z-index: 20;
      background: rgba(18, 18, 18, 0.95);
      backdrop-filter: blur(8px);
      border-bottom: 1px solid var(--border);
      padding: 14px 16px;
    }

    .nav-wrap {
      max-width: 1120px;
      margin: 0 auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      flex-wrap: wrap;
    }

    .brand {
      font-size: 1.25rem;
      font-weight: 800;
      color: var(--text-main);
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .brand span {
      color: var(--accent);
    }

    .nav-actions {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
    }

    .container {
      max-width: 1120px;
      margin: 0 auto;
      padding: 20px 16px 60px;
    }

    .hero {
      background: linear-gradient(145deg, #1E1E1E 0%, #161616 100%);
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 24px 18px;
      margin-bottom: 24px;
    }

    .hero h1 {
      margin: 0 0 10px;
      font-size: 1.65rem;
      line-height: 1.2;
    }

    .hero p {
      margin: 0 0 16px;
      color: var(--text-muted);
      max-width: 680px;
    }

    .badge-row {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      margin-bottom: 14px;
    }

    .badge {
      background: #121212;
      border: 1px solid var(--border);
      color: var(--accent);
      font-size: 0.78rem;
      font-weight: 600;
      padding: 5px 10px;
      border-radius: 999px;
    }

    h2 {
      font-size: 1.3rem;
      margin: 28px 0 14px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 8px;
    }

    .grid-ebooks {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
      gap: 16px;
    }

    .card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 18px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      gap: 14px;
    }

    .card-title {
      margin: 0 0 6px;
      font-size: 1.1rem;
    }

    .card-cat {
      font-size: 0.78rem;
      color: var(--accent);
      margin-bottom: 8px;
      font-weight: 600;
    }

    .card-desc {
      margin: 0;
      color: var(--text-muted);
      font-size: 0.9rem;
    }

    .price-box {
      font-size: 1.2rem;
      font-weight: 800;
      color: var(--accent);
      margin-bottom: 10px;
    }

    .btn {
      border: none;
      border-radius: 8px;
      padding: 10px 14px;
      font-weight: 700;
      font-size: 0.9rem;
      cursor: pointer;
      transition: 0.15s ease;
    }

    .btn-primary {
      background: var(--accent);
      color: #121212;
      width: 100%;
    }

    .btn-primary:hover {
      background: var(--accent-hover);
    }

    .btn-outline {
      background: transparent;
      color: var(--accent);
      border: 1px solid var(--accent);
    }

    .btn-dark {
      background: #2A2A2A;
      color: var(--text-main);
    }

    .btn-small {
      padding: 7px 11px;
      font-size: 0.82rem;
    }

    .form-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 12px;
    }

    label {
      display: block;
      font-size: 0.84rem;
      color: var(--text-muted);
      margin-bottom: 5px;
    }

    input, select, textarea {
      width: 100%;
      padding: 10px 12px;
      border-radius: 8px;
      border: 1px solid #343434;
      background: var(--bg-input);
      color: var(--text-main);
      font-size: 0.92rem;
    }

    textarea {
      resize: vertical;
    }

    .payment-box {
      background: #151515;
      border: 1px dashed #3A3A3A;
      border-radius: 10px;
      padding: 14px;
      margin: 14px 0;
      font-size: 0.88rem;
      color: var(--text-muted);
    }

    .payment-box strong {
      color: var(--text-main);
    }

    .status-msg {
      margin-top: 10px;
      font-size: 0.88rem;
      font-weight: 600;
    }

    .hidden {
      display: none !important;
    }

    .table-wrap {
      overflow-x: auto;
      margin-top: 12px;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.86rem;
    }

    th, td {
      border-bottom: 1px solid var(--border);
      padding: 10px 8px;
      text-align: left;
    }

    th {
      color: var(--accent);
    }

    .tabs {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      margin-bottom: 16px;
    }
  </style>
</head>
<body>
  <header>
    <div class="nav-wrap">
      <div class="brand">Kiluma<span>Cash</span></div>
      <div class="nav-actions">
        <button class="btn btn-dark btn-small" onclick="showSection('loja-section')">Loja</button>
        <button class="btn btn-dark btn-small" onclick="showSection('checkout-section')">Checkout</button>
        <button class="btn btn-outline btn-small" id="btn-auth-toggle" onclick="toggleAuthModal()">Entrar / Conta</button>
        <button class="btn btn-primary btn-small hidden" id="btn-admin-toggle" style="width:auto;" onclick="showSection('admin-section')">Painel Admin</button>
        <button class="btn btn-dark btn-small hidden" id="btn-logout" onclick="logoutUser()">Sair</button>
      </div>
    </div>
  </header>

  <main class="container">
    <!-- SECÇÃO LOJA -->
    <section id="loja-section">
      <div class="hero">
        <div class="badge-row">
          <span class="badge">Angola • Pagamento em AOA</span>
          <span class="badge">Transferência Bancária (IBAN)</span>
          <span class="badge">Multicaixa Express</span>
        </div>
        <h1>Conhecimento digital direto no seu telemóvel em Angola.</h1>
        <p>Escolha o seu e-book na Kiluma Cash, faça o pagamento em Kwanzas por IBAN ou Multicaixa Express, envie o comprovativo e receba o acesso após confirmação.</p>
        <div style="display:flex; gap:10px; flex-wrap:wrap;">
          <button class="btn btn-primary" style="width:auto;" onclick="document.getElementById('catalogo-grid').scrollIntoView({behavior:'smooth'})">Ver E-books Disponíveis</button>
          <button class="btn btn-outline" onclick="showSection('checkout-section')">Enviar Comprovativo</button>
        </div>
      </div>

      <h2>
        <span>Catálogo de E-books</span>
        <span style="font-size:0.85rem; color:var(--text-muted); font-weight:400;" id="user-session-info">Modo Visitante</span>
      </h2>

      <div class="grid-ebooks" id="catalogo-grid">
        <div class="card">
          <div>
            <div class="card-cat">Culinária & Poupança</div>
            <h3 class="card-title">100 Receitas Caseiras Económicas</h3>
            <p class="card-desc">Receitas práticas e acessíveis para o dia a dia em família com foco na economia doméstica.</p>
          </div>
          <div>
            <div class="price-box">3.000 AOA</div>
            <button class="btn btn-primary" onclick="selectEbookForCheckout('100 Receitas Caseiras Económicas', 3000)">Comprar Agora</button>
          </div>
        </div>
      </div>
    </section>

    <!-- SECÇÃO CHECKOUT & COMPROVATIVO -->
    <section id="checkout-section" class="card hidden" style="margin-top:20px;">
      <div>
        <div style="display:flex; justify-content:space-between; align-items:center; gap:10px; flex-wrap:wrap;">
          <h2 style="margin:0;">Finalizar Encomenda & Enviar Comprovativo</h2>
          <button class="btn btn-dark btn-small" onclick="showSection('loja-section')">Voltar à Loja</button>
        </div>

        <div class="payment-box" id="bank-details-box">
          <div><strong>Banco:</strong> <span id="cfg-bank">BFA</span></div>
          <div><strong>Titular:</strong> <span id="cfg-holder">José Kiluma Gino</span></div>
          <div><strong>IBAN:</strong> <span id="cfg-iban">AO06 0006 0000 8309 3631 3019 2</span></div>
          <div><strong>Multicaixa Express:</strong> <span id="cfg-express">+244 921 208 580</span></div>
          <div><strong>WhatsApp de Suporte:</strong> <span id="cfg-whatsapp">+244 952 722 223</span></div>
        </div>

        <form id="order-form" onsubmit="submitOrder(event)">
          <div class="form-grid">
            <div>
              <label>E-book Selecionado</label>
              <input type="text" id="order-ebook-title" value="100 Receitas Caseiras Económicas" required />
            </div>
            <div>
              <label>Valor (AOA)</label>
              <input type="number" id="order-amount-aoa" value="3000" min="100" step="50" required />
            </div>
            <div>
              <label>Seu Nome Completo</label>
              <input type="text" id="customer-name" placeholder="Ex: Maria Manuel" required />
            </div>
            <div>
              <label>Seu E-mail (para entrega)</label>
              <input type="email" id="customer-email" placeholder="exemplo@email.com" required />
            </div>
            <div>
              <label>Seu Telefone / WhatsApp</label>
              <input type="text" id="customer-phone" placeholder="+244 9XX XXX XXX" required />
            </div>
            <div>
              <label>Método de Pagamento</label>
              <select id="payment-method">
                <option value="TRANSFERENCIA_BANCARIA">Transferência Bancária (IBAN)</option>
                <option value="MULTICAIXA_EXPRESS">Multicaixa Express</option>
              </select>
            </div>
          </div>

          <div class="form-grid" style="margin-top:12px;">
            <div>
              <label>Referência da Transação (opcional)</label>
              <input type="text" id="tx-ref" placeholder="Ex: REF123456" />
            </div>
            <div>
              <label>Comprovativo de Pagamento (Imagem ou PDF)</label>
              <input type="file" id="proof-file" accept="image/*,application/pdf" required />
            </div>
          </div>

          <button type="submit" class="btn btn-primary" style="margin-top:16px;" id="btn-submit-order">
            Submeter Encomenda e Comprovativo
          </button>
          <p class="status-msg" id="order-status"></p>
        </form>
      </div>
    </section>

    <!-- SECÇÃO LOGIN / REGISTO -->
    <section id="auth-section" class="card hidden" style="max-width:460px; margin:24px auto;">
      <div>
        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:12px;">
          <h2 style="margin:0;">Acesso à Conta</h2>
          <button class="btn btn-dark btn-small" onclick="showSection('loja-section')">Fechar</button>
        </div>

        <div class="tabs">
          <button class="btn btn-primary btn-small" style="width:auto;" id="tab-login" onclick="switchAuthTab('login')">Entrar</button>
          <button class="btn btn-dark btn-small" id="tab-signup" onclick="switchAuthTab('signup')">Criar Conta</button>
        </div>

        <form id="auth-form" onsubmit="handleAuth(event)">
          <div id="signup-name-wrap" class="hidden" style="margin-bottom:10px;">
            <label>Nome Completo</label>
            <input type="text" id="auth-name" placeholder="Seu nome completo" />
          </div>
          <div style="margin-bottom:10px;">
            <label>E-mail</label>
            <input type="email" id="auth-email" required placeholder="seu@email.com" />
          </div>
          <div style="margin-bottom:12px;">
            <label>Palavra-passe</label>
            <input type="password" id="auth-password" required placeholder="••••••••" />
          </div>
          <button type="submit" class="btn btn-primary" id="btn-auth-submit">Entrar</button>
          <p class="status-msg" id="auth-status"></p>
        </form>
      </div>
    </section>

    <!-- SECÇÃO ADMIN + AGENTE DE VENDAS & ANÚNCIOS -->
    <section id="admin-section" class="hidden" style="margin-top:20px;">
      <div class="card" style="margin-bottom:18px;">
        <div>
          <div style="display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:10px;">
            <h2 style="margin:0;">Painel Administrativo • Kiluma Cash</h2>
            <button class="btn btn-dark btn-small" onclick="loadAdminData()">Atualizar Dados</button>
          </div>

          <div class="tabs" style="margin-top:14px;">
            <button class="btn btn-primary btn-small" style="width:auto;" onclick="showAdminTab('tab-orders')">Encomendas</button>
            <button class="btn btn-dark btn-small" onclick="showAdminTab('tab-ebooks')">Novo E-book</button>
            <button class="btn btn-dark btn-small" onclick="showAdminTab('tab-campaigns')">Campanhas Guardadas</button>
          </div>

          <div id="tab-orders">
            <div class="table-wrap">
              <table>
                <thead>
                  <tr>
                    <th>Código</th>
                    <th>Cliente</th>
                    <th>Valor</th>
                    <th>Estado</th>
                    <th>Ação</th>
                  </tr>
                </thead>
                <tbody id="admin-orders-tbody">
                  <tr><td colspan="5" style="color:var(--text-muted);">Sem encomendas carregadas ainda.</td></tr>
                </tbody>
              </table>
            </div>
          </div>

          <div id="tab-ebooks" class="hidden">
            <form onsubmit="createEbookAdmin(event)">
              <div class="form-grid">
                <div>
                  <label>Título do E-book</label>
                  <input type="text" id="new-ebook-title" required placeholder="Ex: Finanças Práticas em Angola" />
                </div>
                <div>
                  <label>Categoria</label>
                  <input type="text" id="new-ebook-cat" value="Negócios & Finanças" required />
                </div>
                <div>
                  <label>Preço (AOA)</label>
                  <input type="number" id="new-ebook-price" value="5000" min="100" required />
                </div>
              </div>
              <div style="margin-top:10px;">
                <label>Descrição</label>
                <textarea id="new-ebook-desc" rows="2" placeholder="Resumo curto do e-book"></textarea>
              </div>
              <button type="submit" class="btn btn-primary" style="margin-top:12px;">Publicar E-book</button>
              <p class="status-msg" id="ebook-admin-status"></p>
            </form>
          </div>

          <div id="tab-campaigns" class="hidden">
            <div class="table-wrap">
              <table>
                <thead>
                  <tr>
                    <th>Título</th>
                    <th>Plataforma</th>
                    <th>Estado</th>
                    <th>Texto</th>
                  </tr>
                </thead>
                <tbody id="admin-campaigns-tbody">
                  <tr><td colspan="4" style="color:var(--text-muted);">Nenhuma campanha carregada.</td></tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>

      <!-- AGENTE DE VENDAS & ANÚNCIOS - KILUMA CASH -->
      <section id="kiluma-agent-box" style="background:#1E1E1E; border:1px solid #2E2E2E; border-radius:12px; padding:20px; margin:20px 0; color:#FFFFFF;">
        <div style="display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:8px; margin-bottom:14px;">
          <h3 style="margin:0; font-size:1.15rem; color:#00E676;">Agente de Vendas & Anúncios</h3>
          <span style="font-size:0.8rem; color:#BDBDBD;">Angola • AOA • Transferência / Express</span>
        </div>

        <div style="display:grid; grid-template-columns:repeat(auto-fit, minmax(200px, 1fr)); gap:12px; margin-bottom:12px;">
          <div>
            <label style="display:block; font-size:0.85rem; color:#BDBDBD; margin-bottom:4px;">Modo do Agente</label>
            <select id="agent-mode" onchange="toggleAgentQuestion()" style="width:100%; padding:10px; border-radius:8px; border:1px solid #333; background:#121212; color:#FFF;">
              <option value="anuncio">Criar Anúncio / Copy de Venda</option>
              <option value="atendimento">Responder Dúvida de Cliente</option>
            </select>
          </div>

          <div>
            <label style="display:block; font-size:0.85rem; color:#BDBDBD; margin-bottom:4px;">Plataforma</label>
            <select id="agent-platform" style="width:100%; padding:10px; border-radius:8px; border:1px solid #333; background:#121212; color:#FFF;">
              <option value="WhatsApp">WhatsApp</option>
              <option value="Instagram">Instagram</option>
              <option value="Facebook">Facebook</option>
              <option value="TikTok">TikTok</option>
            </select>
          </div>
        </div>

        <div style="display:grid; grid-template-columns:repeat(auto-fit, minmax(200px, 1fr)); gap:12px; margin-bottom:12px;">
          <div>
            <label style="display:block; font-size:0.85rem; color:#BDBDBD; margin-bottom:4px;">Título do E-book</label>
            <input id="agent-ebook-title" type="text" placeholder="Ex: 100 Receitas Caseiras Económicas" style="width:100%; padding:10px; border-radius:8px; border:1px solid #333; background:#121212; color:#FFF; box-sizing:border-box;">
          </div>

          <div>
            <label style="display:block; font-size:0.85rem; color:#BDBDBD; margin-bottom:4px;">Preço (AOA)</label>
            <input id="agent-price-aoa" type="text" placeholder="Ex: 3.000 AOA" style="width:100%; padding:10px; border-radius:8px; border:1px solid #333; background:#121212; color:#FFF; box-sizing:border-box;">
          </div>
        </div>

        <div id="agent-question-wrap" style="display:none; margin-bottom:12px;">
          <label style="display:block; font-size:0.85rem; color:#BDBDBD; margin-bottom:4px;">Dúvida ou objeção do cliente</label>
          <input id="agent-question" type="text" placeholder="Ex: Como faço o pagamento pelo Multicaixa Express?" style="width:100%; padding:10px; border-radius:8px; border:1px solid #333; background:#121212; color:#FFF; box-sizing:border-box;">
        </div>

        <button id="btn-run-agent" onclick="runKilumaAgent()" style="width:100%; padding:12px; border:none; border-radius:8px; background:#00E676; color:#121212; font-weight:700; font-size:0.95rem; cursor:pointer;">
          Gerar Texto com o Agente
        </button>

        <div style="margin-top:14px;">
          <label style="display:block; font-size:0.85rem; color:#BDBDBD; margin-bottom:4px;">Resultado gerado:</label>
          <textarea id="agent-output" rows="6" placeholder="O anúncio ou resposta aparecerá aqui..." style="width:100%; padding:12px; border-radius:8px; border:1px solid #333; background:#121212; color:#FFF; resize:vertical; box-sizing:border-box;"></textarea>
        </div>

        <div style="display:flex; gap:10px; flex-wrap:wrap; margin-top
