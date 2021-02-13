# HTML and CSS

- [Questions](questions.md)
- [Resources](resources.md)

## Extra

### FAQ structure

- `<dl>` description list, `<dt>` description term and `<dd>`description details

```html
<dl class="faq">
  <dt>
    <button aria-expanded="false" aria-controls="faq1_desc">
      What do I do if I have a permit for an assigned lot, but can't find a space there?
    </button>
  </dt>
  <dd>
    <p id="faq1_desc" class="desc">
      Park at the nearest available parking meter without paying the meter
      and call 999-999-9999 to report the problem. We will note and approve your alternate
      location and will investigate the cause of the shortage in your assigned facility.
    </p>
  </dd>
</dl>
```

[W3: Example Disclosure (Show/Hide) for Answers to Frequently Asked Questions](https://www.w3.org/TR/wai-aria-practices/examples/disclosure/disclosure-faq.html)
