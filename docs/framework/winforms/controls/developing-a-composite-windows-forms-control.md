---
title: "開發複合 Windows Form 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da180f888031aace892efc770184be53e9341047
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="cfadc-102">開發複合 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="cfadc-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="cfadc-103">您可以結合其他的 Windows Form 控制項來開發複合 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="cfadc-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="cfadc-104">複合控制項衍生自<xref:System.Web.UI.UserControl>稱為使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="cfadc-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="cfadc-105">基底類別 <xref:System.Windows.Forms.UserControl> 提供鍵盤路徑給子控制項，以確保子控制項可以接收焦點。</span><span class="sxs-lookup"><span data-stu-id="cfadc-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="cfadc-106">如需使用者控制項的範例，請參閱<xref:System.Windows.Forms.UserControl>範例[How to： 適用於 Windows Form 控制項中的屬性](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="cfadc-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="cfadc-107">在 [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] 中的 Windows Form 設計工具對於撰寫使用者控制項提供豐富的設計階段支援。</span><span class="sxs-lookup"><span data-stu-id="cfadc-107">The Windows Forms designer in [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] provides rich design-time support for authoring user controls.</span></span>  
  
-   <span data-ttu-id="cfadc-108">[如何：在選擇工具箱項目對話方塊中顯示控制項](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-108">[How to: Display a Control in the Choose Toolbox Items Dialog Box](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-109">[逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-109">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-110">[逐步解說：使用 Visual C# 繼承自 Windows Forms 控制項](http://msdn.microsoft.com/en-us/09476da0-8d4c-4a4c-b969-649519dfb438))</span><span class="sxs-lookup"><span data-stu-id="cfadc-110">[Walkthrough: Inheriting from a Windows Forms Control with Visual C#](http://msdn.microsoft.com/en-us/09476da0-8d4c-4a4c-b969-649519dfb438))</span></span>  
  
-   <span data-ttu-id="cfadc-111">[如何：為控制項提供工具箱點陣圖](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-111">[How to: Provide a Toolbox Bitmap for a Control](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-112">[如何：繼承自現有的 Windows Forms 控制項](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-112">[How to: Inherit from Existing Windows Forms Controls](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-113">[逐步解說：在設計階段偵錯自訂的 Windows Forms 控制項](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-113">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-114">[如何：繼承自 Control 類別](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-114">[How to: Inherit from the Control Class](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-115">[如何：測試 UserControl 的執行階段行為](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-115">[How to: Test the Run-Time Behavior of a UserControl](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-116">[如何：在設計階段將控制項對齊表單邊緣](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-116">[How to: Align a Control to the Edges of Forms at Design Time](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-117">[如何：繼承自 UserControl 類別](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-117">[How to: Inherit from the UserControl Class](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-118">[如何：撰寫 Windows Forms 的控制項](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-118">[How to: Author Controls for Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-119">[如何：撰寫複合控制項](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-119">[How to: Author Composite Controls](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-120">[逐步解說：使用 Visual Basic 撰寫複合控制項](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-120">[Walkthrough: Authoring a Composite Control with Visual Basic](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-121">[逐步解說：使用 Visual C# 撰寫複合控制項](http://msdn.microsoft.com/en-us/f88481a8-c746-4a36-9479-374ce5f2e91f))</span><span class="sxs-lookup"><span data-stu-id="cfadc-121">[Walkthrough: Authoring a Composite Control with Visual C#](http://msdn.microsoft.com/en-us/f88481a8-c746-4a36-9479-374ce5f2e91f))</span></span>  
  
-   <span data-ttu-id="cfadc-122">[逐步解說：使用 Visual Basic 繼承自 Windows Forms 控制項](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-122">[Walkthrough: Inheriting from a Windows Forms Control with Visual Basic](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-123">[如何：建立採用設計階段功能的 Windows Forms 控制項](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-123">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="cfadc-124">[如何：建立採用設計階段功能的 Windows Forms 控制項](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="cfadc-124">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfadc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfadc-125">See Also</span></span>  
 [<span data-ttu-id="cfadc-126">操作說明：在 Windows Forms 控制項中套用屬性</span><span class="sxs-lookup"><span data-stu-id="cfadc-126">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="cfadc-127">使用 .NET Framework 開發自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="cfadc-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="cfadc-128">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="cfadc-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
