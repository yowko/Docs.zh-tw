---
title: 如何：變更 ToolStrip 文字和影像的外觀
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
ms.openlocfilehash: 7816e138e44554683c201895ece1f886ace8bfa6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746604"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>如何：變更 Windows Form 中 ToolStrip 文字和影像的外觀
您可以控制是否要在 <xref:System.Windows.Forms.ToolStripItem> 上顯示文字和影像，以及它們彼此相對的對齊方式和 <xref:System.Windows.Forms.ToolStrip>。  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>定義 ToolStripItem 上顯示的內容  
  
- 將 [<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>] 屬性設為所需的值。 可能的情況包括 `Image`、`ImageAndText`、`None`和 `Text`。 預設為 `ImageAndText`。  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>對齊 ToolStripItem 上的文字  
  
- 將 [<xref:System.Windows.Forms.ToolStripItem.TextAlign%2A>] 屬性設為所需的值。 這些可能是靠左、置中和靠右的任意組合。 預設為 `MiddleCenter`。  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>在 ToolStripItem 上對齊影像  
  
- 將 [<xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>] 屬性設為所需的值。 這些可能是靠左、置中和靠右的任意組合。 預設為 `MiddleLeft`。  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>若要定義 ToolStripItem 文字和影像彼此之間的顯示方式  
  
- 將 [<xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>] 屬性設為所需的值。 可能的情況包括 `ImageAboveText`、`ImageBeforeText`、`Overlay`、`TextAboveImage`和 `TextBeforeImage`。 預設為 `ImageBeforeText`。  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.ToolStrip>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控制項架構](toolstrip-control-architecture.md)
- [ToolStrip 技術摘要](toolstrip-technology-summary.md)
