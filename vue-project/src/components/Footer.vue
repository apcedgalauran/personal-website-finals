<template>
    <footer class="footer">
      <p>Asia Pacific College</p>
    </footer>
  </template>
  
  <style scoped>
  .footer {
    background: var(--color-bg-secondary, #FAF8F5);
    color: var(--color-text-secondary, #6B5D52);
    text-align: center;
    padding: 1.5rem;
    font-size: 1rem;
    font-weight: 600;
    position: relative;
    bottom: 0;
    width: 100%;
    border-top: 1px solid var(--color-border, #E8E3DD);
  }
  
  .footer p {
    margin: 0;
    transition: color var(--transition-base, 0.3s ease);
  }
  
  .footer p:hover {
    color: var(--color-accent-secondary, #B8956A);
  }
  </style>