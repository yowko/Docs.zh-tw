---
title: 在設計階段開發 Windows Form 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1eebca72b8c564e6d846eba69b6b59139754738e
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015984"
---
# <a name="develop-windows-forms-controls-at-design-time"></a><span data-ttu-id="c3c80-102">在設計階段開發 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="c3c80-102">Develop Windows Forms controls at design time</span></span>

<span data-ttu-id="c3c80-103">針對控制項作者，.NET Framework 提供豐富的控制項撰寫技術。</span><span class="sxs-lookup"><span data-stu-id="c3c80-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="c3c80-104">作者不再只能設計作為預先存在之控制項集合的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="c3c80-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="c3c80-105">透過繼承，您可以從預先存在的複合控制項或預先存在的 Windows Forms 控制項來建立自己的控制項。</span><span class="sxs-lookup"><span data-stu-id="c3c80-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="c3c80-106">您也可以設計可實作自訂繪製的專屬控制項。</span><span class="sxs-lookup"><span data-stu-id="c3c80-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="c3c80-107">這些選項可提供視覺介面設計和功能的大量彈性。</span><span class="sxs-lookup"><span data-stu-id="c3c80-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="c3c80-108">若要利用這些功能，您應該熟悉物件程式設計概念。</span><span class="sxs-lookup"><span data-stu-id="c3c80-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="c3c80-109">您不需要徹底瞭解繼承, 但您可能會發現參考[繼承基本概念 (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)很有説明。</span><span class="sxs-lookup"><span data-stu-id="c3c80-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

<span data-ttu-id="c3c80-110">如果您想要建立自訂控制項以在 Web Forms 上使用，請參閱[開發自訂 ASP.NET 伺服器控制項](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="c3c80-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c3c80-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="c3c80-111">In this section</span></span>

<span data-ttu-id="c3c80-112">[逐步解說：撰寫複合控制項](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-112">[Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span></span>\
<span data-ttu-id="c3c80-113">示範如何在 C# 中建立簡單的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="c3c80-113">Shows how to create a simple composite control in C#.</span></span>

<span data-ttu-id="c3c80-114">[逐步解說：繼承自 Windows Forms 控制項](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-114">[Walkthrough: Inheriting from a Windows Forms Control](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span></span>\
<span data-ttu-id="c3c80-115">示範在 C# 中，如何使用繼承來建立簡單的 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="c3c80-115">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>

<span data-ttu-id="c3c80-116">[逐步解說：在 Windows Forms 控制項上使用智慧標籤執行一般工作](performing-common-tasks-using-smart-tags-on-wf-controls.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-116">[Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](performing-common-tasks-using-smart-tags-on-wf-controls.md)</span></span>\
<span data-ttu-id="c3c80-117">示範如何在 Windows Forms 控制項上使用智慧標籤功能。</span><span class="sxs-lookup"><span data-stu-id="c3c80-117">Shows how to use the smart tag feature on Windows Forms controls.</span></span>

<span data-ttu-id="c3c80-118">[逐步解說：使用 Designerserializationvisibilityattribute 序列化序列化標準類型的集合](serializing-collections-designerserializationvisibilityattribute.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-118">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)</span></span>\
<span data-ttu-id="c3c80-119">顯示如何使用<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType>屬性來序列化集合。</span><span class="sxs-lookup"><span data-stu-id="c3c80-119">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>

<span data-ttu-id="c3c80-120">[逐步解說：在設計階段進行自訂 Windows Forms 控制項的調試](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-120">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span></span>\
<span data-ttu-id="c3c80-121">示範如何偵錯 Windows Forms 控制項的設計階段行為。</span><span class="sxs-lookup"><span data-stu-id="c3c80-121">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>

<span data-ttu-id="c3c80-122">[逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項](creating-a-wf-control-design-time-features.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-122">[Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md)</span></span>\
<span data-ttu-id="c3c80-123">示範如何將複合控制項緊密整合至設計環境。</span><span class="sxs-lookup"><span data-stu-id="c3c80-123">Shows how to tightly integrate a composite control into the design environment.</span></span>

<span data-ttu-id="c3c80-124">[如何：Windows Forms 的作者控制項](how-to-author-controls-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-124">[How to: Author Controls for Windows Forms](how-to-author-controls-for-windows-forms.md)</span></span>\
<span data-ttu-id="c3c80-125">提供 Windows Forms 控制項實作考量的概觀。</span><span class="sxs-lookup"><span data-stu-id="c3c80-125">Provides an overview of considerations for implementing a Windows Forms control.</span></span>

<span data-ttu-id="c3c80-126">[如何：撰寫複合控制項](how-to-author-composite-controls.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-126">[How to: Author Composite Controls](how-to-author-composite-controls.md)</span></span>\
<span data-ttu-id="c3c80-127">示範如何透過繼承自複合控制項來建立控制項。</span><span class="sxs-lookup"><span data-stu-id="c3c80-127">Shows how to create a control by inheriting from a composite control.</span></span>

<span data-ttu-id="c3c80-128">[如何：繼承自 UserControl 類別](how-to-inherit-from-the-usercontrol-class.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-128">[How to: Inherit from the UserControl Class](how-to-inherit-from-the-usercontrol-class.md)</span></span>\
<span data-ttu-id="c3c80-129">提供如何建立複合控制項之程序的概觀。</span><span class="sxs-lookup"><span data-stu-id="c3c80-129">Provides an overview of the procedure for creating a composite control.</span></span>

<span data-ttu-id="c3c80-130">[如何：繼承自現有的 Windows Forms 控制項](how-to-inherit-from-existing-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-130">[How to: Inherit from Existing Windows Forms Controls](how-to-inherit-from-existing-windows-forms-controls.md)</span></span>\
<span data-ttu-id="c3c80-131">示範如何透過繼承自<xref:System.Windows.Forms.Button>控制項類別來建立擴充控制項。</span><span class="sxs-lookup"><span data-stu-id="c3c80-131">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>

<span data-ttu-id="c3c80-132">[如何：繼承自控制項類別](how-to-inherit-from-the-control-class.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-132">[How to: Inherit from the Control Class](how-to-inherit-from-the-control-class.md)</span></span>\
<span data-ttu-id="c3c80-133">提供如何建立擴充控制項的概觀。</span><span class="sxs-lookup"><span data-stu-id="c3c80-133">Provides an overview of creating an extended control.</span></span>

<span data-ttu-id="c3c80-134">[如何：在設計階段將控制項對齊表單邊緣](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-134">[How to: Align a Control to the Edges of Forms at Design Time](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span></span>\
<span data-ttu-id="c3c80-135">示範如何使用<xref:System.Windows.Forms.Control.Dock%2A>屬性, 將您的控制項對齊它所佔用表單的邊緣。</span><span class="sxs-lookup"><span data-stu-id="c3c80-135">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>

<span data-ttu-id="c3c80-136">[如何：在 [選擇工具箱專案] 對話方塊中顯示控制項](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-136">[How to: Display a Control in the Choose Toolbox Items Dialog Box](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>\
<span data-ttu-id="c3c80-137">示範如何安裝控制項的程序，讓它出現在 [自訂工具箱] 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="c3c80-137">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>

<span data-ttu-id="c3c80-138">[如何：提供控制項的工具箱點陣圖](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-138">[How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span></span>\
<span data-ttu-id="c3c80-139">示範如何使用<xref:System.Drawing.ToolboxBitmapAttribute> , 在 [**工具箱**] 中顯示自訂控制項旁邊的圖示。</span><span class="sxs-lookup"><span data-stu-id="c3c80-139">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="c3c80-140">[如何：測試 UserControl 的執行時間行為](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-140">[How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span></span>\
<span data-ttu-id="c3c80-141">示範如何使用 [UserControl 測試容器] 來測試複合控制項的行為。</span><span class="sxs-lookup"><span data-stu-id="c3c80-141">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>

<span data-ttu-id="c3c80-142">[Windows Forms 設計工具的設計階段錯誤](design-time-errors-in-the-windows-forms-designer.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-142">[Design-Time Errors in the Windows Forms Designer](design-time-errors-in-the-windows-forms-designer.md)</span></span>\
<span data-ttu-id="c3c80-143">說明 Windows Forms 設計工具載入失敗時，Microsoft Visual Studio 中所出現的設計階段錯誤清單的意義與使用。</span><span class="sxs-lookup"><span data-stu-id="c3c80-143">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>

<span data-ttu-id="c3c80-144">[針對控制項和元件撰寫進行疑難排解](troubleshooting-control-and-component-authoring.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-144">[Troubleshooting Control and Component Authoring](troubleshooting-control-and-component-authoring.md)</span></span>\
<span data-ttu-id="c3c80-145">示範如何診斷和修正在您撰寫自訂元件或控制項時可能發生的常見問題。</span><span class="sxs-lookup"><span data-stu-id="c3c80-145">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>

## <a name="reference"></a><span data-ttu-id="c3c80-146">參考資料</span><span class="sxs-lookup"><span data-stu-id="c3c80-146">Reference</span></span>

- <xref:System.Windows.Forms.Control?displayProperty=nameWithType>

- <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>

## <a name="related-sections"></a><span data-ttu-id="c3c80-147">相關章節</span><span class="sxs-lookup"><span data-stu-id="c3c80-147">Related sections</span></span>

<span data-ttu-id="c3c80-148">[使用 .NET Framework 開發自訂的 Windows Forms 控制項](developing-custom-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-148">[Developing Custom Windows Forms Controls with the .NET Framework](developing-custom-windows-forms-controls.md)</span></span>\
<span data-ttu-id="c3c80-149">討論如何使用 .NET Framework 建立您自己的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="c3c80-149">Discusses how to create your own custom controls with the .NET Framework.</span></span>

<span data-ttu-id="c3c80-150">[Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-150">[Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md)</span></span>\
<span data-ttu-id="c3c80-151">介紹設計目的是要簡化元件建立和使用的 Common Language Runtime。</span><span class="sxs-lookup"><span data-stu-id="c3c80-151">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="c3c80-152">這個簡化的重要層面是使用不同程式設計語言所撰寫之元件之間增強的互通性。</span><span class="sxs-lookup"><span data-stu-id="c3c80-152">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="c3c80-153">Common Language Specification (CLS) 可讓您建立可處理多種程式設計語言的工具和元件。</span><span class="sxs-lookup"><span data-stu-id="c3c80-153">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>

<span data-ttu-id="c3c80-154">[逐步解說：使用自訂群組件自動填入工具箱](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span><span class="sxs-lookup"><span data-stu-id="c3c80-154">[Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span></span>\
<span data-ttu-id="c3c80-155">描述如何讓元件或控制項顯示在 [自訂工具箱] 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="c3c80-155">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>
