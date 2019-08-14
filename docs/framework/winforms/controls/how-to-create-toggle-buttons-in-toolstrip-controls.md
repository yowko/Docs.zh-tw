---
title: 作法：在 ToolStrip 控制項中建立切換按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: 6a003b91cd4db5db2790a20db97dbaa4d8925e96
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972359"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="24552-102">作法：在 ToolStrip 控制項中建立切換按鈕</span><span class="sxs-lookup"><span data-stu-id="24552-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>

<span data-ttu-id="24552-103">當使用者按一下切換按鈕時, 它會顯示為凹陷, 並會保留凹陷的外觀, 直到使用者再次按一下按鈕為止。</span><span class="sxs-lookup"><span data-stu-id="24552-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>

## <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="24552-104">建立切換 ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="24552-104">To create a toggling ToolStripButton</span></span>

- <span data-ttu-id="24552-105">使用程式碼, 如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="24552-105">Use code such as the following code example.</span></span> <span data-ttu-id="24552-106">此程式碼假設您的表單<xref:System.Windows.Forms.ToolStrip>包含控制項, 而且其<xref:System.Windows.Forms.ToolStrip.Items%2A>集合包含名<xref:System.Windows.Forms.ToolStripButton> `toolStripButton1`為的。</span><span class="sxs-lookup"><span data-stu-id="24552-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="24552-107">它也假設您有一個稱為`toolStripButton1_CheckedChanged`的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="24552-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="24552-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24552-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStripButton>
- [<span data-ttu-id="24552-109">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="24552-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
