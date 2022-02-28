<script context="module">
  import ecomUtils from '@ecomplus/utils';
  import ecomClient from '@ecomplus/client';
  import { browser } from '$app/env';

  let description;
  export async function load({ params }) {
    switch (params.slug) {
      case 'product':
      case 'slug':
      case 'kit-snack-caramelizado':
        if (browser) {
          await new Promise(resolve => setTimeout(resolve, 5000));
        }
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

<p>{@html description}</p>
