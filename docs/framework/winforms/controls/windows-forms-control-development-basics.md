---
title: "Windows Form 控制項開發的基本概念"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bcf06f4dc0d8c70ae85d5add5a2fee078238d5e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-control-development-basics"></a><span data-ttu-id="2a755-102">Windows Form 控制項開發的基本概念</span><span class="sxs-lookup"><span data-stu-id="2a755-102">Windows Forms Control Development Basics</span></span>
<span data-ttu-id="2a755-103">Windows Form 控制項是一個類別，是直接或間接衍生自<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="2a755-103">A Windows Forms control is a class that derives directly or indirectly from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2a755-104">下列清單描述開發 Windows Form 控制項的常見案例：</span><span class="sxs-lookup"><span data-stu-id="2a755-104">The following list describes common scenarios for developing Windows Forms controls:</span></span>  
  
-   <span data-ttu-id="2a755-105">若要撰寫複合控制項結合現有的控制。</span><span class="sxs-lookup"><span data-stu-id="2a755-105">Combining existing controls to author a composite control.</span></span>  
  
     <span data-ttu-id="2a755-106">複合控制項封裝可以重複使用，做為控制項的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="2a755-106">Composite controls encapsulate a user interface that can be reused as a control.</span></span> <span data-ttu-id="2a755-107">複合控制項的範例是包含文字方塊和重設按鈕控制項。</span><span class="sxs-lookup"><span data-stu-id="2a755-107">An example of a composite control is a control that consists of a text box and a reset button.</span></span> <span data-ttu-id="2a755-108">視覺化設計工具提供豐富的支援，如建立複合控制項。</span><span class="sxs-lookup"><span data-stu-id="2a755-108">Visual designers offer rich support for creating composite controls.</span></span> <span data-ttu-id="2a755-109">若要撰寫複合控制項，衍生自<xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="2a755-109">To author a composite control, derive from <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2a755-110">基底類別<xref:System.Windows.Forms.UserControl>提供鍵盤路徑的子控制項，並讓做為群組的子控制項。</span><span class="sxs-lookup"><span data-stu-id="2a755-110">The base class <xref:System.Windows.Forms.UserControl> provides keyboard routing for child controls and enables child controls to work as a group.</span></span> <span data-ttu-id="2a755-111">如需詳細資訊，請參閱[開發複合 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)。</span><span class="sxs-lookup"><span data-stu-id="2a755-111">For more information, see [Developing a Composite Windows Forms Control](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).</span></span>  
  
-   <span data-ttu-id="2a755-112">擴充現有控制項進行自訂，或加入至其功能。</span><span class="sxs-lookup"><span data-stu-id="2a755-112">Extending an existing control to customize it or to add to its functionality.</span></span>  
  
     <span data-ttu-id="2a755-113">無法變更其色彩的按鈕和按鈕有額外的屬性，以追蹤已按下的次數會擴充控制項的範例。</span><span class="sxs-lookup"><span data-stu-id="2a755-113">A button whose color cannot be changed and a button that has an additional property that tracks how many times it has been clicked are examples of extended controls.</span></span> <span data-ttu-id="2a755-114">您可以自訂任何 Windows Form 控制項衍生自它和覆寫或新增屬性、 方法和事件。</span><span class="sxs-lookup"><span data-stu-id="2a755-114">You can customize any Windows Forms control by deriving from it and overriding or adding properties, methods, and events.</span></span>  
  
-   <span data-ttu-id="2a755-115">撰寫不結合或擴充現有控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="2a755-115">Authoring a control that does not combine or extend existing controls.</span></span>  
  
     <span data-ttu-id="2a755-116">在此案例中，衍生您的控制項的基底類別從<xref:System.Windows.Forms.Control>。</span><span class="sxs-lookup"><span data-stu-id="2a755-116">In this scenario, derive your control from the base class <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="2a755-117">您可以新增，以及覆寫屬性、 方法和事件的基底類別。</span><span class="sxs-lookup"><span data-stu-id="2a755-117">You can add as well as override properties, methods, and events of the base class.</span></span> <span data-ttu-id="2a755-118">若要開始使用，請參閱[How to： 開發簡單的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)。</span><span class="sxs-lookup"><span data-stu-id="2a755-118">To get started, see [How to: Develop a Simple Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).</span></span>  
  
 <span data-ttu-id="2a755-119">Windows Form 控制項的基底類別<xref:System.Windows.Forms.Control>，提供所需的用戶端 Windows 架構應用程式中的視覺顯示。</span><span class="sxs-lookup"><span data-stu-id="2a755-119">The base class for Windows Forms controls, <xref:System.Windows.Forms.Control>, provides the plumbing required for visual display in client-side Windows-based applications.</span></span> <span data-ttu-id="2a755-120"><xref:System.Windows.Forms.Control>提供的視窗控制代碼，會處理訊息路由，並可提供滑鼠和鍵盤事件，以及許多其他的使用者介面事件。</span><span class="sxs-lookup"><span data-stu-id="2a755-120"><xref:System.Windows.Forms.Control> provides a window handle, handles message routing, and provides mouse and keyboard events as well as many other user interface events.</span></span> <span data-ttu-id="2a755-121">它提供進階的版面配置，而且有特定的視覺顯示 屬性，例如<xref:System.Windows.Forms.Control.ForeColor%2A>， <xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.Height%2A>， <xref:System.Windows.Forms.Control.Width%2A>，及其他等等。</span><span class="sxs-lookup"><span data-stu-id="2a755-121">It provides advanced layout and has properties specific to visual display, such as <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, and many others.</span></span> <span data-ttu-id="2a755-122">此外，它會提供安全性，執行緒處理的支援，以及 ActiveX 控制項與互通性。</span><span class="sxs-lookup"><span data-stu-id="2a755-122">Additionally, it provides security, threading support, and interoperability with ActiveX controls.</span></span> <span data-ttu-id="2a755-123">因為基底類別提供了非常多的基礎結構，所以開發您自己的 Windows Forms 控制項相對容易。</span><span class="sxs-lookup"><span data-stu-id="2a755-123">Because so much of the infrastructure is provided by the base class, it is relatively easy to develop your own Windows Forms controls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a755-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a755-124">See Also</span></span>  
 [<span data-ttu-id="2a755-125">操作說明：開發簡單的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="2a755-125">How to: Develop a Simple Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [<span data-ttu-id="2a755-126">開發複合 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="2a755-126">Developing a Composite Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [<span data-ttu-id="2a755-127">操作說明：建立顯示進度的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="2a755-127">How to: Create a Windows Forms Control That Shows Progress</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)  
 [<span data-ttu-id="2a755-128">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="2a755-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
