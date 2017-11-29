---
title: "如何：在設計階段設定 Windows Form 上控制項的工具提示"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81716be53468242734c3d722eb21e020e58f65ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>如何：在設計階段設定 Windows Form 上控制項的工具提示
您可以設定<xref:System.Windows.Forms.ToolTip>字串在程式碼中或在 Windows Form 設計工具。 如需有關<xref:System.Windows.Forms.ToolTip>元件，請參閱[ToolTip 元件概觀](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-set-a-tooltip-programmatically"></a>以程式設計方式設定工具提示  
  
1.  新增控制項，將會顯示工具提示。  
  
2.  使用<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>方法<xref:System.Windows.Forms.ToolTip>元件。  
  
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
  
### <a name="to-set-a-tooltip-in-the-designer"></a>在設計工具中設定工具提示  
  
1.  新增 <xref:System.Windows.Forms.ToolTip> 元件至表單。  
  
2.  選取的控制項，會顯示工具提示中，或將它加入至表單。  
  
3.  在**屬性**視窗中，將**ToolTip1 的**適當的文字字串的值。  
  
## <a name="see-also"></a>另請參閱  
 [ToolTip 元件概觀](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [操作說明：變更 Windows Forms ToolTip 元件的延遲時間](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [ToolTip 元件](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
