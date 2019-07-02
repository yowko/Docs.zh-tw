---
title: 自訂控制項繪製和轉譯
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: 14abac5678bfffa3cdb61307fd3cb54681c82a99
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506092"
---
# <a name="custom-control-painting-and-rendering"></a><span data-ttu-id="4d674-102">自訂控制項繪製和轉譯</span><span class="sxs-lookup"><span data-stu-id="4d674-102">Custom Control Painting and Rendering</span></span>
<span data-ttu-id="4d674-103">自訂繪製的控制項是其中一個輕鬆使用.NET framework 的許多複雜工作。</span><span class="sxs-lookup"><span data-stu-id="4d674-103">Custom painting of controls is one of the many complicated tasks made easy by the .NET Framework.</span></span> <span data-ttu-id="4d674-104">當撰寫自訂控制項，您會有相關控制項的圖形化外觀的許多選項。</span><span class="sxs-lookup"><span data-stu-id="4d674-104">When authoring a custom control, you have many options regarding your control's graphical appearance.</span></span> <span data-ttu-id="4d674-105">如果您撰寫控制項是繼承自`Control`，您必須提供可讓您的控制項來呈現其圖形表示法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d674-105">If you are authoring a control that inherits from the `Control`, you must provide code that allows your control to render its graphical representation.</span></span> <span data-ttu-id="4d674-106">如果您要建立使用者控制項繼承自`UserControl`，繼承或從其中一個 Windows Form 控制項，您可能會覆寫標準的圖形化表示法，並提供您自己的圖形程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d674-106">If you are creating a user control by inheriting from the `UserControl`, or are inheriting from one of the Windows Forms controls, you may override the standard graphical representation and provide your own graphics code.</span></span> <span data-ttu-id="4d674-107">如果您想要提供的構成控制項的自訂轉譯`UserControl`您撰寫時，選項變得較少，但仍然允許廣泛的圖形化的能力，為您的控制項和應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d674-107">If you want to provide custom rendering for the constituent controls of a `UserControl` you are authoring, your options become more limited, but still allow a wide range of graphical possibilities for your controls and applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4d674-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="4d674-108">In This Section</span></span>  
 [<span data-ttu-id="4d674-109">呈現 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="4d674-109">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)  
 <span data-ttu-id="4d674-110">示範如何撰寫程式顯示控制項的邏輯。</span><span class="sxs-lookup"><span data-stu-id="4d674-110">Shows how to program the logic that displays a control.</span></span>  
  
 [<span data-ttu-id="4d674-111">使用者自訂描繪控制項</span><span class="sxs-lookup"><span data-stu-id="4d674-111">User-Drawn Controls</span></span>](user-drawn-controls.md)  
 <span data-ttu-id="4d674-112">提供撰寫和覆寫控制項的轉譯程式碼所需的步驟的概觀。</span><span class="sxs-lookup"><span data-stu-id="4d674-112">Gives an overview of the steps involved in writing and overriding rendering code for your control.</span></span>  
  
 [<span data-ttu-id="4d674-113">組成控制項</span><span class="sxs-lookup"><span data-stu-id="4d674-113">Constituent Controls</span></span>](constituent-controls.md)  
 <span data-ttu-id="4d674-114">描述如何在您的使用者控制項和表單中實作的組成控制項的自訂轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d674-114">Describes how to implement custom rendering code for constituent controls in your user controls and forms.</span></span>  
  
 [<span data-ttu-id="4d674-115">如何：在執行階段隱藏控制項</span><span class="sxs-lookup"><span data-stu-id="4d674-115">How to: Make Your Control Invisible at Run Time</span></span>](how-to-make-your-control-invisible-at-run-time.md)  
 <span data-ttu-id="4d674-116">示範如何使用<xref:System.Windows.Forms.Control.Visible%2A>隱藏和顯示控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="4d674-116">Shows how to use the <xref:System.Windows.Forms.Control.Visible%2A> property to hide and show a control.</span></span>  
  
 [<span data-ttu-id="4d674-117">如何：為控制項提供透明背景</span><span class="sxs-lookup"><span data-stu-id="4d674-117">How to: Give Your Control a Transparent Background</span></span>](how-to-give-your-control-a-transparent-background.md)  
 <span data-ttu-id="4d674-118">示範如何使用<xref:System.Windows.Forms.Control.SetStyle%2A>方法用來建立不透明、 透明或部分透明的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="4d674-118">Shows how to use the <xref:System.Windows.Forms.Control.SetStyle%2A> method to create a background color that is opaque, transparent, or partially transparent.</span></span>  
  
 [<span data-ttu-id="4d674-119">使用視覺化樣式呈現控制項</span><span class="sxs-lookup"><span data-stu-id="4d674-119">Rendering Controls with Visual Styles</span></span>](rendering-controls-with-visual-styles.md)  
 <span data-ttu-id="4d674-120">示範如何呈現在支援的作業系統中使用視覺化樣式的控制項。</span><span class="sxs-lookup"><span data-stu-id="4d674-120">Shows how to render controls using visual styles in operating systems that support them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4d674-121">參考資料</span><span class="sxs-lookup"><span data-stu-id="4d674-121">Reference</span></span>  
 <xref:System.Windows.Forms.Control>  
 <span data-ttu-id="4d674-122">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="4d674-122">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="4d674-123">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="4d674-123">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <span data-ttu-id="4d674-124">描述這個方法。</span><span class="sxs-lookup"><span data-stu-id="4d674-124">Describes this method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4d674-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="4d674-125">Related Sections</span></span>  
 [<span data-ttu-id="4d674-126">如何：建立繪圖的圖形物件</span><span class="sxs-lookup"><span data-stu-id="4d674-126">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)  
 <span data-ttu-id="4d674-127">介紹 GDI + 繪圖功能從 Visual Studio 的觀點來看，並提供更多資訊的連結。</span><span class="sxs-lookup"><span data-stu-id="4d674-127">Introduces GDI+ graphics functionality from a Visual Studio perspective and gives links to more information.</span></span>  
  
 [<span data-ttu-id="4d674-128">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="4d674-128">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="4d674-129">描述您可以撰寫自訂控制項的類型。</span><span class="sxs-lookup"><span data-stu-id="4d674-129">Describes the kinds of custom controls you can author.</span></span>
