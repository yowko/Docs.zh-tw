---
title: 如何：在 ToolStrip 控制項中建立切換按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: a04d531433273328c2d8eb0c5ef614f08c33952a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>如何：在 ToolStrip 控制項中建立切換按鈕
當使用者按一下切換按鈕時，它會下凹，並會保留這個狀態，直到使用者按一下按鈕一次。  
  
### <a name="to-create-a-toggling-toolstripbutton"></a>若要建立切換 ToolStripButton  
  
-   使用下列程式碼範例程式碼。 此程式碼假設您的表單包含<xref:System.Windows.Forms.ToolStrip>控制項，而且其<xref:System.Windows.Forms.ToolStrip.Items%2A>集合包含<xref:System.Windows.Forms.ToolStripButton>呼叫`toolStripButton1`。 它也假設您已呼叫事件處理常式`toolStripButton1_CheckedChanged`。  
  
    ```vb  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
    ```csharp  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolStripButton>  
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
