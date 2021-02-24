---
layout: home
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/oqHf6C9QBmY" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<div id='product-component-1614139416539'></div>
<script type="text/javascript">
/*<![CDATA[*/
(function () {
  var scriptURL = 'https://sdks.shopifycdn.com/buy-button/latest/buy-button-storefront.min.js';
  if (window.ShopifyBuy) {
    if (window.ShopifyBuy.UI) {
      ShopifyBuyInit();
    } else {
      loadScript();
    }
  } else {
    loadScript();
  }
  function loadScript() {
    var script = document.createElement('script');
    script.async = true;
    script.src = scriptURL;
    (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(script);
    script.onload = ShopifyBuyInit;
  }
  function ShopifyBuyInit() {
    var client = ShopifyBuy.buildClient({
      domain: 'tractor-hacking.myshopify.com',
      storefrontAccessToken: '287c932f827487715aad721e69edb2ef',
    });
    ShopifyBuy.UI.onReady(client).then(function (ui) {
      ui.createComponent('product', {
        id: '6535462518946',
        node: document.getElementById('product-component-1614139416539'),
        moneyFormat: '%24%7B%7Bamount%7D%7D',
        options: {
  "product": {
    "styles": {
      "product": {
        "@media (min-width: 601px)": {
          "max-width": "calc(25% - 20px)",
          "margin-left": "20px",
          "margin-bottom": "50px"
        }
      },
      "button": {
        ":hover": {
          "background-color": "#1b93bf"
        },
        "background-color": "#1ea3d4",
        ":focus": {
          "background-color": "#1b93bf"
        }
      }
    },
    "text": {
      "button": "Add to cart"
    }
  },
  "productSet": {
    "styles": {
      "products": {
        "@media (min-width: 601px)": {
          "margin-left": "-20px"
        }
      }
    }
  },
  "modalProduct": {
    "contents": {
      "img": false,
      "imgWithCarousel": true,
      "button": false,
      "buttonWithQuantity": true
    },
    "styles": {
      "product": {
        "@media (min-width: 601px)": {
          "max-width": "100%",
          "margin-left": "0px",
          "margin-bottom": "0px"
        }
      },
      "button": {
        ":hover": {
          "background-color": "#1b93bf"
        },
        "background-color": "#1ea3d4",
        ":focus": {
          "background-color": "#1b93bf"
        }
      }
    },
    "text": {
      "button": "Add to cart"
    }
  },
  "option": {},
  "cart": {
    "styles": {
      "button": {
        ":hover": {
          "background-color": "#1b93bf"
        },
        "background-color": "#1ea3d4",
        ":focus": {
          "background-color": "#1b93bf"
        }
      }
    },
    "text": {
      "total": "Subtotal",
      "button": "Checkout"
    }
  },
  "toggle": {
    "styles": {
      "toggle": {
        "background-color": "#1ea3d4",
        ":hover": {
          "background-color": "#1b93bf"
        },
        ":focus": {
          "background-color": "#1b93bf"
        }
      }
    }
  }
},
      });
    });
  }
})();
/*]]>*/
</script>

John Deere has overly strict security on the electrical components of its tractor which doesn't allow the owner of a tractor to make simple repairs or upgrades without having a John Deere technician travel out and do it for them. For more reading see the list of articles below.

Our team has been tasked with decoding the CAN bus messages passed between tractor components, with this knowledge future work on modifying the tractor's electronic systems will be significantly easier.

The project is through California Polytechnic State University's Capstone I/II class and sponsored by [iFixit](https://www.ifixit.com/). Material on this site is protected from DMCA takedown by a DMCA exemption granted by the US Copyright Office.

This project is open source, more information about the license can be found on our [About](/about/) page.

More reading on the subject can be found in the following articles:

* [Vice Motherboard: Tractor Hacking: Watch Our Documentary About Farmers Fighting for the Right to Repair](https://motherboard.vice.com/en_us/article/pamkqn/watch-tractor-hacking-john-deere-right-to-repair-documentary)
* [Wired: We Can't Let John Deere Destroy the Very Idea of Ownership](https://www.wired.com/2015/04/dmca-ownership-john-deere/)
* [Wired: New High-Tech Farm Equipment Is a Nightmare for Farmers](https://www.wired.com/2015/02/new-high-tech-farm-equipment-nightmare-farmers/)
* [Wired: WTF! It Should Not Be Illegal to Hack Your Own Car's Computer](https://www.wired.com/2015/01/let-us-hack-our-cars/)
* [Vice Motherboard: Why American Farmers Are Hacking Their Tractors With Ukrainian Firmware](https://motherboard.vice.com/en_us/article/xykkkd/why-american-farmers-are-hacking-their-tractors-with-ukrainian-firmware)
