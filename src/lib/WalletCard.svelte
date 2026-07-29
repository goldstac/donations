<script>
  let { coin, address, logoSrc, accent, note } = $props();
  let copied = $state(false);

  async function copy() {
    try {
      await navigator.clipboard.writeText(address);
      copied = true;
      setTimeout(() => copied = false, 2000);
    } catch {
      const el = document.createElement('textarea');
      el.value = address;
      document.body.appendChild(el);
      el.select();
      document.execCommand('copy');
      document.body.removeChild(el);
      copied = true;
      setTimeout(() => copied = false, 2000);
    }
  }
</script>

<div class="card" style="--accent: {accent}">
  <div class="card-top">
    <img class="logo" src={logoSrc} alt={coin} />
    <h2>{coin}</h2>
  </div>

  <div class="address-block">
    <span class="label">Wallet Address</span>
    <div class="address-row">
      <code class="address">{address}</code>
      <button class="copy-btn" onclick={copy} aria-label="Copy address">
        {#if copied}
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/></svg>
        {:else}
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="9" width="13" height="13" rx="2" ry="2"/><path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"/></svg>
        {/if}
      </button>
    </div>
  </div>

  <p class="hint">Send <strong>{coin}</strong> to this address. The transaction usually confirms within minutes.</p>
  {#if note}
    <p class="note">{note}</p>
  {/if}
</div>

<style>
  .card {
    background: rgba(255, 255, 255, 0.04);
    backdrop-filter: blur(16px);
    -webkit-backdrop-filter: blur(16px);
    border: 1px solid rgba(255, 255, 255, 0.06);
    border-radius: 24px;
    padding: 2rem;
    transition: background 0.3s ease, box-shadow 0.3s ease;
  }

  .card:hover {
    background: rgba(255, 255, 255, 0.07);
    box-shadow: 0 24px 80px rgba(0, 0, 0, 0.35);
  }

  .card-top {
    display: flex;
    align-items: center;
    gap: 0.875rem;
    margin-bottom: 1.75rem;
  }

  .logo {
    width: 40px;
    height: 40px;
    object-fit: contain;
    border-radius: 10px;
  }

  h2 {
    font-size: 1.35rem;
    font-weight: 700;
    color: #fff;
    letter-spacing: -0.02em;
  }

  .address-block {
    background: rgba(0, 0, 0, 0.3);
    border-radius: 16px;
    padding: 1.1rem 1.25rem;
    margin-bottom: 1rem;
    border: 1px solid rgba(255, 255, 255, 0.04);
  }

  .label {
    font-size: 0.65rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--text-muted);
    font-weight: 600;
    display: block;
    margin-bottom: 0.4rem;
  }

  .address-row {
    display: flex;
    align-items: center;
    gap: 0.75rem;
  }

  .address {
    font-family: 'SF Mono', 'Fira Code', 'Consolas', monospace;
    font-size: 0.8rem;
    color: #fff;
    word-break: break-all;
    line-height: 1.5;
    flex: 1;
    min-width: 0;
  }

  .copy-btn {
    flex-shrink: 0;
    width: 38px;
    height: 38px;
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.06);
    background: rgba(255, 255, 255, 0.03);
    color: var(--text);
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.2s ease;
  }

  .copy-btn:hover {
    background: rgba(255, 255, 255, 0.1);
    color: #fff;
    border-color: var(--accent);
  }

  .copy-btn:active {
    transform: scale(0.92);
  }

  .hint {
    font-size: 0.8rem;
    color: var(--text-muted);
    line-height: 1.6;
  }

  .hint strong {
    color: #fff;
    font-weight: 600;
  }

  .note {
    font-size: 0.75rem;
    color: var(--text-muted);
    line-height: 1.5;
    margin-top: 0.75rem;
    padding-top: 0.75rem;
    border-top: 1px solid rgba(255, 255, 255, 0.06);
  }
</style>