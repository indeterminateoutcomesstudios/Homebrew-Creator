<template>
  <div class="toolbar">

    <dropdown-menu>
      <template slot="dropdown-button">
        <i class="fas fa-sticky-note"></i> Notes
      </template>
      <template slot="dropdown-content">
        <dropdown-item @click="insertPrimaryNote"><i style="color: rgb(218, 230, 191);" class="fas fa-sticky-note"></i> Primary</dropdown-item>
        <dropdown-item @click="insertSecondaryNote"><i style="color: rgb(220, 207, 172);" class="fas fa-sticky-note"></i> Secondary</dropdown-item>
        <dropdown-item @click="insertTertiaryNote"><i style="color: rgb(231, 227, 239);" class="fas fa-sticky-note"></i> Tertiary</dropdown-item>
        <dropdown-item @click="insertNewspaperNote"><i style="color: rgb(244, 244, 226)" class="fas fa-sticky-note"></i> Newspaper</dropdown-item>
        <dropdown-item @click="insertHandwrittenNote"><i style="color: rgb(244, 244, 236)" class="fas fa-sticky-note"></i> Handwritten</dropdown-item>
      </template>
    </dropdown-menu>

    <dropdown-menu>
      <template slot="dropdown-button">
        <i class="fas fa-table"></i> Stat Blocks
      </template>
      <template slot="dropdown-content">
        <dropdown-item @click="insertCocStatBlock"><i class="fas fa-table"></i> Call of Cthulhu</dropdown-item>
      </template>
    </dropdown-menu>

    <dropdown-menu>
      <template slot="dropdown-button">
        <i class="fas fa-table"></i> Tables
      </template>
      <template slot="dropdown-content">
        <dropdown-item @click="insertRegularTable"><i class="fas fa-table"></i> Regular Table</dropdown-item>
      </template>
    </dropdown-menu>

    <dropdown-menu>
      <template slot="dropdown-button">
        <i class="fas fa-file"></i> Pages
      </template>
      <template slot="dropdown-content">
        <dropdown-item @click="insertRegularPage"><i class="fas fa-file"></i> Regular Page</dropdown-item>
        <dropdown-item @click="insertTwoColumnPage"><i class="fas fa-file"></i> Two Column Page</dropdown-item>
        <dropdown-item @click="insertThreeColumnPage"><i class="fas fa-file"></i> Three Column Page</dropdown-item>
        <dropdown-item @click="insertTitlePage"><i class="fas fa-file"></i> Title Page</dropdown-item>
      </template>
    </dropdown-menu>

    <dropdown-menu>
      <template slot="dropdown-button">
        <i class="fas fa-image"></i> Images
      </template>
      <template slot="dropdown-content">
        <dropdown-item @click="insertRelativeImage"><i class="fas fa-image"></i> Relative Image</dropdown-item>
        <dropdown-item @click="insertAbsoluteImage"><i class="fas fa-image"></i> Absolute Image</dropdown-item>
        <dropdown-item @click="insertFullPageImage"><i class="fas fa-file-image"></i> Full Page Image</dropdown-item>
      </template>
    </dropdown-menu>

    <dropdown-menu>
      <template slot="dropdown-button">
        <i class="fas fa-random"></i> Misc
      </template>
      <template slot="dropdown-content">
        <dropdown-item @click="insertColumnBreak"><i class="fas fa-columns"></i> Column Break</dropdown-item>
        <dropdown-item @click="insertWideBlock"><i class="fas fa-arrows-alt-h"></i> Wide Block</dropdown-item>
        <dropdown-item @click="insertVerticalSpacing"><i class="fas fa-arrows-alt-v"></i> Vertical Spacing</dropdown-item>
      </template>
    </dropdown-menu>

    <dropdown-menu>
      <template slot="dropdown-button">
        <i class="fas fa-font"></i> Fonts
      </template>
      <template slot="dropdown-content">
        <dropdown-item @click="insertCustomTitlePageFont"><i class="fas fa-font"></i> Title Font</dropdown-item>
        <dropdown-item @click="insertCustomHeadersFont"><i class="fas fa-font"></i> Headers Font</dropdown-item>
        <dropdown-item @click="insertCustomNoteHeadersFont"><i class="fas fa-font"></i> Note Headers Font</dropdown-item>
        <dropdown-item @click="insertCustomRegularTextFont"><i class="fas fa-font"></i> Regular Text Font</dropdown-item>
        <dropdown-item @click="insertCustomNewspaperHeadersFont"><i class="fas fa-font"></i> Newspaper Headers Font</dropdown-item>
        <dropdown-item @click="insertCustomNewspaperTextFont"><i class="fas fa-font"></i> Newspaper Text Font</dropdown-item>
        <dropdown-item @click="insertCustomHandwritingFont"><i class="fas fa-font"></i> Handwriting Font</dropdown-item>
      </template>
    </dropdown-menu>

    <button-item float-right @click="scrollToPage"><i class="fas fa-arrows-alt-v"></i> Locate</button-item>

    <dropdown-menu float-right>
      <template slot="dropdown-button">
        <i class="fas fa-file"></i> File
      </template>
      <template slot="dropdown-content">
        <dropdown-item @click="downloadGoogleDriveFile"><i class="fab fa-google-drive"></i> Download - Google Drive</dropdown-item>
        <dropdown-item @click="uploadGoogleDriveFile"><i class="fab fa-google-drive"></i> Upload - Google Drive</dropdown-item>
        <dropdown-item @click="downloadFile"><i class="fas fa-download"></i> Download File</dropdown-item>
        <dropdown-item @click="uploadFile"><i class="fas fa-upload"></i> Upload File</dropdown-item>
      </template>
    </dropdown-menu>

    <button-item float-right @click="syncFile" :disabled="!this.storageProviderFileId"><i class="fas fa-sync"></i> Sync</button-item>
    
  </div>
</template>

<script>
import ButtonItem from '@/components/ButtonItem';
import DropdownMenu from '@/components/DropdownMenu';
import DropdownItem from '@/components/DropdownItem';
import { mapGetters } from 'vuex';

export default {
  name: 'TheEditorToolbar',
  components: {
    ButtonItem,
    DropdownMenu,
    DropdownItem
  },
  computed: {
    ...mapGetters({
      storageProviderFileId: 'filepicker/fileId'
    })
  },
  methods: {
    insertPrimaryNote: function () { this.$emit('insertPrimaryNote'); },
    insertSecondaryNote: function () { this.$emit('insertSecondaryNote'); },
    insertTertiaryNote: function () { this.$emit('insertTertiaryNote'); },
    insertNewspaperNote: function () { this.$emit('insertNewspaperNote'); },
    insertHandwrittenNote: function () { this.$emit('insertHandwrittenNote'); },
    insertPhbNote: function () { this.$emit('insertPhbNote'); },
    insertCocStatBlock: function () { this.$emit('insertCocStatBlock'); },
    insertRegularTable: function () { this.$emit('insertRegularTable'); },
    insertRegularPage: function () { this.$emit('insertRegularPage'); },
    insertRelativeImage: function () { this.$emit('insertRelativeImage'); },
    insertAbsoluteImage: function () { this.$emit('insertAbsoluteImage'); },
    insertFullPageImage: function () { this.$emit('insertFullPageImage'); },
    insertTwoColumnPage: function () { this.$emit('insertTwoColumnPage'); },
    insertThreeColumnPage: function () { this.$emit('insertThreeColumnPage'); },
    insertTitlePage: function () { this.$emit('insertTitlePage'); },
    insertColumnBreak: function () { this.$emit('insertColumnBreak'); },
    insertWideBlock: function () { this.$emit('insertWideBlock'); },
    insertVerticalSpacing: function () { this.$emit('insertVerticalSpacing'); },
    insertCustomTitlePageFont: function () { this.$emit('insertCustomTitlePageFont'); },
    insertCustomHeadersFont: function () { this.$emit('insertCustomHeadersFont'); },
    insertCustomNoteHeadersFont: function () { this.$emit('insertCustomNoteHeadersFont'); },
    insertCustomRegularTextFont: function () { this.$emit('insertCustomRegularTextFont'); },
    insertCustomNewspaperHeadersFont: function () { this.$emit('insertCustomNewspaperHeadersFont'); },
    insertCustomNewspaperTextFont: function () { this.$emit('insertCustomNewspaperTextFont'); },
    insertCustomHandwritingFont: function () { this.$emit('insertCustomHandwritingFont'); },
    syncFile: function () { this.$emit('syncFile'); },
    downloadGoogleDriveFile: function () { this.$emit('downloadGoogleDriveFile'); },
    uploadGoogleDriveFile: function () { this.$emit('uploadGoogleDriveFile'); },
    downloadFile: function () { this.$emit('downloadFile'); },
    uploadFile: function () { this.$emit('uploadFile'); },
    scrollToPage: function () { this.$emit('scrollToPage'); }
  }
};
</script>

<style lang="scss" scoped>
.toolbar {
  height: 30px;
  width: 100%;
  background-color: $toolbar-background-color;
  overflow-x: auto;
  overflow-y: hidden;
  clear: both;
}

@media print {
  .toolbar {
    display: none !important;
    height: 0 !important;
  }
}
</style>
