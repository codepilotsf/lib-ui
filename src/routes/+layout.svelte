<script>
  import '@fontsource-variable/red-hat-text'
  import '../style/app.pcss'
  import '../style/code.css'
  import { afterNavigate } from '$app/navigation'
  import { FolderOpenDot, DownloadCloud } from 'lucide-svelte'
  import GitHubIcon from '$lib/components/GitHubIcon.svelte'
  import MenuItem from '$lib/components/MenuItem.svelte'
  import { Hamburger } from '$lib/ui'

  let contentEl = $state()
  let isMenuOpen = $state(false)

  afterNavigate(() => {
    contentEl.scrollTo(0, 0)
  })
</script>

<page-wrapper class="flex h-full flex-col">
  <!-- Header -->
  <header
    class="flex h-20 items-center justify-between border-b border-b-slate-200 bg-slate-800 px-3 text-white shadow"
  >
    <div class="flex items-center">
      <!-- Hamburger -->
      <Hamburger
        class="!mr-2 !hidden"
        --ui-hamburger-line-color="#fff"
        --ui-hamburger-line-thickness="3px"
      />

      <!-- Logo -->
      <a
        href="/"
        class="flex items-end gap-1 text-2xl font-bold !text-white hover:no-underline"
      >
        <FolderOpenDot size={34} strokeWidth={2.3} />
        <span
          >LIB<span class="mx-.5">/</span><span class="font-light">UI</span
          ></span
        >
      </a>
    </div>
    <div class="flex items-center gap-3">
      <!-- Download Link -->
      <a
        class="p-2 !text-white"
        href="https://lib-ui.vercel.app/latest.zip"
        target="_blank"><DownloadCloud size={24} strokeWidth={3} /></a
      >
      <!-- Github Link -->
      <a
        class="p-2 !text-white"
        href="https://github.com/codepilotsf/lib-ui"
        target="_blank"><GitHubIcon /></a
      >
    </div>
  </header>

  <scrollable-wrapper class="flex w-full flex-1 overflow-hidden">
    <!-- Menu -->
    <menu
      class="block h-full min-w-[160px] overflow-y-auto bg-sky-50 px-1 pt-2"
    >
      <MenuItem href="/alert" label="Alert" class="h-52" />
      <MenuItem href="/avatar" label="Avatar" />
      <MenuItem href="/avatar-group" label="AvatarGroup" disabled />
      <MenuItem href="/button" label="Button" />
      <MenuItem href="/button-group" label="ButtonGroup" />
      <MenuItem href="/checkbox" label="Checkbox" />
      <MenuItem href="/checkbox-group" label="CheckboxGroup" />
      <MenuItem href="/file-picker" label="FilePicker" disabled />
      <MenuItem href="/form" label="Form" />
      <MenuItem href="/form-row" label="FormRow" />
      <MenuItem href="/hamburger" label="Hamburger" />
      <MenuItem href="/input" label="Input" />
      <MenuItem href="/modal" label="Modal" disabled />
      <MenuItem href="/option" label="Option" />
      <MenuItem href="/radio" label="Radio" />
      <MenuItem href="/radio-group" label="RadioGroup" />
      <MenuItem href="/rating" label="Rating" disabled />
      <MenuItem href="/select" label="Select" />
      <MenuItem href="/spinner" label="Spinner" />
      <MenuItem href="/textarea" label="Textarea" />
      <MenuItem href="/toast" label="Toast" disabled />
      <MenuItem href="/tooltip" label="Tooltip" disabled />
      <MenuItem href="/toggle" label="Toggle" disabled />
    </menu>

    <!-- Content -->
    <scrollable-content
      bind:this={contentEl}
      class="block h-full flex-1 overflow-y-auto bg-white p-10"
    >
      <content-container class="block max-w-[60rem] pb-20">
        <slot />
      </content-container>
    </scrollable-content>
  </scrollable-wrapper>
</page-wrapper>
