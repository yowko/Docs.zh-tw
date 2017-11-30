---
title: "在設計階段開發 Windows Form 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4f9680bb64339f2f232793beb9c47a36c07aa4a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="developing-windows-forms-controls-at-design-time"></a><span data-ttu-id="5cf5d-102">在設計階段開發 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="5cf5d-102">Developing Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="5cf5d-103">針對控制項作者，.NET Framework 提供豐富的控制項撰寫技術。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="5cf5d-104">作者不再只能設計作為預先存在之控制項集合的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="5cf5d-105">透過繼承，您可以從預先存在的複合控制項或預先存在的 Windows Forms 控制項來建立自己的控制項。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="5cf5d-106">您也可以設計可實作自訂繪製的專屬控制項。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="5cf5d-107">這些選項可提供視覺介面設計和功能的大量彈性。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="5cf5d-108">若要利用這些功能，您應該熟悉物件程式設計概念。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cf5d-109">不需要完全了解的繼承，但您可能會有用來參考[繼承基本概念 (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="5cf5d-110">如果您想要建立自訂控制項以在 Web Forms 上使用，請參閱[開發自訂 ASP.NET 伺服器控制項](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5cf5d-111">本章節內容</span><span class="sxs-lookup"><span data-stu-id="5cf5d-111">In This Section</span></span>  
 [<span data-ttu-id="5cf5d-112">逐步解說：使用 Visual Basic 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="5cf5d-112">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 <span data-ttu-id="5cf5d-113">示範如何在 Visual Basic 中建立簡單的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-113">Shows how to create a simple composite control in Visual Basic.</span></span>  
  
 [<span data-ttu-id="5cf5d-114">逐步解說：使用 Visual C# 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="5cf5d-114">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 <span data-ttu-id="5cf5d-115">示範如何在 C# 中建立簡單的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-115">Shows how to create a simple composite control in C#.</span></span>  
  
 [<span data-ttu-id="5cf5d-116">逐步解說：使用 Visual Basic 繼承自 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="5cf5d-116">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 <span data-ttu-id="5cf5d-117">示範在 Visual Basic 中，如何使用繼承來建立簡單的 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-117">Shows how to create a simple Windows Forms control using inheritance in Visual Basic.</span></span>  
  
 [<span data-ttu-id="5cf5d-118">逐步解說：使用 Visual C# 繼承自 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="5cf5d-118">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 <span data-ttu-id="5cf5d-119">示範在 C# 中，如何使用繼承來建立簡單的 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-119">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>  
  
 [<span data-ttu-id="5cf5d-120">逐步解說：使用 Windows Forms 控制項中的智慧標籤執行一般工作</span><span class="sxs-lookup"><span data-stu-id="5cf5d-120">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 <span data-ttu-id="5cf5d-121">示範如何在 Windows Forms 控制項上使用智慧標籤功能。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-121">Shows how to use the smart tag feature on Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="5cf5d-122">逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合</span><span class="sxs-lookup"><span data-stu-id="5cf5d-122">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 <span data-ttu-id="5cf5d-123">示範如何使用<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType>序列化集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-123">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>  
  
 [<span data-ttu-id="5cf5d-124">逐步解說：在設計階段偵錯自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="5cf5d-124">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 <span data-ttu-id="5cf5d-125">示範如何偵錯 Windows Forms 控制項的設計階段行為。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-125">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="5cf5d-126">逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="5cf5d-126">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 <span data-ttu-id="5cf5d-127">示範如何將複合控制項緊密整合至設計環境。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-127">Shows how to tightly integrate a composite control into the design environment.</span></span>  
  
 [<span data-ttu-id="5cf5d-128">如何：撰寫 Windows Forms 的控制項</span><span class="sxs-lookup"><span data-stu-id="5cf5d-128">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 <span data-ttu-id="5cf5d-129">提供 Windows Forms 控制項實作考量的概觀。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-129">Provides an overview of considerations for implementing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="5cf5d-130">如何：撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="5cf5d-130">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 <span data-ttu-id="5cf5d-131">示範如何透過繼承自複合控制項來建立控制項。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-131">Shows how to create a control by inheriting from a composite control.</span></span>  
  
 [<span data-ttu-id="5cf5d-132">如何：繼承自 UserControl 類別</span><span class="sxs-lookup"><span data-stu-id="5cf5d-132">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 <span data-ttu-id="5cf5d-133">提供如何建立複合控制項之程序的概觀。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-133">Provides an overview of the procedure for creating a composite control.</span></span>  
  
 [<span data-ttu-id="5cf5d-134">操作說明：繼承自現有的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="5cf5d-134">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 <span data-ttu-id="5cf5d-135">示範如何建立擴充的控制項，透過繼承自<xref:System.Windows.Forms.Button>控制項類別。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-135">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>  
  
 [<span data-ttu-id="5cf5d-136">操作說明：繼承自 Control 類別</span><span class="sxs-lookup"><span data-stu-id="5cf5d-136">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 <span data-ttu-id="5cf5d-137">提供如何建立擴充控制項的概觀。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-137">Provides an overview of creating an extended control.</span></span>  
  
 [<span data-ttu-id="5cf5d-138">操作說明：在設計階段將控制項對齊表單邊緣</span><span class="sxs-lookup"><span data-stu-id="5cf5d-138">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 <span data-ttu-id="5cf5d-139">示範如何使用<xref:System.Windows.Forms.Control.Dock%2A>屬性，以您的控制項，會佔用的表單的邊緣對齊。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-139">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>  
  
 [<span data-ttu-id="5cf5d-140">操作說明：在選擇工具箱項目對話方塊中顯示控制項</span><span class="sxs-lookup"><span data-stu-id="5cf5d-140">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 <span data-ttu-id="5cf5d-141">示範如何安裝控制項的程序，讓它出現在 [自訂工具箱] 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-141">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>  
  
 [<span data-ttu-id="5cf5d-142">操作說明：為控制項提供工具箱點陣圖</span><span class="sxs-lookup"><span data-stu-id="5cf5d-142">How to: Provide a Toolbox Bitmap for a Control</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 <span data-ttu-id="5cf5d-143">示範如何使用<xref:System.Drawing.ToolboxBitmapAttribute>顯示自訂控制項旁的圖示**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-143">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>  
  
 [<span data-ttu-id="5cf5d-144">操作說明：測試 UserControl 的執行階段行為</span><span class="sxs-lookup"><span data-stu-id="5cf5d-144">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 <span data-ttu-id="5cf5d-145">示範如何使用 [UserControl 測試容器] 來測試複合控制項的行為。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-145">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>  
  
 [<span data-ttu-id="5cf5d-146">Windows Forms 設計工具的設計階段錯誤</span><span class="sxs-lookup"><span data-stu-id="5cf5d-146">Design-Time Errors in the Windows Forms Designer</span></span>](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 <span data-ttu-id="5cf5d-147">說明 Windows Forms 設計工具載入失敗時，Microsoft Visual Studio 中所出現的設計階段錯誤清單的意義與使用。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-147">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>  
  
 [<span data-ttu-id="5cf5d-148">針對控制項和元件撰寫進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="5cf5d-148">Troubleshooting Control and Component Authoring</span></span>](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="5cf5d-149">示範如何診斷和修正在您撰寫自訂元件或控制項時可能發生的常見問題。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-149">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5cf5d-150">參考資料</span><span class="sxs-lookup"><span data-stu-id="5cf5d-150">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="5cf5d-151">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-151">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="5cf5d-152">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-152">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5cf5d-153">相關章節</span><span class="sxs-lookup"><span data-stu-id="5cf5d-153">Related Sections</span></span>  
 [<span data-ttu-id="5cf5d-154">使用 .NET Framework 開發自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="5cf5d-154">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 <span data-ttu-id="5cf5d-155">討論如何使用 .NET Framework 建立您自己的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-155">Discusses how to create your own custom controls with the .NET Framework.</span></span>  
  
 [<span data-ttu-id="5cf5d-156">語言獨立性以及與語言無關的元件</span><span class="sxs-lookup"><span data-stu-id="5cf5d-156">Language Independence and Language-Independent Components</span></span>](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="5cf5d-157">介紹設計目的是要簡化元件建立和使用的 Common Language Runtime。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-157">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="5cf5d-158">這個簡化的重要層面是使用不同程式設計語言所撰寫之元件之間增強的互通性。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-158">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="5cf5d-159">Common Language Specification (CLS) 可讓您建立可處理多種程式設計語言的工具和元件。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-159">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>  
  
 [<span data-ttu-id="5cf5d-160">逐步解說：自動將自訂元件填入工具箱</span><span class="sxs-lookup"><span data-stu-id="5cf5d-160">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 <span data-ttu-id="5cf5d-161">描述如何讓元件或控制項顯示在 [自訂工具箱] 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="5cf5d-161">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>
