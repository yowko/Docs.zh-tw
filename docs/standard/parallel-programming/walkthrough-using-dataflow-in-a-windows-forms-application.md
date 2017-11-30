---
title: "逐步解說：在 Windows Forms 應用程式中使用資料流程"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2775cc99020fd99d6e7d79cdf3e1ffcc3219146
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a><span data-ttu-id="33b33-102">逐步解說：在 Windows Forms 應用程式中使用資料流程</span><span class="sxs-lookup"><span data-stu-id="33b33-102">Walkthrough: Using Dataflow in a Windows Forms Application</span></span>
<span data-ttu-id="33b33-103">本文鍵示範如何建立資料流程區塊網路，其可以在 Windows Forms 應用程式中執行映像處理。</span><span class="sxs-lookup"><span data-stu-id="33b33-103">This document demonstrates how to create a network of dataflow blocks that perform image processing in a Windows Forms application.</span></span>  
  
 <span data-ttu-id="33b33-104">這個範例會從指定的資料夾載入映像檔案、建立複合映像，以及顯示結果。</span><span class="sxs-lookup"><span data-stu-id="33b33-104">This example loads image files from the specified folder, creates a composite image, and displays the result.</span></span> <span data-ttu-id="33b33-105">這個範例會使用資料流程模型，透過網路路由映像。</span><span class="sxs-lookup"><span data-stu-id="33b33-105">The example uses the dataflow model to route images through the network.</span></span> <span data-ttu-id="33b33-106">在資料流程模型中，程式的獨立元件會透過傳送訊息，彼此進行通訊。</span><span class="sxs-lookup"><span data-stu-id="33b33-106">In the dataflow model, independent components of a program communicate with one another by sending messages.</span></span> <span data-ttu-id="33b33-107">當元件收到訊息時，它會執行某些動作，然後將結果傳遞給另一個元件。</span><span class="sxs-lookup"><span data-stu-id="33b33-107">When a component receives a message, it performs some action and then passes the result to another component.</span></span> <span data-ttu-id="33b33-108">比較資料流程模型與控制流程模型，在其中應用程式會使用控制項結構，例如，條件陳述式、迴圈等等，來控制程式中作業的順序。</span><span class="sxs-lookup"><span data-stu-id="33b33-108">Compare this with the control flow model, in which an application uses control structures, for example, conditional statements, loops, and so on, to control the order of operations in a program.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="33b33-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="33b33-109">Prerequisites</span></span>  
 <span data-ttu-id="33b33-110">在開始進行這個逐步解說之前，請先閱讀[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)。</span><span class="sxs-lookup"><span data-stu-id="33b33-110">Read [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) before you start this walkthrough.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="33b33-111">TPL 資料流程程式庫 (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 命名空間) 並未隨附於 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="33b33-111">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="33b33-112">若要安裝<xref:System.Threading.Tasks.Dataflow>命名空間中，開啟您的專案中[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]，選擇**管理 NuGet 封裝**從 [專案] 功能表中，並在搜尋線上`Microsoft.Tpl.Dataflow`封裝。</span><span class="sxs-lookup"><span data-stu-id="33b33-112">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
 
  
## <a name="sections"></a><span data-ttu-id="33b33-113">章節</span><span class="sxs-lookup"><span data-stu-id="33b33-113">Sections</span></span>  
 <span data-ttu-id="33b33-114">本逐步解說包含下列各節：</span><span class="sxs-lookup"><span data-stu-id="33b33-114">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="33b33-115">建立 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="33b33-115">Creating the Windows Forms Application</span></span>](#winforms)  
  
-   [<span data-ttu-id="33b33-116">建立資料流程網路</span><span class="sxs-lookup"><span data-stu-id="33b33-116">Creating the Dataflow Network</span></span>](#network)  
  
-   [<span data-ttu-id="33b33-117">連接資料流程網路與使用者介面</span><span class="sxs-lookup"><span data-stu-id="33b33-117">Connecting the Dataflow Network to the User Interface</span></span>](#ui)  
  
-   [<span data-ttu-id="33b33-118">完整範例</span><span class="sxs-lookup"><span data-stu-id="33b33-118">The Complete Example</span></span>](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a><span data-ttu-id="33b33-119">建立 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="33b33-119">Creating the Windows Forms Application</span></span>  
 <span data-ttu-id="33b33-120">本節描述如何建立基本 Windows Forms 應用程式，並且將控制項新增至主要表單。</span><span class="sxs-lookup"><span data-stu-id="33b33-120">This section describes how to create the basic Windows Forms application and add controls to the main form.</span></span>  
  
#### <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="33b33-121">若要建立 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="33b33-121">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="33b33-122">在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]中，建立 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 或 Visual Basic 的 [Windows Forms 應用程式] 專案。</span><span class="sxs-lookup"><span data-stu-id="33b33-122">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], create a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="33b33-123">在本文件中，專案命名為 `CompositeImages`。</span><span class="sxs-lookup"><span data-stu-id="33b33-123">In this document, the project is named `CompositeImages`.</span></span>  
  
2.  <span data-ttu-id="33b33-124">在主要表單 Form1.cs 的表單設計工具 (為 Form1.vb [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)])，新增<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="33b33-124">On the form designer for the main form, Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3.  <span data-ttu-id="33b33-125">新增<xref:System.Windows.Forms.ToolStripButton>控制權傳輸至<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="33b33-125">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="33b33-126">設定<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>屬性<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>和<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性**選擇資料夾**。</span><span class="sxs-lookup"><span data-stu-id="33b33-126">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Choose Folder**.</span></span>  
  
4.  <span data-ttu-id="33b33-127">新增第二個<xref:System.Windows.Forms.ToolStripButton>控制權傳輸至<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="33b33-127">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="33b33-128">設定<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>屬性<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>、<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性**取消**，而<xref:System.Windows.Forms.ToolStripItem.Enabled%2A>屬性`False`。</span><span class="sxs-lookup"><span data-stu-id="33b33-128">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5.  <span data-ttu-id="33b33-129">新增<xref:System.Windows.Forms.PictureBox>加入主要表單的物件。</span><span class="sxs-lookup"><span data-stu-id="33b33-129">Add a <xref:System.Windows.Forms.PictureBox> object to the main form.</span></span> <span data-ttu-id="33b33-130">將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="33b33-130">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a><span data-ttu-id="33b33-131">建立資料流程網路</span><span class="sxs-lookup"><span data-stu-id="33b33-131">Creating the Dataflow Network</span></span>  
 <span data-ttu-id="33b33-132">本節描述如何建立會執行映像處理的資料流程網路。</span><span class="sxs-lookup"><span data-stu-id="33b33-132">This section describes how to create the dataflow network that performs image processing.</span></span>  
  
#### <a name="to-create-the-dataflow-network"></a><span data-ttu-id="33b33-133">若要建立資料流程網路</span><span class="sxs-lookup"><span data-stu-id="33b33-133">To Create the Dataflow Network</span></span>  
  
1.  <span data-ttu-id="33b33-134">將 System.Threading.Tasks.Dataflow.dll 參考新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="33b33-134">Add a reference to System.Threading.Tasks.Dataflow.dll to your project.</span></span>  
  
2.  <span data-ttu-id="33b33-135">確定 Form1.cs (在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中為 Form1.vb) 包含下列 `using` (在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中為 `Using`) 陳述式：</span><span class="sxs-lookup"><span data-stu-id="33b33-135">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` (`Using` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) statements:</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3.  <span data-ttu-id="33b33-136">將下列資料成員新增至 `Form1` 類別：</span><span class="sxs-lookup"><span data-stu-id="33b33-136">Add the following data members to the `Form1` class:</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4.  <span data-ttu-id="33b33-137">將下列 `CreateImageProcessingNetwork` 方法新增至 `Form1` 類別。</span><span class="sxs-lookup"><span data-stu-id="33b33-137">Add the following method, `CreateImageProcessingNetwork`, to the `Form1` class.</span></span> <span data-ttu-id="33b33-138">這個方法會建立映像處理網路。</span><span class="sxs-lookup"><span data-stu-id="33b33-138">This method creates the image processing network.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5.  <span data-ttu-id="33b33-139">實作 `LoadBitmaps` 方法。</span><span class="sxs-lookup"><span data-stu-id="33b33-139">Implement the `LoadBitmaps` method.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6.  <span data-ttu-id="33b33-140">實作 `CreateCompositeBitmap` 方法。</span><span class="sxs-lookup"><span data-stu-id="33b33-140">Implement the `CreateCompositeBitmap` method.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  <span data-ttu-id="33b33-141">C# 版本的`CreateCompositeBitmap`方法會使用指標，啟用有效處理<xref:System.Drawing.Bitmap?displayProperty=nameWithType>物件。</span><span class="sxs-lookup"><span data-stu-id="33b33-141">The C# version of the `CreateCompositeBitmap` method uses pointers to enable efficient processing of the <xref:System.Drawing.Bitmap?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="33b33-142">因此，您必須在專案中啟用 [容許 Unsafe 程式碼] 選項，以便使用 [unsafe](~/docs/csharp/language-reference/keywords/unsafe.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="33b33-142">Therefore, you must enable the **Allow unsafe code** option in your project in order to use the [unsafe](~/docs/csharp/language-reference/keywords/unsafe.md) keyword.</span></span> <span data-ttu-id="33b33-143">如需有關如何啟用 unsafe 程式碼中的[!INCLUDE[csprcs](../../../includes/csprcs-md.md)]專案，請參閱 [建置 頁面，專案設計工具 (C#)] https://msdn.microsoft.com/library/kb4wyys2)。</span><span class="sxs-lookup"><span data-stu-id="33b33-143">For more information about how to enable unsafe code in a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] project, see [Build Page, Project Designer (C#)]https://msdn.microsoft.com/library/kb4wyys2).</span></span>  
  
 <span data-ttu-id="33b33-144">下表描述網路的成員。</span><span class="sxs-lookup"><span data-stu-id="33b33-144">The following table describes the members of the network.</span></span>  
  
|<span data-ttu-id="33b33-145">成員</span><span class="sxs-lookup"><span data-stu-id="33b33-145">Member</span></span>|<span data-ttu-id="33b33-146">類型</span><span class="sxs-lookup"><span data-stu-id="33b33-146">Type</span></span>|<span data-ttu-id="33b33-147">說明</span><span class="sxs-lookup"><span data-stu-id="33b33-147">Description</span></span>|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="33b33-148">接受資料夾路徑，做為輸入，然後產生的集合<xref:System.Drawing.Bitmap>做為輸出的物件。</span><span class="sxs-lookup"><span data-stu-id="33b33-148">Takes a folder path as input and produces a collection of <xref:System.Drawing.Bitmap> objects as output.</span></span>|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="33b33-149">使用集合<xref:System.Drawing.Bitmap>物件做為輸入，並會產生複合點陣圖做為輸出。</span><span class="sxs-lookup"><span data-stu-id="33b33-149">Takes a collection of <xref:System.Drawing.Bitmap> objects as input and produces a composite bitmap as output.</span></span>|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<span data-ttu-id="33b33-150">在表單上顯示複合點陣圖。</span><span class="sxs-lookup"><span data-stu-id="33b33-150">Displays the composite bitmap on the form.</span></span>|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<span data-ttu-id="33b33-151">顯示映像以表示作業已取消，讓使用者選取另一個資料夾。</span><span class="sxs-lookup"><span data-stu-id="33b33-151">Displays an image to indicate that the operation is canceled and enables the user to select another folder.</span></span>|  
  
 <span data-ttu-id="33b33-152">若要連接的資料流程區塊以形成網路，這個範例會使用<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="33b33-152">To connect the dataflow blocks to form a network, this example uses the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method.</span></span> <span data-ttu-id="33b33-153"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>方法包含的多載的版本採用<xref:System.Predicate%601>判斷目標區塊接受或拒絕訊息的物件。</span><span class="sxs-lookup"><span data-stu-id="33b33-153">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method contains an overloaded version that takes a <xref:System.Predicate%601> object that determines whether the target block accepts or rejects a message.</span></span> <span data-ttu-id="33b33-154">這個篩選機制可讓訊息區塊僅接收特定的值。</span><span class="sxs-lookup"><span data-stu-id="33b33-154">This filtering mechanism enables message blocks to receive only certain values.</span></span> <span data-ttu-id="33b33-155">在此範例中，網路可以使用兩種方式之一進行分支。</span><span class="sxs-lookup"><span data-stu-id="33b33-155">In this example, the network can branch in one of two ways.</span></span> <span data-ttu-id="33b33-156">主要分支會從磁碟載入映像、建立複合映像，以及在表單上顯示該映像。</span><span class="sxs-lookup"><span data-stu-id="33b33-156">The main branch loads the images from disk, creates the composite image, and displays that image on the form.</span></span> <span data-ttu-id="33b33-157">替代分支會取消目前的作業。</span><span class="sxs-lookup"><span data-stu-id="33b33-157">The alternate branch cancels the current operation.</span></span> <span data-ttu-id="33b33-158"><xref:System.Predicate%601>物件可讓資料流程區塊，沿著主要分支中切換至替代的分支，拒絕特定訊息。</span><span class="sxs-lookup"><span data-stu-id="33b33-158">The <xref:System.Predicate%601> objects enable the dataflow blocks along the main branch to switch to the alternative branch by rejecting certain messages.</span></span> <span data-ttu-id="33b33-159">例如，如果使用者取消作業，資料流程區塊 `createCompositeBitmap` 會產生 `null` (在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中為 `Nothing`) 做為其輸出。</span><span class="sxs-lookup"><span data-stu-id="33b33-159">For example, if the user cancels the operation, the dataflow block `createCompositeBitmap` produces `null` (`Nothing` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) as its output.</span></span> <span data-ttu-id="33b33-160">資料流程區塊 `displayCompositeBitmap` 會拒絕 `null` 輸入值，因此，訊息會提供給 `operationCancelled`。</span><span class="sxs-lookup"><span data-stu-id="33b33-160">The dataflow block `displayCompositeBitmap` rejects `null` input values, and therefore, the message is offered to `operationCancelled`.</span></span> <span data-ttu-id="33b33-161">資料流程區塊 `operationCancelled` 接受所有訊息，因此，會顯示映像表示作業取消。</span><span class="sxs-lookup"><span data-stu-id="33b33-161">The dataflow block `operationCancelled` accepts all messages and therefore, displays an image to indicate that the operation is canceled.</span></span>  
  
 <span data-ttu-id="33b33-162">下圖顯示映像處理網路。</span><span class="sxs-lookup"><span data-stu-id="33b33-162">The following illustration shows the image processing network.</span></span>  
  
 <span data-ttu-id="33b33-163">![影像處理網路](../../../docs/standard/parallel-programming/media/dataflowwinforms.png "DataflowWinForms")</span><span class="sxs-lookup"><span data-stu-id="33b33-163">![The image processing network](../../../docs/standard/parallel-programming/media/dataflowwinforms.png "DataflowWinForms")</span></span>  
  
 <span data-ttu-id="33b33-164">由於 `displayCompositeBitmap` 和 `operationCancelled`資料流程區塊會在使用者介面上進行處理，因此這個動作一定要在使用者介面執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="33b33-164">Because the `displayCompositeBitmap` and `operationCancelled` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="33b33-165">若要達成此目的，在建構期間，這些物件每一個都提供<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>具有物件<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A>屬性設定為<xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="33b33-165">To accomplish this, during construction, these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="33b33-166"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> 方法會建立 <xref:System.Threading.Tasks.TaskScheduler> 物件，該物件會在目前的同步處理內容上執行工作。</span><span class="sxs-lookup"><span data-stu-id="33b33-166">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="33b33-167">因為 `CreateImageProcessingNetwork` 方法是從 [選擇資料夾] 按鈕的處理常式呼叫，它會在使用者介面執行緒上執行，`displayCompositeBitmap` 和 `operationCancelled` 資料流程區塊的動作也會在使用者介面執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="33b33-167">Because the `CreateImageProcessingNetwork` method is called from the handler of the **Choose Folder** button, which runs on the user-interface thread, the actions for the `displayCompositeBitmap` and `operationCancelled` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="33b33-168">這個範例會使用共用的取消語彙基元而非設定<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>屬性因為<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>屬性永遠會取消資料流程區塊執行。</span><span class="sxs-lookup"><span data-stu-id="33b33-168">This example uses a shared cancellation token instead of setting the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution.</span></span> <span data-ttu-id="33b33-169">取消語彙基元可讓此範例重複使用相同的資料流程網路多次，即使使用者取消一或多個作業。</span><span class="sxs-lookup"><span data-stu-id="33b33-169">A cancellation token enables this example to reuse the same dataflow network multiple times, even when the user cancels one or more operations.</span></span> <span data-ttu-id="33b33-170">如需範例，會使用<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>永久取消資料流程區塊的執行，請參閱[如何： 取消資料流程區塊](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)。</span><span class="sxs-lookup"><span data-stu-id="33b33-170">For an example that uses <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> to permanently cancel the execution of a dataflow block, see [How to: Cancel a Dataflow Block](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).</span></span>  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a><span data-ttu-id="33b33-171">連接資料流程網路與使用者介面</span><span class="sxs-lookup"><span data-stu-id="33b33-171">Connecting the Dataflow Network to the User Interface</span></span>  
 <span data-ttu-id="33b33-172">本節描述如何連接資料流程網路與使用者介面。</span><span class="sxs-lookup"><span data-stu-id="33b33-172">This section describes how to connect the dataflow network to the user interface.</span></span> <span data-ttu-id="33b33-173">建立複合映像和取消作業是從 [選擇資料夾] 和 [取消] 按鈕起始。</span><span class="sxs-lookup"><span data-stu-id="33b33-173">The creation of the composite image and cancellation of the operation are initiated from the **Choose Folder** and **Cancel** buttons.</span></span> <span data-ttu-id="33b33-174">當使用者選擇任一個按鈕時，會以非同步方式起始適當的動作。</span><span class="sxs-lookup"><span data-stu-id="33b33-174">When the user chooses either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
#### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a><span data-ttu-id="33b33-175">若要連接資料流程網路與使用者介面</span><span class="sxs-lookup"><span data-stu-id="33b33-175">To Connect the Dataflow Network to the User Interface</span></span>  
  
1.  <span data-ttu-id="33b33-176">在主要表單的表單設計工具，建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件**選擇資料夾** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="33b33-176">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Choose Folder** button.</span></span>  
  
2.  <span data-ttu-id="33b33-177">實作<xref:System.Windows.Forms.ToolStripItem.Click>事件**選擇資料夾** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="33b33-177">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Choose Folder** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3.  <span data-ttu-id="33b33-178">在主要表單的表單設計工具，建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件**取消** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="33b33-178">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="33b33-179">實作<xref:System.Windows.Forms.ToolStripItem.Click>事件**取消** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="33b33-179">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="33b33-180">完整範例</span><span class="sxs-lookup"><span data-stu-id="33b33-180">The Complete Example</span></span>  
 <span data-ttu-id="33b33-181">下列範例將示範本逐步解說的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="33b33-181">The following example shows the complete code for this walkthrough.</span></span>  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 <span data-ttu-id="33b33-182">下圖顯示通用 \Sample Pictures\ 資料夾的一般輸出。</span><span class="sxs-lookup"><span data-stu-id="33b33-182">The following illustration shows typical output for the common \Sample Pictures\ folder.</span></span>  
  
 <span data-ttu-id="33b33-183">![Windows Forms 應用程式](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")</span><span class="sxs-lookup"><span data-stu-id="33b33-183">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="33b33-184">後續步驟</span><span class="sxs-lookup"><span data-stu-id="33b33-184">Next Steps</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33b33-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33b33-185">See Also</span></span>  
 [<span data-ttu-id="33b33-186">資料流程</span><span class="sxs-lookup"><span data-stu-id="33b33-186">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
