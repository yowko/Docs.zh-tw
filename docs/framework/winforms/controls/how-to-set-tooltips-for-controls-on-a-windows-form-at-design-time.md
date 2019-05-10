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
ms.openlocfilehash: 0d6725fc1a00826870e6400bffce63a1788e802c
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211691"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="a1c18-102">HOW TO：在設計階段設定 Windows Form 上控制項的工具提示</span><span class="sxs-lookup"><span data-stu-id="a1c18-102">How to: Set ToolTips for controls on a Windows Form at design time</span></span>

<span data-ttu-id="a1c18-103">您可以設定<xref:System.Windows.Forms.ToolTip>在程式碼，或在 Windows Form 設計工具，在 Visual Studio 中的字串。</span><span class="sxs-lookup"><span data-stu-id="a1c18-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="a1c18-104">如需詳細資訊<xref:System.Windows.Forms.ToolTip>元件，請參閱 < [ToolTip 元件概觀](tooltip-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c18-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>

## <a name="set-a-tooltip-programmatically"></a><span data-ttu-id="a1c18-105">以程式設計方式設定工具提示</span><span class="sxs-lookup"><span data-stu-id="a1c18-105">Set a ToolTip programmatically</span></span>

1. <span data-ttu-id="a1c18-106">新增控制項，將會顯示工具提示。</span><span class="sxs-lookup"><span data-stu-id="a1c18-106">Add the control that will display the ToolTip.</span></span>

2. <span data-ttu-id="a1c18-107">使用<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>方法的<xref:System.Windows.Forms.ToolTip>元件。</span><span class="sxs-lookup"><span data-stu-id="a1c18-107">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="set-a-tooltip-in-the-designer"></a><span data-ttu-id="a1c18-108">設定設計工具中的工具提示</span><span class="sxs-lookup"><span data-stu-id="a1c18-108">Set a ToolTip in the designer</span></span>

1. <span data-ttu-id="a1c18-109">在 Visual Studio 中，新增<xref:System.Windows.Forms.ToolTip>元件至表單。</span><span class="sxs-lookup"><span data-stu-id="a1c18-109">In Visual Studio, add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>

2. <span data-ttu-id="a1c18-110">選取的控制項，將會顯示工具提示，或將它新增至表單。</span><span class="sxs-lookup"><span data-stu-id="a1c18-110">Select the control that will display the ToolTip, or add it to the form.</span></span>

3. <span data-ttu-id="a1c18-111">在 **屬性**視窗中，將**ToolTip1 的**適當的文字字串的值。</span><span class="sxs-lookup"><span data-stu-id="a1c18-111">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="a1c18-112">若要以程式設計方式移除工具提示</span><span class="sxs-lookup"><span data-stu-id="a1c18-112">To remove a ToolTip programmatically</span></span>

1. <span data-ttu-id="a1c18-113">使用<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>方法的<xref:System.Windows.Forms.ToolTip>元件。</span><span class="sxs-lookup"><span data-stu-id="a1c18-113">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="remove-a-tooltip-in-the-designer"></a><span data-ttu-id="a1c18-114">在設計工具中移除的工具提示</span><span class="sxs-lookup"><span data-stu-id="a1c18-114">Remove a ToolTip in the designer</span></span>

1. <span data-ttu-id="a1c18-115">在 Visual Studio 中，選取 顯示工具提示控制項。</span><span class="sxs-lookup"><span data-stu-id="a1c18-115">In Visual Studio, select the control that is displaying the ToolTip.</span></span>

2. <span data-ttu-id="a1c18-116">在 [**屬性**] 視窗中，刪除中的文字**ToolTip1 的**。</span><span class="sxs-lookup"><span data-stu-id="a1c18-116">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1c18-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1c18-117">See also</span></span>

- [<span data-ttu-id="a1c18-118">ToolTip 元件概觀</span><span class="sxs-lookup"><span data-stu-id="a1c18-118">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="a1c18-119">如何：變更 Windows Form ToolTip 元件的延遲時間</span><span class="sxs-lookup"><span data-stu-id="a1c18-119">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="a1c18-120">ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="a1c18-120">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
