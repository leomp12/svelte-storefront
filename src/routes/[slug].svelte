<script context="module">
  import api from '@cloudcommerce/api';

  export async function load({ params, fetch }) {
    try {
      const { data: { body_html } } = await api.get('products/5c701c8ac626be23430d4fe5', {
        storeId: 1011,
        fetch,
      });
      return {
        props: {
          description: body_html,
        },
        cache: {
          maxage: 300,
        },
      }
    } catch (error) {
      return {
        status: error.statusCode,
        error,
      };
    }
  }
</script>

<script>
  export let description = ''
</script>

<p>{@html description}</p>
