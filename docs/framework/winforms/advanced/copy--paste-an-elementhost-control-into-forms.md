---
title: "逐步解說：將 ElementHost 控制項複製並貼至另外的 Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f98d3463adab9bace30610efbaf06dcade78f17
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a><span data-ttu-id="b05ab-102">逐步解說：將 ElementHost 控制項複製並貼至另外的 Windows Form</span><span class="sxs-lookup"><span data-stu-id="b05ab-102">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>
<span data-ttu-id="b05ab-103">本逐步解說示範如何將 Windows Presentation Foundation (WPF) 控制項從一個 Windows Form 複製到另一個 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="b05ab-103">This walkthrough shows you how to copy a Windows Presentation Foundation (WPF) control from one Windows Form to another.</span></span>  
  
 <span data-ttu-id="b05ab-104">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="b05ab-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="b05ab-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="b05ab-105">Create the project.</span></span>  
  
-   <span data-ttu-id="b05ab-106">複製 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="b05ab-106">Copy a WPF Control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b05ab-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="b05ab-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b05ab-108">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="b05ab-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b05ab-109">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="b05ab-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b05ab-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="b05ab-110">Prerequisites</span></span>  
 <span data-ttu-id="b05ab-111">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="b05ab-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="b05ab-112">.</span><span class="sxs-lookup"><span data-stu-id="b05ab-112">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="b05ab-113">建立專案</span><span class="sxs-lookup"><span data-stu-id="b05ab-113">Creating the Project</span></span>  
 <span data-ttu-id="b05ab-114">第一個步驟是建立 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="b05ab-114">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b05ab-115">裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="b05ab-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="b05ab-116">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="b05ab-116">To create the project</span></span>  
  
-   <span data-ttu-id="b05ab-117">建立新的 Windows Forms 應用程式專案在 Visual Basic 或 Visual C# 中名為`CopyElementHost`。</span><span class="sxs-lookup"><span data-stu-id="b05ab-117">Create a new Windows Forms Application project in Visual Basic or Visual C# named `CopyElementHost`.</span></span>  
  
## <a name="copying-a-wpf-control"></a><span data-ttu-id="b05ab-118">複製 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="b05ab-118">Copying a WPF Control</span></span>  
 <span data-ttu-id="b05ab-119">將 WPF 控制項加入專案之後，您可以將其複製到專案中的其他表單。</span><span class="sxs-lookup"><span data-stu-id="b05ab-119">After you add a WPF control to the project, you can copy it to other forms in the project.</span></span>  
  
#### <a name="to-copy-a-wpf-control"></a><span data-ttu-id="b05ab-120">複製 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="b05ab-120">To copy a WPF control</span></span>  
  
1.  <span data-ttu-id="b05ab-121">將新的 WPF <xref:System.Windows.Controls.UserControl> 專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="b05ab-121">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="b05ab-122">使用控制項類型的預設名稱 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="b05ab-122">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="b05ab-123">如需詳細資訊，請參閱[逐步解說： 建立的新 WPF 內容在設計階段的 Windows Form 上](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="b05ab-123">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="b05ab-124">建置專案。</span><span class="sxs-lookup"><span data-stu-id="b05ab-124">Build the project.</span></span>  
  
3.  <span data-ttu-id="b05ab-125">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="b05ab-125">Open `Form1` in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="b05ab-126">從**工具箱**，拖曳的執行個體`UserControl1`拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="b05ab-126">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="b05ab-127">`UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="b05ab-127">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
5.  <span data-ttu-id="b05ab-128">在選取 `elementHost1` 時，按 CTRL+C 將其複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="b05ab-128">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
6.  <span data-ttu-id="b05ab-129">將新的 Windows Form 加入專案。</span><span class="sxs-lookup"><span data-stu-id="b05ab-129">Add a new Windows Form to the project.</span></span> <span data-ttu-id="b05ab-130">使用表單類型的預設名稱 `Form2`。</span><span class="sxs-lookup"><span data-stu-id="b05ab-130">Use the default name for the form type, `Form2`.</span></span>  
  
7.  <span data-ttu-id="b05ab-131">當 `Form2` 在 Windows Form 設計工具中開啟時，按 CTRL+V 將 `elementHost1` 的複本貼到表單上。</span><span class="sxs-lookup"><span data-stu-id="b05ab-131">With `Form2` open in the Windows Forms Designer, press CTRL+V to paste a copy of `elementHost1` onto the form.</span></span>  
  
     <span data-ttu-id="b05ab-132">由於複製的控制項是 `Form2` 類別的私用欄位，因此該控制項的名稱也是 `elementHost1`。</span><span class="sxs-lookup"><span data-stu-id="b05ab-132">The copied control is also named `elementHost1`, because it is a private field of the `Form2` class.</span></span> <span data-ttu-id="b05ab-133">這樣並不會與 `Form1` 類別中的 `elementHost1` 產生名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="b05ab-133">There is no name collision with the `elementHost1` in the `Form1` class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b05ab-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="b05ab-134">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="b05ab-135">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="b05ab-135">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="b05ab-136">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="b05ab-136">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="b05ab-137">WPF 設計工具</span><span class="sxs-lookup"><span data-stu-id="b05ab-137">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
