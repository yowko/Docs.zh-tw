---
title: HOW TO：在設計階段設定 Windows Forms 的控制項工具提示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: cc8f8c620516a943d6d70187e19b72f5a2a99888
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013071"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>HOW TO：在設計階段設定 Windows Forms 的控制項工具提示
您可以設定<xref:System.Windows.Forms.ToolTip>在程式碼，或在 Windows Form 設計工具中的字串。 如需詳細資訊<xref:System.Windows.Forms.ToolTip>元件，請參閱 < [ToolTip 元件概觀](tooltip-component-overview-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-set-a-tooltip-programmatically"></a>以程式設計方式設定工具提示  
  
1. 新增控制項，將會顯示工具提示。  
  
2. 使用<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>方法的<xref:System.Windows.Forms.ToolTip>元件。  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a>若要在設計師中設定工具提示  
  
1. 新增 <xref:System.Windows.Forms.ToolTip> 元件至表單。  
  
2. 選取的控制項，將會顯示工具提示，或將它新增至表單。  
  
3. 在 **屬性**視窗中，將**ToolTip1 的**適當的文字字串的值。  

### <a name="to-remove-a-tooltip-programmatically"></a>若要以程式設計方式移除工具提示  
  
1. 使用<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>方法的<xref:System.Windows.Forms.ToolTip>元件。  
  
    ```vb  
    ' In this example, Button1 is the control displaying the ToolTip.  
    ToolTip1.SetToolTip(Button1, Nothing)  
    ```  
  
    ```csharp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1.SetToolTip(button1, null);  
    ```  
  
    ```cpp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1->SetToolTip(button1, NULL);  
    ```  
  
### <a name="to-remove-a-tooltip-in-the-designer"></a>若要在設計工具中移除的工具提示  
  
1. 選取顯示工具提示控制項。  
  
2. 在 [**屬性**] 視窗中，刪除中的文字**ToolTip1 的**。  

## <a name="see-also"></a>另請參閱

- [ToolTip 元件概觀](tooltip-component-overview-windows-forms.md)
- [如何：變更 Windows Form ToolTip 元件的延遲時間](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [ToolTip 元件](tooltip-component-windows-forms.md)
