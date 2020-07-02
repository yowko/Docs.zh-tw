---
title: 開發自訂控制項
description: 瞭解 Windows Form 控制項。 具體而言，您將瞭解如何結合現有的控制項、擴充現有的控制項，以及撰寫您自己的自訂控制項。
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 12013496c9650489fdd7512206317000fc0ec78c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618372"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="4f661-104">使用 .NET Framework 開發自訂的 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="4f661-104">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="4f661-105">Windows Form 控制項是可重複使用的元件，這些控制項可封裝使用者介面功能，並可用於用戶端 Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f661-105">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="4f661-106">Windows Form 不僅提供許多立即可用的控制項，也提供用以開發您自己的控制項的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="4f661-106">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="4f661-107">您可以結合現有的控制項、擴充現有的控制項，或撰寫您自己的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="4f661-107">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="4f661-108">本節提供背景資訊和範例，以協助您開發 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="4f661-108">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f661-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="4f661-109">In This Section</span></span>  
 [<span data-ttu-id="4f661-110">在 Windows Form 中使用控制項的概觀</span><span class="sxs-lookup"><span data-stu-id="4f661-110">Overview of Using Controls in Windows Forms</span></span>](overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="4f661-111">重點說明在 Windows Forms 應用程式中使用控制項的基本項目。</span><span class="sxs-lookup"><span data-stu-id="4f661-111">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="4f661-112">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="4f661-112">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="4f661-113">描述可以使用 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間撰寫之各種不同的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="4f661-113">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="4f661-114">Windows Forms 控制項開發的基本概念</span><span class="sxs-lookup"><span data-stu-id="4f661-114">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)  
 <span data-ttu-id="4f661-115">討論開發 Windows Form 控制項的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="4f661-115">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="4f661-116">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="4f661-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)  
 <span data-ttu-id="4f661-117">示範如何將屬性加入 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="4f661-117">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="4f661-118">Windows Form 控制項中的事件</span><span class="sxs-lookup"><span data-stu-id="4f661-118">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)  
 <span data-ttu-id="4f661-119">示範如何在 Windows Form 控制項中處理及定義事件。</span><span class="sxs-lookup"><span data-stu-id="4f661-119">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="4f661-120">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="4f661-120">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="4f661-121">描述可以套用至屬性 (Property) 或您的自訂控制項和元件之其他成員的屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="4f661-121">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="4f661-122">自訂控制項繪製和轉譯</span><span class="sxs-lookup"><span data-stu-id="4f661-122">Custom Control Painting and Rendering</span></span>](custom-control-painting-and-rendering.md)  
 <span data-ttu-id="4f661-123">示範如何自訂控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="4f661-123">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="4f661-124">Windows Forms 控制項中的配置</span><span class="sxs-lookup"><span data-stu-id="4f661-124">Layout in Windows Forms Controls</span></span>](layout-in-windows-forms-controls.md)  
 <span data-ttu-id="4f661-125">示範如何為控制項和表單建立複雜的配置。</span><span class="sxs-lookup"><span data-stu-id="4f661-125">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="4f661-126">在 Windows Form 控制項中的多執行緒</span><span class="sxs-lookup"><span data-stu-id="4f661-126">Multithreading in Windows Forms Controls</span></span>](multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="4f661-127">示範如何實作多執行緒的控制項。</span><span class="sxs-lookup"><span data-stu-id="4f661-127">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4f661-128">參考</span><span class="sxs-lookup"><span data-stu-id="4f661-128">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="4f661-129">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="4f661-129">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="4f661-130">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="4f661-130">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4f661-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="4f661-131">Related Sections</span></span>  
 <span data-ttu-id="4f661-132">[元件的設計階段屬性](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="4f661-132">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="4f661-133">列出要套用至元件和控制項的中繼資料屬性，以便在設計階段於視覺設計工具中正確顯示這些屬性。</span><span class="sxs-lookup"><span data-stu-id="4f661-133">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="4f661-134">[擴充設計階段支援](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="4f661-134">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="4f661-135">描述如何實作類別，例如提供設計階段支援的編輯器和設計工具。</span><span class="sxs-lookup"><span data-stu-id="4f661-135">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 <span data-ttu-id="4f661-136">[如何：授權元件和控制項](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="4f661-136">[How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span></span>  
 <span data-ttu-id="4f661-137">描述如何在您的控制項或元件中實作授權。</span><span class="sxs-lookup"><span data-stu-id="4f661-137">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="4f661-138">另請參閱[在設計階段開發 Windows Forms 控制項](developing-windows-forms-controls-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="4f661-138">Also see [Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md).</span></span>
