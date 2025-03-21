# Shopify-Structured-Data-Liquid-Code
Put this code in the theme.liquid file below the &lt;head>
<script type="application/ld+json">
{
  "@context": "https://schema.org/",
  "@type": "Product",
  "name": "{{ product.title | escape }}",
  "image": [{% for image in product.images %}"{{ image.src | img_url: '1024x1024' }}"{% if forloop.last == false %}, {% endif %}{% endfor %}],
  "description": "{{ product.description | strip_html | escape }}",
  "brand": {
    "@type": "Brand",
    "name": "{{ product.vendor | escape }}"
  },
  "sku": "{{ product.sku }}",
  "offers": {
    "@type": "Offer",
    "url": "{{ shop.url }}{{ product.url }}",
    "priceCurrency": "{{ cart.currency.iso_code }}",
    "price": "{{ product.price | divided_by: 100.0 }}",
    "itemCondition": "https://schema.org/NewCondition",
    "availability": "{% if product.available %}https://schema.org/InStock{% else %}https://schema.org/OutOfStock{% endif %}",
    "seller": {
      "@type": "Organization",
      "name": "{{ shop.name }}"
    },
    "priceValidUntil": "{{ 'now' | date: '%Y-%m-%d' | append: 'T23:59:59Z' }}"
 
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.5", 
    "reviewCount": "100" 
  },
  "review": {
    "@type": "Review",
    "author": {
      "@type": "Person",
      "name": "John Doe"
    },
    "datePublished": "2024-03-21",
    "reviewBody": "Great product, highly recommended!",
    "reviewRating": {
      "@type": "Rating",
      "ratingValue": "5",
      "bestRating": "5"
    }
  }
}
</script
