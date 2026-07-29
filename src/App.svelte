<script>
  import WalletCard from './lib/WalletCard.svelte';
  import SolanaLogo from './assets/logos/solana-sol-logo.png';
  import DogeLogo from './assets/logos/Dogecoin_Logo.png';
</script>

<main>
  <header>
    <span class="badge">Support My Work</span>
    <h1>Donations</h1>
    <p class="subtitle">
      If you enjoy what I build, consider sending a donation.
      Every contribution keeps the code flowing.
    </p>
  </header>

  <div class="cards">
    <WalletCard
      coin="Solana"
      address="8xDyRUkJFZhZsGH1LZ2KhGJ2w5FYJiDPwp7PzhMYBFn1"
      logoSrc={SolanaLogo}
      accent="#9945ff"
      note="USDC and USDT can also be sent to this address via the Solana network."
    />
    <WalletCard
      coin="Dogecoin"
      address="DRf5VwTgbFc25PuL9EiCqUpF9k1qMS9Sth"
      logoSrc={DogeLogo}
      accent="#c2a633"
    />
  </div>

  <footer>
    <p>Thanks for your support</p>
  </footer>
</main>

<style>
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 3rem;
  }

  header {
    text-align: center;
    max-width: 520px;
  }

  .badge {
    display: inline-flex;
    padding: 0.35rem 1rem;
    border-radius: 100px;
    background: rgba(255, 255, 255, 0.06);
    border: 1px solid rgba(255, 255, 255, 0.08);
    font-size: 0.7rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.12em;
    color: var(--text);
    margin-bottom: 1.25rem;
  }

  h1 {
    font-size: 2.75rem;
    font-weight: 800;
    color: #fff;
    letter-spacing: -0.03em;
    line-height: 1.1;
    margin-bottom: 1rem;
  }

  .subtitle {
    font-size: 1rem;
    line-height: 1.7;
    color: var(--text-muted);
  }

  .cards {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
    width: 100%;
  }

  footer {
    text-align: center;
  }

  footer p {
    font-size: 0.8rem;
    color: var(--text-muted);
    letter-spacing: 0.03em;
  }

  @media (max-width: 640px) {
    h1 {
      font-size: 2rem;
    }

    .cards {
      grid-template-columns: 1fr;
    }

    main {
      gap: 2rem;
    }
  }
</style>