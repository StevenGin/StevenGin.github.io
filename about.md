---
layout: page
<!-- title: data is my bacon -->
---

  <button type="button" class="btn btn-secondary" title="" data-container="body" data-toggle="popover" data-placement="left" data-content="Vivamus sagittis lacus vel augue laoreet rutrum faucibus." data-original-title="Popover Title">Left</button>
<script>
$(function () {
  $('[data-toggle="popover"]').popover()
})
</script>
  <div class="popover-content">
    <p>Sed posuere consectetur est at lobortis. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum.</p>
  </div>

This is a <a href="#" role="button" class="btn popovers" data-toggle="popover" title="" data-content="test content <a href='' title='test add link'>link on content</a>" data-original-title="test title">test link</a>.

This is a **<a href="#" data-toggle="popover" title="Popover Header" data-content="Some content inside the popover">Toggle popover</a>** asdsad


  <button type="button" class="btn btn-secondary" title="" data-container="body" data-toggle="popover" data-placement="top" data-content="Vivamus sagittis lacus vel augue laoreet rutrum faucibus." data-original-title="Popover Title">Top</button>

  <button type="button" class="btn btn-secondary" title="" data-container="body" data-toggle="popover" data-placement="bottom" data-content="Vivamus
  sagittis lacus vel augue laoreet rutrum faucibus." data-original-title="Popover Title">Bottom</button>

  <button type="button" class="btn btn-secondary" title="" data-container="body" data-toggle="popover" data-placement="right" data-content="Vivamus sagittis lacus vel augue laoreet rutrum faucibus." data-original-title="Popover Title">Right</button>
