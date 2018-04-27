---
title: 使用 WPF 控制項
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8225447e6c0daa7894d622616131febb6ac82b5
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="using-wpf-controls"></a><span data-ttu-id="125ad-102">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="125ad-102">Using WPF Controls</span></span>
<span data-ttu-id="125ad-103">您可以在 Windows form 應用程式中使用 Windows Presentation Foundation (WPF) 控制項。</span><span class="sxs-lookup"><span data-stu-id="125ad-103">You can use Windows Presentation Foundation (WPF) controls in your Windows Forms-based applications.</span></span> <span data-ttu-id="125ad-104">雖然這些是兩個不同的檢視技術，但是它們順暢的互通。</span><span class="sxs-lookup"><span data-stu-id="125ad-104">Although these are two different view technologies, they interoperate smoothly.</span></span>  
  
 <span data-ttu-id="125ad-105">Windows Form 設計工具提供視覺化設計環境來裝載 Windows Presentation Foundation 控制項。</span><span class="sxs-lookup"><span data-stu-id="125ad-105">The Windows Forms Designer provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="125ad-106">由名為特殊 Windows Form 控制項裝載 WPF 控制項<xref:System.Windows.Forms.Integration.ElementHost>。</span><span class="sxs-lookup"><span data-stu-id="125ad-106">A WPF control is hosted by a special Windows Forms control that is named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="125ad-107">這個控制項可讓 WPF 控制項加入表單的版面配置，並接收鍵盤和滑鼠的訊息。</span><span class="sxs-lookup"><span data-stu-id="125ad-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="125ad-108">您可以在設計階段排列<xref:System.Windows.Forms.Integration.ElementHost>控制就如同任何 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="125ad-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>  
  
 <span data-ttu-id="125ad-109">您也可以使用 Windows Form 控制項以 WPF 為基礎的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="125ad-109">You can also use Windows Forms controls in your WPF-based applications.</span></span> <span data-ttu-id="125ad-110">如需詳細資訊，請參閱[WPF 設計工具](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)。</span><span class="sxs-lookup"><span data-stu-id="125ad-110">For more information, see [WPF Designer](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="125ad-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="125ad-111">In This Section</span></span>  
 [<span data-ttu-id="125ad-112">操作說明：在設計階段複製和貼上 ElementHost 控制項</span><span class="sxs-lookup"><span data-stu-id="125ad-112">How to: Copy and Paste an ElementHost Control at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 <span data-ttu-id="125ad-113">示範如何複製 Windows Form 上的 Windows Presentation Foundation 控制項。</span><span class="sxs-lookup"><span data-stu-id="125ad-113">Shows how to copy a Windows Presentation Foundation control on a Windows Form.</span></span>  
  
 [<span data-ttu-id="125ad-114">逐步解說：在設計階段排列 Windows Forms 的 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="125ad-114">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="125ad-115">示範如何使用 Windows Form 的配置功能，例如錨定和對齊線，來排列 Windows Presentation Foundation 控制項。</span><span class="sxs-lookup"><span data-stu-id="125ad-115">Shows how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation controls.</span></span>  
  
 [<span data-ttu-id="125ad-116">逐步解說：在設計階段變更已裝載之 WPF 元素的屬性</span><span class="sxs-lookup"><span data-stu-id="125ad-116">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 <span data-ttu-id="125ad-117">顯示 Windows Form 設計工具之間的工作流程和[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]變更 WPF 控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="125ad-117">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] for changing properties on WPF controls.</span></span>  
  
 [<span data-ttu-id="125ad-118">逐步解說：在設計階段建立 Windows Forms 的新 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="125ad-118">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="125ad-119">示範如何建立使用 Windows Presentation Foundation 控制項在 Windows Form 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="125ad-119">Shows how to create a Windows Presentation Foundation control for use in your Windows Forms-based applications.</span></span>  
  
 [<span data-ttu-id="125ad-120">逐步解說：將 ElementHost 控制項複製並貼至另外的 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="125ad-120">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 <span data-ttu-id="125ad-121">示範如何在 Windows Presentation Foundation 控制項複製到另一個 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="125ad-121">Shows how to copy a Windows Presentation Foundation control from one Windows Form to another.</span></span>  
  
 [<span data-ttu-id="125ad-122">逐步解說：在設計階段指派 Windows Forms 的 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="125ad-122">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="125ad-123">顯示如何選取您想要顯示在表單上的 Windows Presentation Foundation 控制項類型。</span><span class="sxs-lookup"><span data-stu-id="125ad-123">Shows how to select the Windows Presentation Foundation control types you want to display on your form.</span></span>  
  
 [<span data-ttu-id="125ad-124">逐步解說：設定 WPF 內容的樣式</span><span class="sxs-lookup"><span data-stu-id="125ad-124">Walkthrough: Styling WPF Content</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 <span data-ttu-id="125ad-125">顯示 Windows Form 設計工具之間的工作流程和[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]將樣式套用至 Windows Presentation Foundation 控制項。</span><span class="sxs-lookup"><span data-stu-id="125ad-125">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] for applying styles to Windows Presentation Foundation controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="125ad-126">參考資料</span><span class="sxs-lookup"><span data-stu-id="125ad-126">Reference</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <span data-ttu-id="125ad-127">描述您可以在 Windows form 應用程式中使用主機的 Windows Presentation Foundation 控制項的類別。</span><span class="sxs-lookup"><span data-stu-id="125ad-127">Describes a class which you can use to host Windows Presentation Foundation controls in your Windows Forms-based applications.</span></span>  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 <span data-ttu-id="125ad-128">描述您可以在 Windows Presentation Foundation 應用程式中使用主機的 Windows Form 控制項的類別。</span><span class="sxs-lookup"><span data-stu-id="125ad-128">Describes a class which you can use to host Windows Forms controls in your Windows Presentation Foundation-based application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="125ad-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="125ad-129">Related Sections</span></span>  
 [<span data-ttu-id="125ad-130">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="125ad-130">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 <span data-ttu-id="125ad-131">描述 Windows Presentation Foundation 和 Windows Form 技術之間的互通性。</span><span class="sxs-lookup"><span data-stu-id="125ad-131">Describes interoperation between the Windows Presentation Foundation and Windows Forms technologies.</span></span>  
  
 [<span data-ttu-id="125ad-132">WPF 設計工具</span><span class="sxs-lookup"><span data-stu-id="125ad-132">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 <span data-ttu-id="125ad-133">描述如何設計 Visual Studio 中的 Windows Presentation Foundation 控制項。</span><span class="sxs-lookup"><span data-stu-id="125ad-133">Describes how to design Windows Presentation Foundation controls in Visual Studio.</span></span>
