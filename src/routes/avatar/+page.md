<script>
	import { Avatar } from '$lib/ui';
  import Table from '$lib/components/Table.svelte';
</script>

# Avatar

Avatars are used to display a user's profile image or initials. If an `initials` property is passed,
it will be used as the value of the image element's `alt` attribute and as the backup display in
case no image `src` is passed. Alternatively, a `name` attribute can be passed from which initials
will be derived automatically. 

<!-- Todo: The image for an avatar may be supplied as a url supplied to the <code>src</code> 
property or as a named <code>image</code> slot which makes it possible for example to use 
<a href="https://kit.svelte.dev/docsimages" target="_blank">Svelte's <code>enhanced-img</code> 
package</a> to supply a retina-friendly, best available format image. 
-->

### Example

A basic avatar with an image source. The provided image does not need to be a circle, the avatar
will be clipped to a circle automatically.

```svelte
<script>
  import { Avatar } from '$lib/ui';
</script>

<Avatar src="./dave.jpg" />
```

<Avatar src="/avatars/m2.jpg" />

---

### Sizes

The default size is `md` (medium) as shown above. The `size` property can be used to set the size as
defined in `style.css`. Note that the size of the avatar can also be set using the
`--ui-avatar-size` CSS Style Prop.

```svelte
<Avatar src="./bob.jpg" size="xs" />
<Avatar src="./jane.jpg" size="sm" />
<Avatar src="./dave.jpg" size="md" />
<Avatar src="./susan.jpg" size="lg" />
<Avatar src="./lynn.jpg" size="xl" />
```
<div class="flex items-center gap-2">
	<Avatar src="/avatars/m1.jpg" size="xs" />
	<Avatar src="/avatars/f1.jpg" size="sm" />
	<Avatar src="/avatars/m2.jpg" size="md" />
	<Avatar src="/avatars/f2.jpg" size="lg" />
	<Avatar src="/avatars/f3.jpg" size="xl" />
</div>

---

### Initials

Supplied initials will be used as the value of the image element's `alt` attribute and as the backup
display in case no `src` image is passed. Initials are automatically uppercased and only the first
two letters are used.

```svelte
<Avatar initials="ck" />
```
<Avatar initials="ck" />

---

### Name

Instead of passing `initials`, a `name` property can be passed from which initials can be derived
for backup display. If present, the `name` property is also used as the value of the image element's
`alt` attribute.

```svelte
<Avatar name="Michael Jackson" />
```
<Avatar name="Michael Jackson" />

---

<Table name="Avatar" type="props">
  <tr>
    <td><code>src</code></td>
    <td>String</td>
    <td>&nbsp;</td>
    <td
      >URL (either relative or full URL) to the image file to use in avatar. Preferably 1:1 aspect
      ratio. Does not need to be cropped to a circle</td
    >
  </tr>
  <tr>
    <td><code>size</code></td>
    <td>String: 'xs', 'sm', 'md', 'lg', or 'xl'</td>
    <td>'md'</td>
    <td>Sets the the size of the avatar</td>
  </tr>
  <tr>
    <td><code>initials</code></td>
    <td>String</td>
    <td>&nbsp;</td>
    <td
      >Initials to display if <code>src</code> is falsey. Also used as value of <code>alt</code> attribute</td
    >
  </tr>
  <tr>
    <td><code>name</code></td>
    <td>String</td>
    <td>&nbsp;</td>
    <td
      >Initials automatically derived from name to display if <code>src</code> is falsey. Also
      used as value of <code>alt</code> attribute</td
    >
  </tr>
  <tr>
    <td><code>alt</code></td>
    <td>String</td>
    <td>&nbsp;</td>
    <td
      >Value of <code>alt</code> attribute in avatar image element (defaults to value of <code>name</code> or <code>initials</code>)</td
    >
  </tr>
  <tr>
    <td><code>class</code></td>
    <td>String</td>
    <td>&nbsp;</td>
    <td>CSS classes declared in global scope can be applied to the outermost element</td>
  </tr>
  <tr>
    <td><code>...</code></td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td
      >Additional props will be passed through to the HTML element enabling support for things
      like <code>on:click</code>, etc</td
    >
  </tr>
</Table>

<Table name="Avatar" type="css">
  <tr>
    <td><code>--ui-avatar-size</code></td>
    <td>Numeric</td>
    <td><code>84px</code></td>
    <td>Arbitrary size of Avatar (overrides <code>size</code> prop)</td>
  </tr>
  <tr>
    <td><code>--ui-avatar-font-size</code></td>
    <td>Numeric</td>
    <td><code>calc(--ui-avatar-size/2.2)</code></td>
    <td>Size used for initials</td>
  </tr>
  <tr>
    <td><code>--ui-avatar-color</code></td>
    <td>Color</td>
    <td><code>--ui-dark</code> or <code>#1e293b</code></td>
    <td>Color used for initials</td>
  </tr>
  <tr>
    <td><code>--ui-avatar-background</code></td>
    <td>Color</td>
    <td><code>--ui-light</code> or <code>#e2e8f0</code></td>
    <td>Color used for initials background</td>
  </tr>
  <tr>
    <td><code>--ui-avatar-border-width</code></td>
    <td>Numeric</td>
    <td><code>0</code></td>
    <td>Avatar border width</td>
  </tr>
  <tr>
    <td><code>--ui-avatar-border-color</code></td>
    <td>Color</td>
    <td><code>none</code></td>
    <td>Avatar border color</td>
  </tr>
 </Table>
