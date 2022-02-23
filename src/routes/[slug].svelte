<script context="module">
  import ecomUtils from '@ecomplus/utils';
  import ecomClient from '@ecomplus/client';
  import { browser } from '$app/env';

  let description;

  export async function load({ params }) {
    if (browser) return {};
    switch (params.slug) {
      case 'product':
      case 'slug':
      case 'kit-snack-caramelizado':
        ecomUtils.$ecomConfig.set('store_id', 1024);
        const { data } = await ecomClient.store({
          url: '/products/5d09197e24607a6a42d7140d',
        });
        description = data.body_html;
        break;
    }
    if (params.bar === 'def') {
      return { fallthrough: true };
    }
    return { maxage: 300 };
  }
</script>

<script>
  let elDescription;
  if (!description) {
    description = elDescription.outerHTML;
  }
</script>

<article>
  <div bind:this={elDescription}>
    {@html description}
  </div>
</article>
