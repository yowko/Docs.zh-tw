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
ms.workload: dotnet
ms.openlocfilehash: 5547b35bda8054b3ca41435e04855408d8a77c8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="85286-102">如何：在 ToolStrip 控制項中建立切換按鈕</span><span class="sxs-lookup"><span data-stu-id="85286-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>
<span data-ttu-id="85286-103">當使用者按一下切換按鈕時，它會下凹，並會保留這個狀態，直到使用者按一下按鈕一次。</span><span class="sxs-lookup"><span data-stu-id="85286-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>  
  
### <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="85286-104">若要建立切換 ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="85286-104">To create a toggling ToolStripButton</span></span>  
  
-   <span data-ttu-id="85286-105">使用下列程式碼範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="85286-105">Use code such as the following code example.</span></span> <span data-ttu-id="85286-106">此程式碼假設您的表單包含<xref:System.Windows.Forms.ToolStrip>控制項，而且其<xref:System.Windows.Forms.ToolStrip.Items%2A>集合包含<xref:System.Windows.Forms.ToolStripButton>呼叫`toolStripButton1`。</span><span class="sxs-lookup"><span data-stu-id="85286-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="85286-107">它也假設您已呼叫事件處理常式`toolStripButton1_CheckedChanged`。</span><span class="sxs-lookup"><span data-stu-id="85286-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="85286-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="85286-108">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripButton>  
 [<span data-ttu-id="85286-109">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="85286-109">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
