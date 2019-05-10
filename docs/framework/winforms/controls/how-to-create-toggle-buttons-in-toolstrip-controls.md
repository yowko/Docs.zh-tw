---
title: HOW TO：在 ToolStrip 控制項中建立切換按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: 21da5564bfeec01d448c23d3e734bdd16fc1566b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666427"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="997f7-102">HOW TO：在 ToolStrip 控制項中建立切換按鈕</span><span class="sxs-lookup"><span data-stu-id="997f7-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>
<span data-ttu-id="997f7-103">當使用者按一下切換按鈕時，它會出現下凹的連線，並保留下凹的外觀，直到使用者按一下按鈕時一次。</span><span class="sxs-lookup"><span data-stu-id="997f7-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>  
  
### <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="997f7-104">若要建立切換 prvek ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="997f7-104">To create a toggling ToolStripButton</span></span>  
  
- <span data-ttu-id="997f7-105">使用程式碼，如下列程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="997f7-105">Use code such as the following code example.</span></span> <span data-ttu-id="997f7-106">此程式碼假設您的表單包含<xref:System.Windows.Forms.ToolStrip>控制項，且其<xref:System.Windows.Forms.ToolStrip.Items%2A>集合包含<xref:System.Windows.Forms.ToolStripButton>稱為`toolStripButton1`。</span><span class="sxs-lookup"><span data-stu-id="997f7-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="997f7-107">同時也假設您已經呼叫事件處理常式`toolStripButton1_CheckedChanged`。</span><span class="sxs-lookup"><span data-stu-id="997f7-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="997f7-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="997f7-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStripButton>
- [<span data-ttu-id="997f7-109">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="997f7-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
