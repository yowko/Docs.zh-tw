---
title: 開發複合 Windows Form 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: bfbb9091d40652bdd1ae277f3a77feefbccbf080
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196459"
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="92c22-102">開發複合 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="92c22-103">您可以結合其他的 Windows Form 控制項來開發複合 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="92c22-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="92c22-104">複合控制項是衍生自<xref:System.Web.UI.UserControl>稱為使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="92c22-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="92c22-105">基底類別 <xref:System.Windows.Forms.UserControl> 提供鍵盤路徑給子控制項，以確保子控制項可以接收焦點。</span><span class="sxs-lookup"><span data-stu-id="92c22-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="92c22-106">如需使用者控制項的範例，請參閱 <<c0> <xref:System.Windows.Forms.UserControl> 範例中[How to:在 Windows Form 控制項中套用屬性](how-to-apply-attributes-in-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="92c22-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="92c22-107">在 Visual Studio 中的 Windows Form 設計工具對於撰寫使用者控制項，提供豐富的設計階段支援。</span><span class="sxs-lookup"><span data-stu-id="92c22-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>  
  
-   [<span data-ttu-id="92c22-108">HOW TO：在 [選擇工具箱項目] 對話方塊中顯示控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
  
-   [<span data-ttu-id="92c22-109">逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合</span><span class="sxs-lookup"><span data-stu-id="92c22-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   [<span data-ttu-id="92c22-110">逐步解說：使用 Visual C# 繼承來自 Windows Form 的控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
  
-   [<span data-ttu-id="92c22-111">HOW TO：提供控制項的工具箱點陣圖</span><span class="sxs-lookup"><span data-stu-id="92c22-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
  
-   [<span data-ttu-id="92c22-112">HOW TO：繼承現有的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)  
  
-   [<span data-ttu-id="92c22-113">逐步解說：在設計階段偵錯自訂 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
  
-   [<span data-ttu-id="92c22-114">HOW TO：繼承控制項類別</span><span class="sxs-lookup"><span data-stu-id="92c22-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)  
  
-   [<span data-ttu-id="92c22-115">HOW TO：測試 UserControl 的執行階段行為</span><span class="sxs-lookup"><span data-stu-id="92c22-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   [<span data-ttu-id="92c22-116">HOW TO：在設計階段將控制項對齊表單邊緣</span><span class="sxs-lookup"><span data-stu-id="92c22-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
  
-   [<span data-ttu-id="92c22-117">HOW TO：繼承 UserControl 類別</span><span class="sxs-lookup"><span data-stu-id="92c22-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)  
  
-   [<span data-ttu-id="92c22-118">HOW TO：撰寫 Windows Forms 的控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)  
  
-   [<span data-ttu-id="92c22-119">HOW TO：撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)  
  
-   [<span data-ttu-id="92c22-120">逐步解說：使用 Visual Basic 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-120">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
  
-   [<span data-ttu-id="92c22-121">逐步解說：使用 Visual C# 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-121">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
  
-   [<span data-ttu-id="92c22-122">逐步解說：使用 Visual Basic 繼承 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-122">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
  
-   [<span data-ttu-id="92c22-123">逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-123">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
  
-   [<span data-ttu-id="92c22-124">HOW TO：建立採用設計階段功能的 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-124">How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))  
  
## <a name="see-also"></a><span data-ttu-id="92c22-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92c22-125">See also</span></span>

- [<span data-ttu-id="92c22-126">HOW TO：在 Windows Forms 控制項中套用屬性</span><span class="sxs-lookup"><span data-stu-id="92c22-126">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="92c22-127">使用 .NET Framework 開發自訂的 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="92c22-128">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="92c22-128">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
