---
title: "如何：在 ToolStrip 控制項中建立切換按鈕"
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
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a8529637db7bc4cca011d0992b257d5b8ce9aaff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
