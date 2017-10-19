# Mainpanel Source Code 

```javascript
/**
 * @class Viewer.view.main.Main
 */
Ext.define('Viewer.view.main.Main', {
    extend: 'Ext.tab.Panel',
    xtype: 'app-main',

    requires: [
        'Ext.button.Button',
        'Ext.layout.container.boxOverflow.None',
        'Ext.plugin.Responsive',
        'MarkdownPanel.panel.MarkdownPanel',
        'PdfViewer.view.panel.PDF',
        'Viewer.view.main.MainController'
    ],

    controller: 'main',

    ui: 'navigation',

    tabBarHeaderPosition: 1,
    titleRotation: 0,
    tabRotation: 0,

    header: {
        layout: {
            align: 'stretchmax'
        },
        title: {
            text: 'ext-pdf-viewer',
            flex: 0
        },
        iconCls: 'fa-th-list'
    },

    tabBar: {
        flex: 1,
        layout: {
            align: 'stretch',
            overflowHandler: 'none'
        }
    },

    responsiveConfig: {
        tall: {
            headerPosition: 'top'
        },
        wide: {
            headerPosition: 'left'
        }
    },

    defaults: {
        bodyPadding: 20,
        tabConfig: {
            plugins: 'responsive',
            responsiveConfig: {
                wide: {
                    iconAlign: 'left',
                    textAlign: 'left'
                },
                tall: {
                    iconAlign: 'top',
                    textAlign: 'center',
                    width: 120
                }
            }
        }
    },

    items: [{
        title: 'Viewer 1 (cors)',
        iconCls: 'fa-file-pdf-o',
        xtype: 'PdfViewerPdfPanel',
        showPerPage: true,
        src: 'https://cdn.mozilla.net/pdfjs/tracemonkey.pdf'
    }, {
        title: 'Viewer 2 (local)',
        iconCls: 'fa-file-pdf-o',
        xtype: 'PdfViewerPdfPanel',
        pageScale: 2,
        src: '/data/The Rise of Web Technology.pdf'
    }, {
        title: 'Viewer 3 (dynamic)',
        iconCls: 'fa-file-pdf-o',
        xtype: 'PdfViewerPdfPanel',
        dockedItems: [{
            dock: 'top',
            xtype: 'toolbar',
            items: [{
                xtype: 'button',
                text: 'Load PDF 1',
                scope: this,
                handler: function (btn) {
                    btn.up('PdfViewerPdfPanel').setSrc('/data/sample.pdf');
                }
            }, {
                xtype: 'button',
                text: 'Load PDF 2',
                scope: this,
                handler: function (btn) {
                    btn.up('PdfViewerPdfPanel').setSrc('/data/pdf.pdf');
                }
            }, {
                xtype: 'button',
                text: 'Load PDF 3',
                scope: this,
                handler: function (btn) {
                    btn.up('PdfViewerPdfPanel').setSrc('/data/HuckFinn.pdf');
                }
            }]
        }]
    }, {
        title: 'Source Code',
        xtype: 'MdPanel',
        rootFolder: '/data/doc/source',
        rootDocument: 'index.md',
        iconCls: 'fa fa-code'
    }, {
        title: 'Documentation',
        xtype: 'MdPanel',
        rootFolder: '/data/doc/documenation',
        rootDocument: 'READE.md',
        iconCls: 'fa fa-document-o'
    }]
});
```