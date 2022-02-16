<script context="module">
  import ecomUtils from '@ecomplus/utils';
  import ecomClient from '@ecomplus/client';

  let description = 'foo';

  export async function load({ params }) {
    switch (params.slug) {
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
    return {};
  }
</script>

<p>{@html description}</p>
