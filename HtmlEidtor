mport $ from 'jquery'
import './vendor/trumbowyg.min'

class CustomEditor {
  constructor (opts) {
    this.editors = document.querySelectorAll('.thesis-content-html')
    this.enabled = false
    this.onChange = opts.onChange
    this.changedHtmlEditor = this.changedHtmlEditor.bind(this)
  }

  enable () {
    if (this.enabled) return
    if (this.editors.length > 0) {
      $(this.editors).trumbowyg({
        btns: [
          ['viewHTML'],
          'btnGrp-design',
          ['formatting'],
          ['link'],
          ['justifyLeft', 'justifyCenter', 'justifyRight'],
          'btnGrp-lists',
          ['removeformat'],
          ['fullscreen']
        ]
      })
      $('.trumbowyg-box').css('z-index', 9999)
      $(this.editors).on('tbwchange', this.changedHtmlEditor)
    }
    this.enabled = true
  }

  disable () {
    if (!this.enabled) return
    $(this.editors).trumbowyg('destroy')
    this.enabled = false
  }

  content (ed) {
    return ed.innerHTML
  }

  set (name, data) {
    const ed = document.querySelector(`[data-thesis-content-id='${name}']`)
    if (!ed) return
    ed.innerHTML = data.content
    ed.classList.add('modified')
  }

  changedHtmlEditor (event) {
    event.target.classList.add('modified')
    this.onChange()
  }
}

window.CustomEditor = CustomEditor

export default CustomEditor
