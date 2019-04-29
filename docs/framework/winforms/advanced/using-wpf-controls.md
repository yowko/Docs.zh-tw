---
title: 使用 WPF 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: 24b88e456628c5a0bdc3cded60b0e52a92057851
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747611"
---
# <a name="using-wpf-controls"></a><span data-ttu-id="ea6e0-102">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="ea6e0-102">Using WPF Controls</span></span>
<span data-ttu-id="ea6e0-103">您可以在 Windows form 應用程式中使用 Windows Presentation Foundation (WPF) 控制項。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-103">You can use Windows Presentation Foundation (WPF) controls in your Windows Forms-based applications.</span></span> <span data-ttu-id="ea6e0-104">雖然這些都是兩個不同的檢視技術，它們順暢的互通。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-104">Although these are two different view technologies, they interoperate smoothly.</span></span>  
  
 <span data-ttu-id="ea6e0-105">Windows Form 設計工具提供視覺化設計環境來裝載 Windows Presentation Foundation 控制項。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-105">The Windows Forms Designer provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="ea6e0-106">由特殊的 Windows Form 控制項是名為裝載 WPF 控制項<xref:System.Windows.Forms.Integration.ElementHost>。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-106">A WPF control is hosted by a special Windows Forms control that is named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="ea6e0-107">這個控制項可讓 WPF 控制項加入表單的版面配置，並接收鍵盤和滑鼠的訊息。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="ea6e0-108">您可以在設計階段排列<xref:System.Windows.Forms.Integration.ElementHost>控制就如同任何 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>  
  
 <span data-ttu-id="ea6e0-109">您也可以在您以 WPF 為基礎的應用程式中使用 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-109">You can also use Windows Forms controls in your WPF-based applications.</span></span> <span data-ttu-id="ea6e0-110">如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-110">For more information, see [Design XAML in Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea6e0-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="ea6e0-111">In This Section</span></span>  
 [<span data-ttu-id="ea6e0-112">如何：複製並貼上 ElementHost 控制項在設計階段</span><span class="sxs-lookup"><span data-stu-id="ea6e0-112">How to: Copy and Paste an ElementHost Control at Design Time</span></span>](how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 <span data-ttu-id="ea6e0-113">示範如何複製 Windows Form 上的 Windows Presentation Foundation 控制項。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-113">Shows how to copy a Windows Presentation Foundation control on a Windows Form.</span></span>  
  
 [<span data-ttu-id="ea6e0-114">逐步解說：在設計階段排列 Windows Form 的 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="ea6e0-114">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>](walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="ea6e0-115">示範如何使用 Windows Form 的配置功能，例如錨定和對齊線，來排列 Windows Presentation Foundation 控制項。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-115">Shows how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation controls.</span></span>
  
 [<span data-ttu-id="ea6e0-116">逐步解說：在設計階段建立 Windows Form 上的新 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="ea6e0-116">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="ea6e0-117">示範如何建立 Windows Presentation Foundation 控制項，以便在 Windows form 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-117">Shows how to create a Windows Presentation Foundation control for use in your Windows Forms-based applications.</span></span>
  
 [<span data-ttu-id="ea6e0-118">逐步解說：在設計階段指派 Windows Forms 的 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="ea6e0-118">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>](walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="ea6e0-119">顯示如何選取您想要在表單上顯示的 Windows Presentation Foundation 控制項類型。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-119">Shows how to select the Windows Presentation Foundation control types you want to display on your form.</span></span>  
  
 [<span data-ttu-id="ea6e0-120">逐步解說：設定 WPF 內容的樣式</span><span class="sxs-lookup"><span data-stu-id="ea6e0-120">Walkthrough: Styling WPF Content</span></span>](walkthrough-styling-wpf-content.md)  
 <span data-ttu-id="ea6e0-121">顯示 Windows Form 設計工具之間的工作流程和[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]將樣式套用至 Windows Presentation Foundation 控制項。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-121">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] for applying styles to Windows Presentation Foundation controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ea6e0-122">參考資料</span><span class="sxs-lookup"><span data-stu-id="ea6e0-122">Reference</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <span data-ttu-id="ea6e0-123">描述您可以在 Windows form 應用程式中使用來裝載 Windows Presentation Foundation 控制項的類別。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-123">Describes a class which you can use to host Windows Presentation Foundation controls in your Windows Forms-based applications.</span></span>  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 <span data-ttu-id="ea6e0-124">描述您可以在 Windows Presentation Foundation 架構應用程式中使用來裝載 Windows Forms 控制項的類別。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-124">Describes a class which you can use to host Windows Forms controls in your Windows Presentation Foundation-based application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ea6e0-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="ea6e0-125">Related Sections</span></span>  
 [<span data-ttu-id="ea6e0-126">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="ea6e0-126">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)  
 <span data-ttu-id="ea6e0-127">描述 Windows Presentation Foundation 和 Windows Form 技術之間的互通性。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-127">Describes interoperation between the Windows Presentation Foundation and Windows Forms technologies.</span></span>  
  
 [<span data-ttu-id="ea6e0-128">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="ea6e0-128">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 <span data-ttu-id="ea6e0-129">描述如何設計 Visual Studio 中的 Windows Presentation Foundation 控制項。</span><span class="sxs-lookup"><span data-stu-id="ea6e0-129">Describes how to design Windows Presentation Foundation controls in Visual Studio.</span></span>
