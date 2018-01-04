---
title: "使用 .NET Framework 開發自訂的 Windows Form 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2f15dc4bb3bd4a6d1163823509f0f2c2bf2c11a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="47cb0-102">使用 .NET Framework 開發自訂的 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="47cb0-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="47cb0-103">Windows Form 控制項是可重複使用的元件，這些控制項可封裝使用者介面功能，並可用於用戶端 Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="47cb0-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="47cb0-104">Windows Form 不僅提供許多立即可用的控制項，也提供用以開發您自己的控制項的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="47cb0-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="47cb0-105">您可以結合現有的控制項、擴充現有的控制項，或撰寫您自己的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="47cb0-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="47cb0-106">本節提供背景資訊和範例，以協助您開發 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="47cb0-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47cb0-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="47cb0-107">In This Section</span></span>  
 [<span data-ttu-id="47cb0-108">在 Windows Forms 中使用控制項的概觀</span><span class="sxs-lookup"><span data-stu-id="47cb0-108">Overview of Using Controls in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="47cb0-109">重點說明在 Windows Forms 應用程式中使用控制項的基本項目。</span><span class="sxs-lookup"><span data-stu-id="47cb0-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="47cb0-110">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="47cb0-110">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="47cb0-111">描述可以使用 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間撰寫之各種不同的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="47cb0-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="47cb0-112">Windows Forms 控制項開發的基本概念</span><span class="sxs-lookup"><span data-stu-id="47cb0-112">Windows Forms Control Development Basics</span></span>](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)  
 <span data-ttu-id="47cb0-113">討論開發 Windows Form 控制項的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="47cb0-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="47cb0-114">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="47cb0-114">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 <span data-ttu-id="47cb0-115">示範如何將屬性加入 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="47cb0-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="47cb0-116">Windows Forms 控制項中的事件</span><span class="sxs-lookup"><span data-stu-id="47cb0-116">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 <span data-ttu-id="47cb0-117">示範如何在 Windows Form 控制項中處理及定義事件。</span><span class="sxs-lookup"><span data-stu-id="47cb0-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="47cb0-118">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="47cb0-118">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="47cb0-119">描述可以套用至屬性 (Property) 或您的自訂控制項和元件之其他成員的屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="47cb0-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="47cb0-120">自訂控制項繪製和轉譯</span><span class="sxs-lookup"><span data-stu-id="47cb0-120">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="47cb0-121">示範如何自訂控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="47cb0-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="47cb0-122">Windows Forms 控制項中的配置</span><span class="sxs-lookup"><span data-stu-id="47cb0-122">Layout in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/layout-in-windows-forms-controls.md)  
 <span data-ttu-id="47cb0-123">示範如何為控制項和表單建立複雜的配置。</span><span class="sxs-lookup"><span data-stu-id="47cb0-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="47cb0-124">Windows Forms 控制項中的多執行緒</span><span class="sxs-lookup"><span data-stu-id="47cb0-124">Multithreading in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="47cb0-125">示範如何實作多執行緒的控制項。</span><span class="sxs-lookup"><span data-stu-id="47cb0-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="47cb0-126">參考資料</span><span class="sxs-lookup"><span data-stu-id="47cb0-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="47cb0-127">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="47cb0-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="47cb0-128">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="47cb0-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="47cb0-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="47cb0-129">Related Sections</span></span>  
 [<span data-ttu-id="47cb0-130">元件的設計階段屬性</span><span class="sxs-lookup"><span data-stu-id="47cb0-130">Design-Time Attributes for Components</span></span>](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="47cb0-131">列出要套用至元件和控制項的中繼資料屬性，以便在設計階段於視覺設計工具中正確顯示這些屬性。</span><span class="sxs-lookup"><span data-stu-id="47cb0-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="47cb0-132">擴充設計階段支援</span><span class="sxs-lookup"><span data-stu-id="47cb0-132">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="47cb0-133">描述如何實作類別，例如提供設計階段支援的編輯器和設計工具。</span><span class="sxs-lookup"><span data-stu-id="47cb0-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 [<span data-ttu-id="47cb0-134">如何：授權元件和控制項</span><span class="sxs-lookup"><span data-stu-id="47cb0-134">How to: License Components and Controls</span></span>](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57)  
 <span data-ttu-id="47cb0-135">描述如何在您的控制項或元件中實作授權。</span><span class="sxs-lookup"><span data-stu-id="47cb0-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="47cb0-136">另請參閱[在設計階段開發 Windows Forms 控制項](http://msdn.microsoft.com/library/w29y3h59\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="47cb0-136">Also see [Developing Windows Forms Controls at Design Time](http://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span></span>
