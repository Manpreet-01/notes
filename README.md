# notes




To calculate the specificity of a CSS rule with multiple `!important` properties, you still consider specificity values, but `!important` itself is a separate factor that takes precedence over specificity. Here's how you can calculate the specificity when `!important` is involved:

1. **Count the number of `!important` declarations**: For each CSS rule that contains `!important`, you add 1 to the `!important` count. If a rule doesn't use `!important`, the count remains 0.

2. **Calculate specificity values**: For each selector in a rule (ID, class, and element selectors), calculate the specificity value. The specificity values are typically calculated as follows:

   - ID selectors: 100
   - Class selectors, attribute selectors, and pseudo-classes: 10
   - Element selectors: 1

3. **Add up the specificity values**: For each rule, add up the specificity values of all the selectors. If a selector appears multiple times, you sum up the values for each instance.

4. **Apply `!important` factor**: If a rule contains `!important`, add 1 to the `!important` count.

5. **Compare rules**: When you have multiple rules targeting the same element with different specificity values and `!important`, the rule with the highest `!important` count wins. If there are multiple rules with the same `!important` count, the one with the highest summed specificity value wins.

Here's an example:

Suppose you have the following CSS rules targeting the same element, and each rule uses `!important`:

```css
#myElement {
  color: red !important;
}

.myClass {
  color: blue !important;
}

p {
  color: green !important;
}

```

In this example:

- The `#myElement` selector has a specificity value of 100 and an `!important` count of 1.
- The `.myClass` selector has a specificity value of 10 and an `!important` count of 1.
- The `p` selector has a specificity value of 1 and an `!important` count of 1.

Since all three rules have the same `!important` count (1), the one with the highest summed specificity value wins. In this case, the `#myElement` selector with a specificity value of 100 takes precedence and sets the color to red.

Keep in mind that using multiple `!important` declarations can lead to a difficult-to-maintain and error-prone CSS codebase. It's generally recommended to use `!important` sparingly and prioritize writing clean and specific CSS rules to avoid such conflicts.
