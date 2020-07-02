---
title: 如何：在設計階段設定 Windows Form 上控制項的工具提示
description: 瞭解如何以程式設計方式或在 Visual Studio 的 Windows Form 設計工具中設定控制項的工具提示。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 144ba5b6bffb4a538e345f7b2df4a453fc6fd63d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618021"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="e2fab-103">如何：在設計階段設定 Windows Form 上控制項的工具提示</span><span class="sxs-lookup"><span data-stu-id="e2fab-103">How to: Set ToolTips for controls on a Windows Form at design time</span></span>

<span data-ttu-id="e2fab-104">您可以在程式 <xref:System.Windows.Forms.ToolTip> 代碼中，或在 Visual Studio 的 Windows Form 設計工具中設定字串。</span><span class="sxs-lookup"><span data-stu-id="e2fab-104">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="e2fab-105">如需元件的詳細資訊 <xref:System.Windows.Forms.ToolTip> ，請參閱[工具提示元件總覽](tooltip-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="e2fab-105">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>

## <a name="set-a-tooltip-programmatically"></a><span data-ttu-id="e2fab-106">以程式設計方式設定工具提示</span><span class="sxs-lookup"><span data-stu-id="e2fab-106">Set a ToolTip programmatically</span></span>

1. <span data-ttu-id="e2fab-107">加入將顯示工具提示的控制項。</span><span class="sxs-lookup"><span data-stu-id="e2fab-107">Add the control that will display the ToolTip.</span></span>

2. <span data-ttu-id="e2fab-108">使用 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 元件的方法 <xref:System.Windows.Forms.ToolTip> 。</span><span class="sxs-lookup"><span data-stu-id="e2fab-108">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="set-a-tooltip-in-the-designer"></a><span data-ttu-id="e2fab-109">在設計工具中設定工具提示</span><span class="sxs-lookup"><span data-stu-id="e2fab-109">Set a ToolTip in the designer</span></span>

1. <span data-ttu-id="e2fab-110">在 Visual Studio 中，將 <xref:System.Windows.Forms.ToolTip> 元件新增至表單。</span><span class="sxs-lookup"><span data-stu-id="e2fab-110">In Visual Studio, add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>

2. <span data-ttu-id="e2fab-111">選取要顯示工具提示的控制項，或將它新增至表單。</span><span class="sxs-lookup"><span data-stu-id="e2fab-111">Select the control that will display the ToolTip, or add it to the form.</span></span>

3. <span data-ttu-id="e2fab-112">在 [**屬性**] 視窗中，將 [ToolTip1 值]**上的工具提示**設定為適當的文字字串。</span><span class="sxs-lookup"><span data-stu-id="e2fab-112">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="e2fab-113">以程式設計方式移除工具提示</span><span class="sxs-lookup"><span data-stu-id="e2fab-113">To remove a ToolTip programmatically</span></span>

1. <span data-ttu-id="e2fab-114">使用 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 元件的方法 <xref:System.Windows.Forms.ToolTip> 。</span><span class="sxs-lookup"><span data-stu-id="e2fab-114">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="remove-a-tooltip-in-the-designer"></a><span data-ttu-id="e2fab-115">移除設計師中的工具提示</span><span class="sxs-lookup"><span data-stu-id="e2fab-115">Remove a ToolTip in the designer</span></span>

1. <span data-ttu-id="e2fab-116">在 [Visual Studio 中，選取顯示工具提示的控制項。</span><span class="sxs-lookup"><span data-stu-id="e2fab-116">In Visual Studio, select the control that is displaying the ToolTip.</span></span>

2. <span data-ttu-id="e2fab-117">在 [**屬性**] 視窗中，刪除**ToolTip1 上工具提示**中的文字。</span><span class="sxs-lookup"><span data-stu-id="e2fab-117">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2fab-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2fab-118">See also</span></span>

- [<span data-ttu-id="e2fab-119">ToolTip 元件概觀</span><span class="sxs-lookup"><span data-stu-id="e2fab-119">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="e2fab-120">操作說明：變更 Windows Forms ToolTip 元件的延遲時間</span><span class="sxs-lookup"><span data-stu-id="e2fab-120">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="e2fab-121">ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="e2fab-121">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
