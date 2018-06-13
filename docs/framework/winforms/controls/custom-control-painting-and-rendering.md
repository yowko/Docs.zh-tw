---
title: 自訂控制項繪製和轉譯
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: 18a05a739f42d41a650e66723f44aae69c1707c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526047"
---
# <a name="custom-control-painting-and-rendering"></a><span data-ttu-id="5a1bd-102">自訂控制項繪製和轉譯</span><span class="sxs-lookup"><span data-stu-id="5a1bd-102">Custom Control Painting and Rendering</span></span>
<span data-ttu-id="5a1bd-103">自訂繪製的控制項是容易由.NET Framework 的許多複雜工作。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-103">Custom painting of controls is one of the many complicated tasks made easy by the .NET Framework.</span></span> <span data-ttu-id="5a1bd-104">撰寫的自訂控制項，當您有許多有關控制項的圖形的外觀。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-104">When authoring a custom control, you have many options regarding your control's graphical appearance.</span></span> <span data-ttu-id="5a1bd-105">如果您撰寫控制項是繼承自`Control`，您必須提供程式碼，讓您的控制項轉譯其圖形表示。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-105">If you are authoring a control that inherits from the `Control`, you must provide code that allows your control to render its graphical representation.</span></span> <span data-ttu-id="5a1bd-106">如果您要建立使用者控制項透過繼承自`UserControl`，繼承或從其中一個 Windows Form 控制項，您可能會覆寫標準的圖形表示，並提供您自己的圖形的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-106">If you are creating a user control by inheriting from the `UserControl`, or are inheriting from one of the Windows Forms controls, you may override the standard graphical representation and provide your own graphics code.</span></span> <span data-ttu-id="5a1bd-107">如果您想要提供自訂的構成控制項轉譯`UserControl`撰寫時，您的選項變得更小，但仍然可讓各種不同的圖形化的控制項和應用程式的可能性。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-107">If you want to provide custom rendering for the constituent controls of a `UserControl` you are authoring, your options become more limited, but still allow a wide range of graphical possibilities for your controls and applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a1bd-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="5a1bd-108">In This Section</span></span>  
 [<span data-ttu-id="5a1bd-109">呈現 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="5a1bd-109">Rendering a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 <span data-ttu-id="5a1bd-110">示範如何撰寫程式顯示控制項的邏輯。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-110">Shows how to program the logic that displays a control.</span></span>  
  
 [<span data-ttu-id="5a1bd-111">使用者自訂描繪控制項</span><span class="sxs-lookup"><span data-stu-id="5a1bd-111">User-Drawn Controls</span></span>](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 <span data-ttu-id="5a1bd-112">提供撰寫和覆寫控制項的轉譯程式碼所需的步驟的概觀。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-112">Gives an overview of the steps involved in writing and overriding rendering code for your control.</span></span>  
  
 [<span data-ttu-id="5a1bd-113">組成控制項</span><span class="sxs-lookup"><span data-stu-id="5a1bd-113">Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 <span data-ttu-id="5a1bd-114">描述如何在使用者控制項和表單實作的組成控制項的自訂轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-114">Describes how to implement custom rendering code for constituent controls in your user controls and forms.</span></span>  
  
 [<span data-ttu-id="5a1bd-115">操作說明：在執行階段期間隱藏控制項</span><span class="sxs-lookup"><span data-stu-id="5a1bd-115">How to: Make Your Control Invisible at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 <span data-ttu-id="5a1bd-116">示範如何使用<xref:System.Windows.Forms.Control.Visible%2A>隱藏和顯示控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-116">Shows how to use the <xref:System.Windows.Forms.Control.Visible%2A> property to hide and show a control.</span></span>  
  
 [<span data-ttu-id="5a1bd-117">操作說明：為控制項提供透明背景</span><span class="sxs-lookup"><span data-stu-id="5a1bd-117">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 <span data-ttu-id="5a1bd-118">示範如何使用<xref:System.Windows.Forms.Control.SetStyle%2A>方法來建立不透明、 透明或透明部分的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-118">Shows how to use the <xref:System.Windows.Forms.Control.SetStyle%2A> method to create a background color that is opaque, transparent, or partially transparent.</span></span>  
  
 [<span data-ttu-id="5a1bd-119">使用視覺化樣式呈現控制項</span><span class="sxs-lookup"><span data-stu-id="5a1bd-119">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 <span data-ttu-id="5a1bd-120">示範如何呈現在支援的作業系統中使用視覺化樣式的控制項。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-120">Shows how to render controls using visual styles in operating systems that support them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5a1bd-121">參考資料</span><span class="sxs-lookup"><span data-stu-id="5a1bd-121">Reference</span></span>  
 <xref:System.Windows.Forms.Control>  
 <span data-ttu-id="5a1bd-122">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-122">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="5a1bd-123">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-123">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <span data-ttu-id="5a1bd-124">描述這個方法。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-124">Describes this method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5a1bd-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="5a1bd-125">Related Sections</span></span>  
 [<span data-ttu-id="5a1bd-126">操作說明：建立繪圖的圖形物件</span><span class="sxs-lookup"><span data-stu-id="5a1bd-126">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 <span data-ttu-id="5a1bd-127">導入了[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]從 Visual Studio 中的檢視方塊並提供連結的圖形功能的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-127">Introduces [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] graphics functionality from a Visual Studio perspective and gives links to more information.</span></span>  
  
 [<span data-ttu-id="5a1bd-128">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="5a1bd-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="5a1bd-129">描述您可以編寫自訂控制項類型。</span><span class="sxs-lookup"><span data-stu-id="5a1bd-129">Describes the kinds of custom controls you can author.</span></span>
