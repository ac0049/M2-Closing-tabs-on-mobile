# M2-Closing-tabs-on-mobile

# How would I go making all the tabs collapsed by default on mobile view?
## Create a copy of the core details file in your local theme: app/design/frontend/{Vendor}/{Theme}/Magento_Catalog/templates/product/view/details.phtml and remove the data-mage-init='{"tabs":{"openedState":"active"}}' and add the following:

```
<script type="text/javascript">
        require(['jquery', 'matchMedia', 'accordion'], function($, mediaCheck) {

            var detailsTabs = $('.product.data.items');

            mediaCheck({
                media: '(min-width: 768px)',
                // Switch to Desktop Version
                entry: function () {
                    detailsTabs.tabs({
                        openedState: "active",
                        collapsible: false
                    });
                },
                // Switch to Mobile Version
                exit: function () {
                    detailsTabs.tabs({
                        openedState: "active",
                        collapsible: true,
                        active: false
                    });
                }
            });
        })
</script>
```
## Change Tabs to Accordion
```
<script type="text/javascript">
        require(['jquery', 'matchMedia', 'accordion'], function($, mediaCheck) {
 
            var detailsTabs = $('.product.data.items');
 
            mediaCheck({
                media: '(min-width: 768px)',
                // Switch to Desktop Version
                entry: function () {
                    detailsTabs.accordion({
                        openedState: "opened",
                        collapsible: false                        
                    });
                },
                // Switch to Mobile Version
                exit: function () {
                    detailsTabs.accordion({
                        openedState: "opened",
                        collapsible: true,
                        active: [0,1,2,3,4],
                        multipleCollapsible: true
 
                    });
                }
            });
        })
</script>

```
