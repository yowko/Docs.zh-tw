---
title: 如何：變更 Windows Form 中 ToolStrip 文字和影像的外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: d3f53291e24d6a57e798725b716a7fd56eb661b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>如何：變更 Windows Form 中 ToolStrip 文字和影像的外觀
您可以控制是否顯示文字和影像上<xref:System.Windows.Forms.ToolStripItem>和與彼此相對的對齊方式和<xref:System.Windows.Forms.ToolStrip>。  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>若要定義 ToolStripItem 上顯示的內容  
  
-   設定<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>屬性設為所需的值。 這些可能是`Image`， `ImageAndText`， `None`，和`Text`。 預設值為 `ImageAndText`。  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>至 ToolStripItem 上的文字對齊  
  
-   設定<xref:System.Windows.Forms.ToolStripItem.TextAlign%2A>屬性設為所需的值。 這些可能是上方、 中間與下方左、 置中與權限的任何組合。 預設值為 `MiddleCenter`。  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>若要對齊 ToolStripItem 上的影像  
  
-   設定<xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>屬性設為所需的值。 這些可能是上方、 中間與下方左、 置中與權限的任何組合。 預設值為 `MiddleLeft`。  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>來定義如何顯示相對於彼此的 ToolStripItem 文字和影像  
  
-   設定<xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>屬性設為所需的值。 這些可能是`ImageAboveText`， `ImageBeforeText`， `Overlay`， `TextAboveImage`，和`TextBeforeImage`。 預設值為 `ImageBeforeText`。  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolStrip>  
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
