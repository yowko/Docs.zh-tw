---
title: 開發複合控制項
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: d80564c71dad57ce9145fbedd45a1396df1ddfec
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746025"
---
# <a name="develop-a-composite-windows-forms-control"></a><span data-ttu-id="ed3d6-102">開發複合 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="ed3d6-102">Develop a composite Windows Forms control</span></span>

<span data-ttu-id="ed3d6-103">您可以結合其他的 Windows Form 控制項來開發複合 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="ed3d6-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="ed3d6-104">衍生自 <xref:System.Web.UI.UserControl> 的複合控制項稱為「使用者控制項」。</span><span class="sxs-lookup"><span data-stu-id="ed3d6-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="ed3d6-105">基底類別 <xref:System.Windows.Forms.UserControl> 提供鍵盤路徑給子控制項，以確保子控制項可以接收焦點。</span><span class="sxs-lookup"><span data-stu-id="ed3d6-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="ed3d6-106">如需使用者控制項的範例，請參閱[如何：在 Windows Forms 控制項](how-to-apply-attributes-in-windows-forms-controls.md)中套用屬性中的 <xref:System.Windows.Forms.UserControl> 範例。</span><span class="sxs-lookup"><span data-stu-id="ed3d6-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>

<span data-ttu-id="ed3d6-107">Visual Studio 中的 Windows Forms 設計工具會提供豐富的設計階段支援，以撰寫使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="ed3d6-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>

- [<span data-ttu-id="ed3d6-108">如何：在選擇工具箱項目對話方塊中顯示控制項</span><span class="sxs-lookup"><span data-stu-id="ed3d6-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)

- [<span data-ttu-id="ed3d6-109">逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合</span><span class="sxs-lookup"><span data-stu-id="ed3d6-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)

- [<span data-ttu-id="ed3d6-110">逐步解說：使用 Visual C# 繼承自 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="ed3d6-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

- [<span data-ttu-id="ed3d6-111">如何：為控制項提供工具箱點陣圖</span><span class="sxs-lookup"><span data-stu-id="ed3d6-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)

- [<span data-ttu-id="ed3d6-112">如何：繼承自現有的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="ed3d6-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)

- [<span data-ttu-id="ed3d6-113">逐步解說：在設計階段偵錯自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="ed3d6-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)

- [<span data-ttu-id="ed3d6-114">操作說明：繼承自 Control 類別</span><span class="sxs-lookup"><span data-stu-id="ed3d6-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)

- [<span data-ttu-id="ed3d6-115">如何：測試 UserControl 的執行階段行為</span><span class="sxs-lookup"><span data-stu-id="ed3d6-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

- [<span data-ttu-id="ed3d6-116">如何：在設計階段將控制項對齊表單邊緣</span><span class="sxs-lookup"><span data-stu-id="ed3d6-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)

- [<span data-ttu-id="ed3d6-117">如何：繼承自 UserControl 類別</span><span class="sxs-lookup"><span data-stu-id="ed3d6-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)

- [<span data-ttu-id="ed3d6-118">操作說明：撰寫 Windows Forms 的控制項</span><span class="sxs-lookup"><span data-stu-id="ed3d6-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)

- [<span data-ttu-id="ed3d6-119">操作說明：撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="ed3d6-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)

- [<span data-ttu-id="ed3d6-120">逐步解說：使用 Visual C# 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="ed3d6-120">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)

- [<span data-ttu-id="ed3d6-121">逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="ed3d6-121">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

- <span data-ttu-id="ed3d6-122">[如何：建立採用設計階段功能的 Windows Forms 控制項](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="ed3d6-122">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>

## <a name="see-also"></a><span data-ttu-id="ed3d6-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed3d6-123">See also</span></span>

- [<span data-ttu-id="ed3d6-124">操作說明：在 Windows Forms 控制項中套用屬性</span><span class="sxs-lookup"><span data-stu-id="ed3d6-124">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="ed3d6-125">使用 .NET Framework 開發自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="ed3d6-125">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="ed3d6-126">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="ed3d6-126">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
