---
title: 開發複合 Windows Form 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: 82d76c1656ff14c6d1c9bbbb1c79ec3a30708a90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635711"
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="94c78-102">開發複合 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="94c78-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="94c78-103">您可以結合其他的 Windows Form 控制項來開發複合 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="94c78-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="94c78-104">複合控制項是衍生自<xref:System.Web.UI.UserControl>稱為使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="94c78-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="94c78-105">基底類別 <xref:System.Windows.Forms.UserControl> 提供鍵盤路徑給子控制項，以確保子控制項可以接收焦點。</span><span class="sxs-lookup"><span data-stu-id="94c78-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="94c78-106">如需使用者控制項的範例，請參閱 <<c0> <xref:System.Windows.Forms.UserControl> 範例中[How to:在 Windows Form 控制項中套用屬性](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="94c78-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="94c78-107">在 Visual Studio 中的 Windows Form 設計工具對於撰寫使用者控制項，提供豐富的設計階段支援。</span><span class="sxs-lookup"><span data-stu-id="94c78-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>  
  
-   <span data-ttu-id="94c78-108">[如何：顯示中的控制項選擇工具箱項目對話方塊](https://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="94c78-108">[How to: Display a Control in the Choose Toolbox Items Dialog Box](https://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span></span>  
  
-   [<span data-ttu-id="94c78-109">逐步解說：序列化標準類型使用 DesignerSerializationVisibilityAttribute 集合</span><span class="sxs-lookup"><span data-stu-id="94c78-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   <span data-ttu-id="94c78-110">[逐步解說：繼承自 Windows Forms 控制項的視覺化C# ](https://msdn.microsoft.com/library/09476da0-8d4c-4a4c-b969-649519dfb438))</span><span class="sxs-lookup"><span data-stu-id="94c78-110">[Walkthrough: Inheriting from a Windows Forms Control with Visual C#](https://msdn.microsoft.com/library/09476da0-8d4c-4a4c-b969-649519dfb438))</span></span>  
  
-   <span data-ttu-id="94c78-111">[如何：為控制項提供工具箱點陣圖](https://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="94c78-111">[How to: Provide a Toolbox Bitmap for a Control](https://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="94c78-112">[如何：繼承自現有的 Windows Forms 控制項](https://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="94c78-112">[How to: Inherit from Existing Windows Forms Controls](https://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="94c78-113">[逐步解說：在設計階段針對自訂 Windows Forms 控制項進行偵錯](https://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="94c78-113">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](https://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="94c78-114">[如何：繼承自 Control 類別](https://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="94c78-114">[How to: Inherit from the Control Class](https://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span></span>  
  
-   [<span data-ttu-id="94c78-115">如何：測試 UserControl 的執行階段行為</span><span class="sxs-lookup"><span data-stu-id="94c78-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   <span data-ttu-id="94c78-116">[如何：將控制項和表單邊緣對齊在設計階段](https://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="94c78-116">[How to: Align a Control to the Edges of Forms at Design Time](https://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="94c78-117">[如何：繼承自 UserControl 類別](https://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="94c78-117">[How to: Inherit from the UserControl Class](https://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="94c78-118">[如何：撰寫 Windows forms 的控制項](https://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="94c78-118">[How to: Author Controls for Windows Forms](https://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="94c78-119">[如何：撰寫複合控制項](https://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="94c78-119">[How to: Author Composite Controls](https://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="94c78-120">[逐步解說：撰寫使用 Visual Basic 複合控制項](https://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="94c78-120">[Walkthrough: Authoring a Composite Control with Visual Basic](https://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="94c78-121">[逐步解說：撰寫複合控制項的視覺化C# ](https://msdn.microsoft.com/library/f88481a8-c746-4a36-9479-374ce5f2e91f))</span><span class="sxs-lookup"><span data-stu-id="94c78-121">[Walkthrough: Authoring a Composite Control with Visual C#](https://msdn.microsoft.com/library/f88481a8-c746-4a36-9479-374ce5f2e91f))</span></span>  
  
-   <span data-ttu-id="94c78-122">[逐步解說：繼承自使用 Visual Basic 的 Windows Forms 控制項](https://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="94c78-122">[Walkthrough: Inheriting from a Windows Forms Control with Visual Basic](https://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="94c78-123">[如何：建立採用設計階段功能的 Windows Form 控制項](https://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="94c78-123">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="94c78-124">[如何：建立採用設計階段功能的 Windows Form 控制項](https://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="94c78-124">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c78-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94c78-125">See also</span></span>
- [<span data-ttu-id="94c78-126">如何：在 Windows Form 控制項中套用屬性</span><span class="sxs-lookup"><span data-stu-id="94c78-126">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="94c78-127">使用 .NET Framework 開發自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="94c78-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="94c78-128">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="94c78-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
