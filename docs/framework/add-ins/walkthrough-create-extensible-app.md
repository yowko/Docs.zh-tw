---
title: 逐步解說：建立可延伸應用程式
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
caps.latest.revision: 32
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8946e30ac9d7a224af7801bc721e7d9cf6e1fab0
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-creating-an-extensible-application"></a><span data-ttu-id="4e454-102">逐步解說：建立可延伸應用程式</span><span class="sxs-lookup"><span data-stu-id="4e454-102">Walkthrough: Creating an Extensible Application</span></span>
<span data-ttu-id="4e454-103">本逐步解說描述如何建立會執行簡單的計算機功能的增益集的管線。</span><span class="sxs-lookup"><span data-stu-id="4e454-103">This walkthrough describes how to create a pipeline for an add-in that performs simple calculator functions.</span></span> <span data-ttu-id="4e454-104">不會示範真實世界的實例。相反地，它會示範在管線，以及如何增益集可以提供主機服務的基本功能。</span><span class="sxs-lookup"><span data-stu-id="4e454-104">It does not demonstrate a real-world scenario; rather, it demonstrates the basic functionality of a pipeline and how an add-in can provide services for a host.</span></span>  
  
 <span data-ttu-id="4e454-105">本逐步解說將說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="4e454-105">This walkthrough describes the following tasks:</span></span>  
  
-   <span data-ttu-id="4e454-106">建立 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-106">Creating a Visual Studio solution.</span></span>  
  
-   <span data-ttu-id="4e454-107">建立管線目錄結構。</span><span class="sxs-lookup"><span data-stu-id="4e454-107">Creating the pipeline directory structure.</span></span>  
  
-   <span data-ttu-id="4e454-108">正在建立的合約和檢視表。</span><span class="sxs-lookup"><span data-stu-id="4e454-108">Creating the contract and views.</span></span>  
  
-   <span data-ttu-id="4e454-109">建立增益集端配接器。</span><span class="sxs-lookup"><span data-stu-id="4e454-109">Creating the add-in-side adapter.</span></span>  
  
-   <span data-ttu-id="4e454-110">建立主應用程式端配接器。</span><span class="sxs-lookup"><span data-stu-id="4e454-110">Creating the host-side adapter.</span></span>  
  
-   <span data-ttu-id="4e454-111">建立主機。</span><span class="sxs-lookup"><span data-stu-id="4e454-111">Creating the host.</span></span>  
  
-   <span data-ttu-id="4e454-112">建立增益集。</span><span class="sxs-lookup"><span data-stu-id="4e454-112">Creating the add-in.</span></span>  
  
-   <span data-ttu-id="4e454-113">部署管線。</span><span class="sxs-lookup"><span data-stu-id="4e454-113">Deploying the pipeline.</span></span>  
  
-   <span data-ttu-id="4e454-114">執行主應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e454-114">Running the host application.</span></span>  
  
 <span data-ttu-id="4e454-115">此管線傳遞僅可序列化的型別 (<xref:System.Double>和<xref:System.String>)、 主機和增益集之間。</span><span class="sxs-lookup"><span data-stu-id="4e454-115">This pipeline passes only serializable types (<xref:System.Double> and <xref:System.String>), between the host and the add-in.</span></span> <span data-ttu-id="4e454-116">如需示範如何將複雜資料型別集合的範例，請參閱[逐步解說： 將傳遞主機集合與增益集](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)。</span><span class="sxs-lookup"><span data-stu-id="4e454-116">For an example that shows how to pass collections of complex data types, see [Walkthrough: Passing Collections Between Hosts and Add-Ins](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span></span>  
  
 <span data-ttu-id="4e454-117">這個管線的合約會定義四個的算術運算的物件模型： 加入、 減、 乘、 和分割。</span><span class="sxs-lookup"><span data-stu-id="4e454-117">The contract for this pipeline defines an object model of four arithmetic operations: add, subtract, multiply, and divide.</span></span> <span data-ttu-id="4e454-118">使用公式來計算，例如 2 + 2，主機會提供增益集和增益集傳回結果至主機。</span><span class="sxs-lookup"><span data-stu-id="4e454-118">The host provides the add-in with an equation to calculate, such as 2 + 2, and the add-in returns the result to the host.</span></span>  
  
 <span data-ttu-id="4e454-119">第 2 版的計算機增益集提供更多計算的可能性，並示範版本控制。</span><span class="sxs-lookup"><span data-stu-id="4e454-119">Version 2 of the calculator add-in provides more calculating possibilities and demonstrates versioning.</span></span> <span data-ttu-id="4e454-120">中描述[逐步解說： 為您的主機變更啟用回溯相容性](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)。</span><span class="sxs-lookup"><span data-stu-id="4e454-120">It is described in [Walkthrough: Enabling Backward Compatibility as Your Host Changes](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4e454-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="4e454-121">Prerequisites</span></span>  
 <span data-ttu-id="4e454-122">您需要下列項目才能完成本逐步解說：</span><span class="sxs-lookup"><span data-stu-id="4e454-122">You need the following to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="4e454-123">Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4e454-123">Visual Studio.</span></span>  
  
## <a name="creating-a-visual-studio-solution"></a><span data-ttu-id="4e454-124">建立 Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="4e454-124">Creating a Visual Studio Solution</span></span>  
 <span data-ttu-id="4e454-125">使用 Visual Studio 中的解決方案，以包含管線區段的專案。</span><span class="sxs-lookup"><span data-stu-id="4e454-125">Use a solution in Visual Studio to contain the projects of your pipeline segments.</span></span>  
  
#### <a name="to-create-the-pipeline-solution"></a><span data-ttu-id="4e454-126">若要建立管線方案</span><span class="sxs-lookup"><span data-stu-id="4e454-126">To create the pipeline solution</span></span>  
  
1.  <span data-ttu-id="4e454-127">在 Visual Studio 中，建立新的專案，名為`Calc1Contract`。</span><span class="sxs-lookup"><span data-stu-id="4e454-127">In Visual Studio, create a new project named `Calc1Contract`.</span></span> <span data-ttu-id="4e454-128">它的基礎**類別庫**範本。</span><span class="sxs-lookup"><span data-stu-id="4e454-128">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="4e454-129">將方案命名`CalculatorV1`。</span><span class="sxs-lookup"><span data-stu-id="4e454-129">Name the solution `CalculatorV1`.</span></span>  
  
## <a name="creating-the-pipeline-directory-structure"></a><span data-ttu-id="4e454-130">建立管線目錄結構</span><span class="sxs-lookup"><span data-stu-id="4e454-130">Creating the Pipeline Directory Structure</span></span>  
 <span data-ttu-id="4e454-131">增益集模型要求管線區段組件應置於指定的目錄結構。</span><span class="sxs-lookup"><span data-stu-id="4e454-131">The add-in model requires the pipeline segment assemblies to be placed in a specified directory structure.</span></span> <span data-ttu-id="4e454-132">如需管線結構的詳細資訊，請參閱[管線開發需求](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。</span><span class="sxs-lookup"><span data-stu-id="4e454-132">For more information about the pipeline structure, see [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
#### <a name="to-create-the-pipeline-directory-structure"></a><span data-ttu-id="4e454-133">若要建立管線目錄結構</span><span class="sxs-lookup"><span data-stu-id="4e454-133">To create the pipeline directory structure</span></span>  
  
1.  <span data-ttu-id="4e454-134">在您的電腦上的任何位置建立應用程式資料夾。</span><span class="sxs-lookup"><span data-stu-id="4e454-134">Create an application folder anywhere on your computer.</span></span>  
  
2.  <span data-ttu-id="4e454-135">在該資料夾中建立下列結構：</span><span class="sxs-lookup"><span data-stu-id="4e454-135">In that folder, create the following structure:</span></span>  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     <span data-ttu-id="4e454-136">不需要將管線資料夾結構放在應用程式資料夾。完成以下只是為了方便起見。</span><span class="sxs-lookup"><span data-stu-id="4e454-136">It is not necessary to put the pipeline folder structure in your application folder; it is done here only for convenience.</span></span> <span data-ttu-id="4e454-137">在適當的步驟，逐步解說會說明如何變更程式碼，如果管線資料夾結構是在不同的位置。</span><span class="sxs-lookup"><span data-stu-id="4e454-137">At the appropriate step, the walkthrough explains how to change the code if the pipeline folder structure is in a different location.</span></span> <span data-ttu-id="4e454-138">請參閱中的管線目錄需求的討論[管線開發需求](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。</span><span class="sxs-lookup"><span data-stu-id="4e454-138">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4e454-139">`CalcV2`資料夾不是在本逐步解說，它是一個預留位置，如[逐步解說： 為您的主機變更啟用回溯相容性](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)。</span><span class="sxs-lookup"><span data-stu-id="4e454-139">The `CalcV2` folder is not used in this walkthrough; it is a placeholder for [Walkthrough: Enabling Backward Compatibility as Your Host Changes](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="creating-the-contract-and-views"></a><span data-ttu-id="4e454-140">建立合約和檢視</span><span class="sxs-lookup"><span data-stu-id="4e454-140">Creating the Contract and Views</span></span>  
 <span data-ttu-id="4e454-141">此管線的合約區段會定義`ICalc1Contract`介面，定義四種方法： `add`， `subtract`， `multiply`，和`divide`。</span><span class="sxs-lookup"><span data-stu-id="4e454-141">The contract segment for this pipeline defines the `ICalc1Contract` interface, which defines four methods: `add`, `subtract`, `multiply`, and `divide`.</span></span>  
  
#### <a name="to-create-the-contract"></a><span data-ttu-id="4e454-142">若要建立合約</span><span class="sxs-lookup"><span data-stu-id="4e454-142">To create the contract</span></span>  
  
1.  <span data-ttu-id="4e454-143">名為 Visual Studio 方案中`CalculatorV1`，開啟`Calc1Contract`專案。</span><span class="sxs-lookup"><span data-stu-id="4e454-143">In the Visual Studio solution named `CalculatorV1`, open the `Calc1Contract` project.</span></span>  
  
2.  <span data-ttu-id="4e454-144">在**方案總管 中**，加入下列組件的參考`Calc1Contract`專案：</span><span class="sxs-lookup"><span data-stu-id="4e454-144">In **Solution Explorer**, add references to the following assemblies to the `Calc1Contract` project:</span></span>  
  
     <span data-ttu-id="4e454-145">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="4e454-145">System.AddIn.Contract.dll</span></span>  
  
     <span data-ttu-id="4e454-146">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="4e454-146">System.AddIn.dll</span></span>  
  
3.  <span data-ttu-id="4e454-147">在**方案總管 中**，排除加入新的預設類別**類別庫**專案。</span><span class="sxs-lookup"><span data-stu-id="4e454-147">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects.</span></span>  
  
4.  <span data-ttu-id="4e454-148">在**方案總管 中**，加入新項目加入專案中，使用**介面**範本。</span><span class="sxs-lookup"><span data-stu-id="4e454-148">In **Solution Explorer**, add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="4e454-149">在**加入新項目**對話方塊中，名稱介面`ICalc1Contract`。</span><span class="sxs-lookup"><span data-stu-id="4e454-149">In the **Add New Item** dialog box, name the interface `ICalc1Contract`.</span></span>  
  
5.  <span data-ttu-id="4e454-150">在介面檔案中加入命名空間的參考<xref:System.AddIn.Contract>和<xref:System.AddIn.Pipeline>。</span><span class="sxs-lookup"><span data-stu-id="4e454-150">In the interface file, add namespace references to <xref:System.AddIn.Contract> and <xref:System.AddIn.Pipeline>.</span></span>  
  
6.  <span data-ttu-id="4e454-151">您可以使用下列程式碼來完成此合約區段。</span><span class="sxs-lookup"><span data-stu-id="4e454-151">Use the following code to complete this contract segment.</span></span> <span data-ttu-id="4e454-152">請注意，此介面必須<xref:System.AddIn.Pipeline.AddInContractAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="4e454-152">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInContractAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  <span data-ttu-id="4e454-153">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-153">Optionally, build the Visual Studio solution.</span></span> <span data-ttu-id="4e454-154">無法執行方案，直到最後的程序，但每個程序可確保每個專案都會後建置更正。</span><span class="sxs-lookup"><span data-stu-id="4e454-154">The solution cannot be run until the final procedure, but building it after each procedure ensures that each project is correct.</span></span>  
  
 <span data-ttu-id="4e454-155">由於增益集的檢視和主應用程式檢視的增益集通常在相同的程式碼，特別是增益集的第一個版本，您可以輕鬆檢視建立在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="4e454-155">Because the add-in view and the host view of the add-in usually have the same code, especially in the first version of an add-in, you can easily create the views at the same time.</span></span> <span data-ttu-id="4e454-156">它們之間只能有一個因數的差異： 增益集檢視需要<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性，而增益集的 [主機] 檢視不需要任何屬性。</span><span class="sxs-lookup"><span data-stu-id="4e454-156">They differ by only one factor: the add-in view requires the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute, while the host view of the add-in does not require any attributes.</span></span>  
  
#### <a name="to-create-the-add-in-view"></a><span data-ttu-id="4e454-157">若要建立增益集的檢視</span><span class="sxs-lookup"><span data-stu-id="4e454-157">To create the add-in view</span></span>  
  
1.  <span data-ttu-id="4e454-158">加入新的專案，名為`Calc1AddInView`至`CalculatorV1`方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-158">Add a new project named `Calc1AddInView` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="4e454-159">它的基礎**類別庫**範本。</span><span class="sxs-lookup"><span data-stu-id="4e454-159">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="4e454-160">在**方案總管 中**，將參考加入至 System.AddIn.dll`Calc1AddInView`專案。</span><span class="sxs-lookup"><span data-stu-id="4e454-160">In **Solution Explorer**, add a reference to System.AddIn.dll to the `Calc1AddInView` project.</span></span>  
  
3.  <span data-ttu-id="4e454-161">在**方案總管 中**，排除加入新的預設類別**類別庫**專案，並將新的項目加入至專案，使用**介面**範本。</span><span class="sxs-lookup"><span data-stu-id="4e454-161">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="4e454-162">在**加入新項目**對話方塊中，名稱介面`ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="4e454-162">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
4.  <span data-ttu-id="4e454-163">在介面檔案中，加入的命名空間參考<xref:System.AddIn.Pipeline>。</span><span class="sxs-lookup"><span data-stu-id="4e454-163">In the interface file, add a namespace reference to <xref:System.AddIn.Pipeline>.</span></span>  
  
5.  <span data-ttu-id="4e454-164">您可以使用下列程式碼來完成此增益集檢視。</span><span class="sxs-lookup"><span data-stu-id="4e454-164">Use the following code to complete this add-in view.</span></span> <span data-ttu-id="4e454-165">請注意，此介面必須<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="4e454-165">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  <span data-ttu-id="4e454-166">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-166">Optionally, build the Visual Studio solution.</span></span>  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a><span data-ttu-id="4e454-167">若要建立增益集的 [主機] 檢視</span><span class="sxs-lookup"><span data-stu-id="4e454-167">To create the host view of the add-in</span></span>  
  
1.  <span data-ttu-id="4e454-168">加入新的專案，名為`Calc1HVA`至`CalculatorV1`方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-168">Add a new project named `Calc1HVA` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="4e454-169">它的基礎**類別庫**範本。</span><span class="sxs-lookup"><span data-stu-id="4e454-169">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="4e454-170">在**方案總管 中**，排除加入新的預設類別**類別庫**專案，並將新的項目加入至專案，使用**介面**範本。</span><span class="sxs-lookup"><span data-stu-id="4e454-170">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="4e454-171">在**加入新項目**對話方塊中，名稱介面`ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="4e454-171">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
3.  <span data-ttu-id="4e454-172">在介面檔案中，使用下列程式碼來完成增益集的 [主機] 檢視。</span><span class="sxs-lookup"><span data-stu-id="4e454-172">In the interface file, use the following code to complete the host view of the add-in.</span></span>  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  <span data-ttu-id="4e454-173">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-173">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in-side-adapter"></a><span data-ttu-id="4e454-174">建立增益集端配接器</span><span class="sxs-lookup"><span data-stu-id="4e454-174">Creating the Add-in-side Adapter</span></span>  
 <span data-ttu-id="4e454-175">此增益集端配接器是由一個檢視合約配接器所組成。</span><span class="sxs-lookup"><span data-stu-id="4e454-175">This add-in-side adapter consists of one view-to-contract adapter.</span></span> <span data-ttu-id="4e454-176">這個管線區段轉換從增益集的檢視為合約的型別。</span><span class="sxs-lookup"><span data-stu-id="4e454-176">This pipeline segment converts the types from the add-in view to the contract.</span></span>  
  
 <span data-ttu-id="4e454-177">在此管線中，增益集提供的服務主機，主機，型別從增益集至主機。</span><span class="sxs-lookup"><span data-stu-id="4e454-177">In this pipeline, the add-in provides a service to the host, and the types flow from the add-in to the host.</span></span> <span data-ttu-id="4e454-178">由於沒有型別從主機到增益集，您沒有包含此管線的增益集端上的合約來檢視配接器。</span><span class="sxs-lookup"><span data-stu-id="4e454-178">Because no types flow from the host to the add-in, you do not have to include a contract-to-view adapter on the add-in side of this pipeline.</span></span>  
  
#### <a name="to-create-the-add-in-side-adapter"></a><span data-ttu-id="4e454-179">若要建立增益集端配接器</span><span class="sxs-lookup"><span data-stu-id="4e454-179">To create the add-in-side adapter</span></span>  
  
1.  <span data-ttu-id="4e454-180">加入新的專案，名為`Calc1AddInSideAdapter`至`CalculatorV1`方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-180">Add a new project named `Calc1AddInSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="4e454-181">它的基礎**類別庫**範本。</span><span class="sxs-lookup"><span data-stu-id="4e454-181">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="4e454-182">在**方案總管 中**，加入下列組件的參考`Calc1AddInSideAdapter`專案：</span><span class="sxs-lookup"><span data-stu-id="4e454-182">In **Solution Explorer**, add references to the following assemblies to the `Calc1AddInSideAdapter` project:</span></span>  
  
     <span data-ttu-id="4e454-183">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="4e454-183">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="4e454-184">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="4e454-184">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="4e454-185">加入相鄰的管線區段的專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="4e454-185">Add project references to the projects for the adjacent pipeline segments:</span></span>  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  <span data-ttu-id="4e454-186">選取每個專案參考，然後在**屬性**設定**複製到本機**至**False**。</span><span class="sxs-lookup"><span data-stu-id="4e454-186">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="4e454-187">在 Visual Basic 使用**參考** 索引標籤**專案屬性**設定**複製到本機**至**False**為兩個專案的參考。</span><span class="sxs-lookup"><span data-stu-id="4e454-187">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="4e454-188">重新命名專案的預設類別`CalculatorViewToContractAddInSideAdapter`。</span><span class="sxs-lookup"><span data-stu-id="4e454-188">Rename the project's default class `CalculatorViewToContractAddInSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="4e454-189">在類別檔案中，加入命名空間參考<xref:System.AddIn.Pipeline>。</span><span class="sxs-lookup"><span data-stu-id="4e454-189">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="4e454-190">在類別檔案中，加入相鄰的區段的命名空間參考：`CalcAddInViews`和`CalculatorContracts`。</span><span class="sxs-lookup"><span data-stu-id="4e454-190">In the class file, add namespace references for the adjacent segments: `CalcAddInViews` and `CalculatorContracts`.</span></span> <span data-ttu-id="4e454-191">(在 Visual Basic 中為這些命名空間參考`Calc1AddInView.CalcAddInViews`和`Calc1Contract.CalculatorContracts`，除非您已在 Visual Basic 專案中關閉的預設命名空間。)</span><span class="sxs-lookup"><span data-stu-id="4e454-191">(In Visual Basic, these namespace references are `Calc1AddInView.CalcAddInViews` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="4e454-192">套用<xref:System.AddIn.Pipeline.AddInAdapterAttribute>屬性`CalculatorViewToContractAddInSideAdapter`類別，將其識別為增益集端配接器。</span><span class="sxs-lookup"><span data-stu-id="4e454-192">Apply the <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute to the `CalculatorViewToContractAddInSideAdapter` class, to identify it as the add-in-side adapter.</span></span>  
  
9. <span data-ttu-id="4e454-193">請`CalculatorViewToContractAddInSideAdapter`類別繼承<xref:System.AddIn.Pipeline.ContractBase>，其提供的預設實作<xref:System.AddIn.Contract.IContract>介面，並實作管線的合約介面`ICalc1Contract`。</span><span class="sxs-lookup"><span data-stu-id="4e454-193">Make the `CalculatorViewToContractAddInSideAdapter` class inherit <xref:System.AddIn.Pipeline.ContractBase>, which provides a default implementation of the <xref:System.AddIn.Contract.IContract> interface, and implement the contract interface for the pipeline, `ICalc1Contract`.</span></span>  
  
10. <span data-ttu-id="4e454-194">新增公用建構函式可接受`ICalculator`、 放入快取中的私用欄位，並呼叫基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="4e454-194">Add a public constructor that accepts an `ICalculator`, caches it in a private field, and calls the base class constructor.</span></span>  
  
11. <span data-ttu-id="4e454-195">若要實作的成員`ICalc1Contract`，只需呼叫的對應成員`ICalculator`會傳遞至建構函式，並傳回結果的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4e454-195">To implement the members of `ICalc1Contract`, simply call the corresponding members of the `ICalculator` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="4e454-196">這會調整檢視 (`ICalculator`) 的合約 (`ICalc1Contract`)。</span><span class="sxs-lookup"><span data-stu-id="4e454-196">This adapts the view (`ICalculator`) to the contract (`ICalc1Contract`).</span></span>  
  
     <span data-ttu-id="4e454-197">下列程式碼顯示完整的增益集端配接器。</span><span class="sxs-lookup"><span data-stu-id="4e454-197">The following code shows the completed add-in-side adapter.</span></span>  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. <span data-ttu-id="4e454-198">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-198">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host-side-adapter"></a><span data-ttu-id="4e454-199">建立主應用程式端配接器</span><span class="sxs-lookup"><span data-stu-id="4e454-199">Creating the Host-side Adapter</span></span>  
 <span data-ttu-id="4e454-200">這個主應用程式端配接器是由一個合約來檢視配接器所組成。</span><span class="sxs-lookup"><span data-stu-id="4e454-200">This host-side adapter consists of one contract-to-view adapter.</span></span> <span data-ttu-id="4e454-201">此區段會調整到主機的檢視增益集的合約。</span><span class="sxs-lookup"><span data-stu-id="4e454-201">This segment adapts the contract to the host view of the add-in.</span></span>  
  
 <span data-ttu-id="4e454-202">在此管線中，增益集提供服務給主機和類型流程從增益集至主機。</span><span class="sxs-lookup"><span data-stu-id="4e454-202">In this pipeline, the add-in provides a service to the host and the types flow from the add-in to the host.</span></span> <span data-ttu-id="4e454-203">由於沒有型別從主機到增益集，您不必包括檢視合約介面卡。</span><span class="sxs-lookup"><span data-stu-id="4e454-203">Because no types flow from the host to the add-in, you do not have to include a view-to-contract adapter.</span></span>  
  
 <span data-ttu-id="4e454-204">若要實作生命週期管理，請使用<xref:System.AddIn.Pipeline.ContractHandle>物件存留期語彙基元附加的合約。</span><span class="sxs-lookup"><span data-stu-id="4e454-204">To implement lifetime management, use a <xref:System.AddIn.Pipeline.ContractHandle> object to attach a lifetime token to the contract.</span></span> <span data-ttu-id="4e454-205">您必須將此控制代碼的參考在存留期管理工作的順序。</span><span class="sxs-lookup"><span data-stu-id="4e454-205">You must keep a reference to this handle in order for lifetime management to work.</span></span> <span data-ttu-id="4e454-206">套用語彙基元之後，任何其他程式設計需要不，因為增益集系統可以處置的物件時便不再使用，讓它們可供記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="4e454-206">After the token is applied, no additional programming is required because the add-in system can dispose of objects when they are no longer being used and make them available for garbage collection.</span></span> <span data-ttu-id="4e454-207">如需詳細資訊，請參閱[生命週期管理](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5)。</span><span class="sxs-lookup"><span data-stu-id="4e454-207">For more information, see [Lifetime Management](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
#### <a name="to-create-the-host-side-adapter"></a><span data-ttu-id="4e454-208">若要建立主應用程式端配接器</span><span class="sxs-lookup"><span data-stu-id="4e454-208">To create the host-side adapter</span></span>  
  
1.  <span data-ttu-id="4e454-209">加入新的專案，名為`Calc1HostSideAdapter`至`CalculatorV1`方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-209">Add a new project named `Calc1HostSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="4e454-210">它的基礎**類別庫**範本。</span><span class="sxs-lookup"><span data-stu-id="4e454-210">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="4e454-211">在**方案總管 中**，加入下列組件的參考`Calc1HostSideAdapter`專案：</span><span class="sxs-lookup"><span data-stu-id="4e454-211">In **Solution Explorer**, add references to the following assemblies to the `Calc1HostSideAdapter` project:</span></span>  
  
     <span data-ttu-id="4e454-212">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="4e454-212">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="4e454-213">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="4e454-213">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="4e454-214">加入相鄰的區段的專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="4e454-214">Add project references to the projects for the adjacent segments:</span></span>  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  <span data-ttu-id="4e454-215">選取每個專案參考，然後在**屬性**設定**複製到本機**至**False**。</span><span class="sxs-lookup"><span data-stu-id="4e454-215">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="4e454-216">在 Visual Basic 使用**參考** 索引標籤**專案屬性**設定**複製到本機**至**False**為兩個專案的參考。</span><span class="sxs-lookup"><span data-stu-id="4e454-216">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="4e454-217">重新命名專案的預設類別`CalculatorContractToViewHostSideAdapter`。</span><span class="sxs-lookup"><span data-stu-id="4e454-217">Rename the project's default class `CalculatorContractToViewHostSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="4e454-218">在類別檔案中，加入命名空間參考<xref:System.AddIn.Pipeline>。</span><span class="sxs-lookup"><span data-stu-id="4e454-218">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="4e454-219">在類別檔案中，加入相鄰的區段的命名空間參考：`CalcHVAs`和`CalculatorContracts`。</span><span class="sxs-lookup"><span data-stu-id="4e454-219">In the class file, add namespace references for the adjacent segments: `CalcHVAs` and `CalculatorContracts`.</span></span> <span data-ttu-id="4e454-220">(在 Visual Basic 中為這些命名空間參考`Calc1HVA.CalcHVAs`和`Calc1Contract.CalculatorContracts`，除非您已在 Visual Basic 專案中關閉的預設命名空間。)</span><span class="sxs-lookup"><span data-stu-id="4e454-220">(In Visual Basic, these namespace references are `Calc1HVA.CalcHVAs` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="4e454-221">套用<xref:System.AddIn.Pipeline.HostAdapterAttribute>屬性`CalculatorContractToViewHostSideAdapter`類別，以識別為主應用程式端配接器區段。</span><span class="sxs-lookup"><span data-stu-id="4e454-221">Apply the <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribute to the `CalculatorContractToViewHostSideAdapter` class, to identify it as the host-side adapter segment.</span></span>  
  
9. <span data-ttu-id="4e454-222">請`CalculatorContractToViewHostSideAdapter`類別實作介面，代表增益集的 [主機] 檢視： `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator`在 Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="4e454-222">Make the `CalculatorContractToViewHostSideAdapter` class implement the interface that represents the host view of the add-in: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` in Visual Basic).</span></span>  
  
10. <span data-ttu-id="4e454-223">新增公用建構函式可接受管線的合約型別， `ICalc1Contract`。</span><span class="sxs-lookup"><span data-stu-id="4e454-223">Add a public constructor that accepts the pipeline contract type, `ICalc1Contract`.</span></span> <span data-ttu-id="4e454-224">建構函式必須快取之合約的參考。</span><span class="sxs-lookup"><span data-stu-id="4e454-224">The constructor must cache the reference to the contract.</span></span> <span data-ttu-id="4e454-225">它也必須建立並快取新<xref:System.AddIn.Pipeline.ContractHandle>合約，若要管理的增益集的存留期。</span><span class="sxs-lookup"><span data-stu-id="4e454-225">It must also create and cache a new <xref:System.AddIn.Pipeline.ContractHandle> for the contract, to manage the lifetime of the add-in.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4e454-226"><xref:System.AddIn.Pipeline.ContractHandle> ，請務必存留期管理。</span><span class="sxs-lookup"><span data-stu-id="4e454-226">The <xref:System.AddIn.Pipeline.ContractHandle> is critical to lifetime management.</span></span> <span data-ttu-id="4e454-227">如果您無法將參考保留<xref:System.AddIn.Pipeline.ContractHandle>物件，記憶體回收會回收，及管線時您的程式不會預期它會關閉。</span><span class="sxs-lookup"><span data-stu-id="4e454-227">If you fail to keep a reference to the <xref:System.AddIn.Pipeline.ContractHandle> object, garbage collection will reclaim it, and the pipeline will shut down when your program does not expect it.</span></span> <span data-ttu-id="4e454-228">這可能會導致錯誤很難進行診斷，例如<xref:System.AppDomainUnloadedException>。</span><span class="sxs-lookup"><span data-stu-id="4e454-228">This can lead to errors that are difficult to diagnose, such as <xref:System.AppDomainUnloadedException>.</span></span> <span data-ttu-id="4e454-229">Shutdown 正在正常階段生命週期的管線，因此沒有任何方法的存留期管理程式碼偵測此狀況，會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4e454-229">Shutdown is a normal stage in the life of a pipeline, so there is no way for the lifetime management code to detect that this condition is an error.</span></span>  
  
11. <span data-ttu-id="4e454-230">若要實作的成員`ICalculator`，只需呼叫的對應成員`ICalc1Contract`會傳遞至建構函式，並傳回結果的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4e454-230">To implement the members of `ICalculator`, simply call the corresponding members of the `ICalc1Contract` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="4e454-231">這會調整的合約 (`ICalc1Contract`) 檢視 (`ICalculator`)。</span><span class="sxs-lookup"><span data-stu-id="4e454-231">This adapts the contract (`ICalc1Contract`) to the view (`ICalculator`).</span></span>  
  
     <span data-ttu-id="4e454-232">下列程式碼顯示完整的主應用程式端配接器。</span><span class="sxs-lookup"><span data-stu-id="4e454-232">The following code shows the completed host-side adapter.</span></span>  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. <span data-ttu-id="4e454-233">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-233">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host"></a><span data-ttu-id="4e454-234">建立主機</span><span class="sxs-lookup"><span data-stu-id="4e454-234">Creating the Host</span></span>  
 <span data-ttu-id="4e454-235">主應用程式互動的增益集透過增益集的 [主機] 檢視。</span><span class="sxs-lookup"><span data-stu-id="4e454-235">A host application interacts with the add-in through the host view of the add-in.</span></span> <span data-ttu-id="4e454-236">它會使用增益集探索與啟用方法所提供<xref:System.AddIn.Hosting.AddInStore>和<xref:System.AddIn.Hosting.AddInToken>類別來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="4e454-236">It uses add-in discovery and activation methods provided by the <xref:System.AddIn.Hosting.AddInStore> and <xref:System.AddIn.Hosting.AddInToken> classes to do the following:</span></span>  
  
-   <span data-ttu-id="4e454-237">更新快取的管線和增益集的資訊。</span><span class="sxs-lookup"><span data-stu-id="4e454-237">Update the cache of pipeline and add-in information.</span></span>  
  
-   <span data-ttu-id="4e454-238">尋找增益集主機檢視類型的`ICalculator`，指定的管線根目錄下。</span><span class="sxs-lookup"><span data-stu-id="4e454-238">Find add-ins of the host view type, `ICalculator`, under the specified pipeline root directory.</span></span>  
  
-   <span data-ttu-id="4e454-239">提示使用者指定的增益集使用。</span><span class="sxs-lookup"><span data-stu-id="4e454-239">Prompt the user to specify which add-in to use.</span></span>  
  
-   <span data-ttu-id="4e454-240">啟用所選增益新應用程式定義域中具有指定之安全性的信任層級。</span><span class="sxs-lookup"><span data-stu-id="4e454-240">Activate the selected add-in in a new application domain with a specified security trust level.</span></span>  
  
-   <span data-ttu-id="4e454-241">執行自訂`RunCalculator`方法，這個方法會呼叫增益集的增益集的 [主機] 檢視中所指定的方法。</span><span class="sxs-lookup"><span data-stu-id="4e454-241">Run the custom `RunCalculator` method, which calls the add-in's methods as specified by the host view of the add-in.</span></span>  
  
#### <a name="to-create-the-host"></a><span data-ttu-id="4e454-242">若要建立主應用程式</span><span class="sxs-lookup"><span data-stu-id="4e454-242">To create the host</span></span>  
  
1.  <span data-ttu-id="4e454-243">加入新的專案，名為`Calc1Host`至`CalculatorV1`方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-243">Add a new project named `Calc1Host` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="4e454-244">它的基礎**主控台應用程式**範本。</span><span class="sxs-lookup"><span data-stu-id="4e454-244">Base it on the **Console Application** template.</span></span>  
  
2.  <span data-ttu-id="4e454-245">在**方案總管 中**，加入 System.AddIn.dll 組件的參考`Calc1Host`專案。</span><span class="sxs-lookup"><span data-stu-id="4e454-245">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the `Calc1Host` project.</span></span>  
  
3.  <span data-ttu-id="4e454-246">將專案參考加入`Calc1HVA`專案。</span><span class="sxs-lookup"><span data-stu-id="4e454-246">Add a project reference to the `Calc1HVA` project.</span></span> <span data-ttu-id="4e454-247">選取該專案的參考，然後在**屬性**設定**複製到本機**至**False**。</span><span class="sxs-lookup"><span data-stu-id="4e454-247">Select the project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="4e454-248">在 Visual Basic 使用**參考** 索引標籤**專案屬性**設定**複製到本機**至**False**。</span><span class="sxs-lookup"><span data-stu-id="4e454-248">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False**.</span></span>  
  
4.  <span data-ttu-id="4e454-249">重新命名類別檔案 （在 Visual Basic 中的模組） `MathHost1`。</span><span class="sxs-lookup"><span data-stu-id="4e454-249">Rename the class file (module in Visual Basic) `MathHost1`.</span></span>  
  
5.  <span data-ttu-id="4e454-250">在 Visual Basic 使用**應用程式** 索引標籤**專案屬性**對話方塊來設定**啟始物件**至**Sub Main**。</span><span class="sxs-lookup"><span data-stu-id="4e454-250">In Visual Basic, use the **Application** tab of the **Project Properties** dialog box to set **Startup object** to **Sub Main**.</span></span>  
  
6.  <span data-ttu-id="4e454-251">在類別或模組檔案中，加入的命名空間參考<xref:System.AddIn.Hosting>。</span><span class="sxs-lookup"><span data-stu-id="4e454-251">In the class or module file, add a namespace reference to <xref:System.AddIn.Hosting>.</span></span>  
  
7.  <span data-ttu-id="4e454-252">在類別或模組檔案中，加入 增益集的 主機 檢視的命名空間參考： `CalcHVAs`。</span><span class="sxs-lookup"><span data-stu-id="4e454-252">In the class or module file, add a namespace reference for the host view of the add-in: `CalcHVAs`.</span></span> <span data-ttu-id="4e454-253">(在 Visual Basic 中為這個命名空間參考`Calc1HVA.CalcHVAs`，除非您已在 Visual Basic 專案中關閉的預設命名空間。)</span><span class="sxs-lookup"><span data-stu-id="4e454-253">(In Visual Basic, this namespace reference is `Calc1HVA.CalcHVAs`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="4e454-254">在**方案總管] 中**，選取方案以及從**專案**功能表中選擇 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="4e454-254">In **Solution Explorer**, select the solution and from the **Project** menu choose **Properties**.</span></span> <span data-ttu-id="4e454-255">在**方案屬性頁** 對話方塊中，將**單一啟始專案**是這個主機應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="4e454-255">In the **Solution Property Pages** dialog box, set the **Single Startup Project** to be this host application project.</span></span>  
  
9. <span data-ttu-id="4e454-256">在類別或模組檔案中，使用<xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType>方法，以更新快取。</span><span class="sxs-lookup"><span data-stu-id="4e454-256">In the class or module file, use the <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> method to update the cache.</span></span> <span data-ttu-id="4e454-257">使用<xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType>方法來取得權杖，集合使用<xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType>方法來啟動增益集。</span><span class="sxs-lookup"><span data-stu-id="4e454-257">Use the <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> method to get a collection of tokens, and use the <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> method to activate an add-in.</span></span>  
  
     <span data-ttu-id="4e454-258">下列程式碼顯示完整的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e454-258">The following code shows the completed host application.</span></span>  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="4e454-259">此程式碼會假設管線資料夾結構位於應用程式資料夾。</span><span class="sxs-lookup"><span data-stu-id="4e454-259">This code assumes that the pipeline folder structure is located in the application folder.</span></span> <span data-ttu-id="4e454-260">如果您位於其他地方，變更設定的程式碼行`addInRoot`變數，使變數包含管線目錄結構的路徑。</span><span class="sxs-lookup"><span data-stu-id="4e454-260">If you located it elsewhere, change the line of code that sets the `addInRoot` variable, so that the variable contains the path to your pipeline directory structure.</span></span>  
  
     <span data-ttu-id="4e454-261">程式碼會使用`ChooseCalculator`清單語彙基元，並提示使用者選擇增益集的方法。</span><span class="sxs-lookup"><span data-stu-id="4e454-261">The code uses a `ChooseCalculator` method to list the tokens and to prompt the user to choose an add-in.</span></span> <span data-ttu-id="4e454-262">`RunCalculator`方法提示使用者提供簡單的數學運算式時，會剖析運算式使用`Parser`類別，並顯示增益集所傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="4e454-262">The `RunCalculator` method prompts the user for simple math expressions, parses the expressions using the `Parser` class, and displays the results returned by the add-in.</span></span>  
  
10. <span data-ttu-id="4e454-263">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-263">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in"></a><span data-ttu-id="4e454-264">建立增益集</span><span class="sxs-lookup"><span data-stu-id="4e454-264">Creating the Add-In</span></span>  
 <span data-ttu-id="4e454-265">增益集實作增益集的檢視所指定的方法。</span><span class="sxs-lookup"><span data-stu-id="4e454-265">An add-in implements the methods specified by the add-in view.</span></span> <span data-ttu-id="4e454-266">此增益集實作`Add`， `Subtract`， `Multiply`，和`Divide`作業並將結果傳回到主應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e454-266">This add-in implements the `Add`, `Subtract`, `Multiply`, and `Divide` operations and returns the results to the host.</span></span>  
  
#### <a name="to-create-the-add-in"></a><span data-ttu-id="4e454-267">若要建立增益集</span><span class="sxs-lookup"><span data-stu-id="4e454-267">To create the add-in</span></span>  
  
1.  <span data-ttu-id="4e454-268">加入新的專案，名為`AddInCalcV1`至`CalculatorV1`方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-268">Add a new project named `AddInCalcV1` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="4e454-269">它的基礎**類別庫**範本。</span><span class="sxs-lookup"><span data-stu-id="4e454-269">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="4e454-270">在**方案總管 中**，System.AddIn.dll 組件的參考加入專案。</span><span class="sxs-lookup"><span data-stu-id="4e454-270">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the project.</span></span>  
  
3.  <span data-ttu-id="4e454-271">將專案參考加入`Calc1AddInView`專案。</span><span class="sxs-lookup"><span data-stu-id="4e454-271">Add a project reference to the `Calc1AddInView` project.</span></span> <span data-ttu-id="4e454-272">選取該專案的參考，然後在**屬性**，將**複製到本機**至**False**。</span><span class="sxs-lookup"><span data-stu-id="4e454-272">Select the project reference, and in **Properties**, set **Copy Local** to **False**.</span></span> <span data-ttu-id="4e454-273">在 Visual Basic 使用**參考** 索引標籤**專案屬性**設定**複製到本機**至**False**專案參考。</span><span class="sxs-lookup"><span data-stu-id="4e454-273">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the project reference.</span></span>  
  
4.  <span data-ttu-id="4e454-274">重新命名類別`AddInCalcV1`。</span><span class="sxs-lookup"><span data-stu-id="4e454-274">Rename the class `AddInCalcV1`.</span></span>  
  
5.  <span data-ttu-id="4e454-275">在類別檔案中，加入的命名空間參考<xref:System.AddIn>與增益集的檢視區段： `CalcAddInViews` (`Calc1AddInView.CalcAddInViews`在 Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="4e454-275">In the class file, add a namespace reference to <xref:System.AddIn> and the add-in view segment: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` in Visual Basic).</span></span>  
  
6.  <span data-ttu-id="4e454-276">套用<xref:System.AddIn.AddInAttribute>屬性`AddInCalcV1`類別，以將類別識別為增益集。</span><span class="sxs-lookup"><span data-stu-id="4e454-276">Apply the <xref:System.AddIn.AddInAttribute> attribute to the `AddInCalcV1` class, to identify the class as an add-in.</span></span>  
  
7.  <span data-ttu-id="4e454-277">請`AddInCalcV1`類別實作介面代表增益集的檢視： `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator`在 Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="4e454-277">Make the `AddInCalcV1` class implement the interface that represents the add-in view: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` in Visual Basic).</span></span>  
  
8.  <span data-ttu-id="4e454-278">實作的成員`ICalculator`藉由傳回適當的計算結果。</span><span class="sxs-lookup"><span data-stu-id="4e454-278">Implement the members of `ICalculator` by returning the results of the appropriate calculations.</span></span>  
  
     <span data-ttu-id="4e454-279">下列程式碼會顯示已完成的增益集。</span><span class="sxs-lookup"><span data-stu-id="4e454-279">The following code shows the completed add-in.</span></span>  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. <span data-ttu-id="4e454-280">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-280">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="deploying-the-pipeline"></a><span data-ttu-id="4e454-281">部署管線</span><span class="sxs-lookup"><span data-stu-id="4e454-281">Deploying the Pipeline</span></span>  
 <span data-ttu-id="4e454-282">您現在準備建置和增益集區段部署至必要的管線目錄結構。</span><span class="sxs-lookup"><span data-stu-id="4e454-282">You are now ready to build and deploy the add-in segments to the required pipeline directory structure.</span></span>  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a><span data-ttu-id="4e454-283">將區段部署至管線</span><span class="sxs-lookup"><span data-stu-id="4e454-283">To deploy the segments to the pipeline</span></span>  
  
1.  <span data-ttu-id="4e454-284">針對每個專案方案中，使用**建置** 索引標籤**專案屬性**(**編譯** 索引標籤，在 Visual Basic 中的) 設定的值**輸出路徑** (**建置輸出路徑**在 Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="4e454-284">For each project in the solution, use the **Build** tab of **Project Properties** (the **Compile** tab in Visual Basic) to set the value of the **Output path** (the **Build output path** in Visual Basic).</span></span> <span data-ttu-id="4e454-285">如果您命名為應用程式資料夾`MyApp`，比方說，您的專案會建置至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="4e454-285">If you named your application folder `MyApp`, for example, your projects would build into the following folders:</span></span>  
  
    |<span data-ttu-id="4e454-286">專案</span><span class="sxs-lookup"><span data-stu-id="4e454-286">Project</span></span>|<span data-ttu-id="4e454-287">路徑</span><span class="sxs-lookup"><span data-stu-id="4e454-287">Path</span></span>|  
    |-------------|----------|  
    |<span data-ttu-id="4e454-288">AddInCalcV1</span><span class="sxs-lookup"><span data-stu-id="4e454-288">AddInCalcV1</span></span>|<span data-ttu-id="4e454-289">MyApp\Pipeline\AddIns\CalcV1</span><span class="sxs-lookup"><span data-stu-id="4e454-289">MyApp\Pipeline\AddIns\CalcV1</span></span>|  
    |<span data-ttu-id="4e454-290">Calc1AddInSideAdapter</span><span class="sxs-lookup"><span data-stu-id="4e454-290">Calc1AddInSideAdapter</span></span>|<span data-ttu-id="4e454-291">MyApp\Pipeline\AddInSideAdapters</span><span class="sxs-lookup"><span data-stu-id="4e454-291">MyApp\Pipeline\AddInSideAdapters</span></span>|  
    |<span data-ttu-id="4e454-292">Calc1AddInView</span><span class="sxs-lookup"><span data-stu-id="4e454-292">Calc1AddInView</span></span>|<span data-ttu-id="4e454-293">MyApp\Pipeline\AddInViews</span><span class="sxs-lookup"><span data-stu-id="4e454-293">MyApp\Pipeline\AddInViews</span></span>|  
    |<span data-ttu-id="4e454-294">Calc1Contract</span><span class="sxs-lookup"><span data-stu-id="4e454-294">Calc1Contract</span></span>|<span data-ttu-id="4e454-295">MyApp\Pipeline\Contracts</span><span class="sxs-lookup"><span data-stu-id="4e454-295">MyApp\Pipeline\Contracts</span></span>|  
    |<span data-ttu-id="4e454-296">Calc1Host</span><span class="sxs-lookup"><span data-stu-id="4e454-296">Calc1Host</span></span>|<span data-ttu-id="4e454-297">MyApp</span><span class="sxs-lookup"><span data-stu-id="4e454-297">MyApp</span></span>|  
    |<span data-ttu-id="4e454-298">Calc1HostSideAdapter</span><span class="sxs-lookup"><span data-stu-id="4e454-298">Calc1HostSideAdapter</span></span>|<span data-ttu-id="4e454-299">MyApp\Pipeline\HostSideAdapters</span><span class="sxs-lookup"><span data-stu-id="4e454-299">MyApp\Pipeline\HostSideAdapters</span></span>|  
    |<span data-ttu-id="4e454-300">Calc1HVA</span><span class="sxs-lookup"><span data-stu-id="4e454-300">Calc1HVA</span></span>|<span data-ttu-id="4e454-301">MyApp</span><span class="sxs-lookup"><span data-stu-id="4e454-301">MyApp</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="4e454-302">如果您決定要在應用程式資料夾以外的位置中放置管線資料夾結構，您必須修改顯示在資料表中的對應路徑。</span><span class="sxs-lookup"><span data-stu-id="4e454-302">If you decided to put your pipeline folder structure in a location other than your application folder, you must modify the paths shown in the table accordingly.</span></span> <span data-ttu-id="4e454-303">請參閱中的管線目錄需求的討論[管線開發需求](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。</span><span class="sxs-lookup"><span data-stu-id="4e454-303">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
2.  <span data-ttu-id="4e454-304">建置 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="4e454-304">Build the Visual Studio solution.</span></span>  
  
3.  <span data-ttu-id="4e454-305">請檢查以確保組件已複製到正確的目錄，而且沒有額外的複製的組件已安裝不正確的資料夾中的應用程式和管線目錄。</span><span class="sxs-lookup"><span data-stu-id="4e454-305">Check the application and pipeline directories to ensure that the assemblies were copied to the correct directories and that no extra copies of assemblies were installed in the wrong folders.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4e454-306">如果您沒有變更**複製到本機**至**False**如`Calc1AddInView`專案中的參考`AddInCalcV1`專案中，載入器環境問題會造成增益集無法找到。</span><span class="sxs-lookup"><span data-stu-id="4e454-306">If you did not change **Copy Local** to **False** for the `Calc1AddInView` project reference in the `AddInCalcV1` project, loader context problems will prevent the add-in from being located.</span></span>  
  
     <span data-ttu-id="4e454-307">如需部署到管線的相關資訊，請參閱[管線開發需求](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。</span><span class="sxs-lookup"><span data-stu-id="4e454-307">For information about deploying to the pipeline, see [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
## <a name="running-the-host-application"></a><span data-ttu-id="4e454-308">執行主應用程式</span><span class="sxs-lookup"><span data-stu-id="4e454-308">Running the Host Application</span></span>  
 <span data-ttu-id="4e454-309">現在您已經準備好要執行主機及互動 增益集。</span><span class="sxs-lookup"><span data-stu-id="4e454-309">You are now ready to run the host and interact with the add-in.</span></span>  
  
#### <a name="to-run-the-host-application"></a><span data-ttu-id="4e454-310">執行主應用程式</span><span class="sxs-lookup"><span data-stu-id="4e454-310">To run the host application</span></span>  
  
1.  <span data-ttu-id="4e454-311">在命令提示字元中，移至應用程式目錄和執行主應用程式， `Calc1Host.exe`。</span><span class="sxs-lookup"><span data-stu-id="4e454-311">At the command prompt, go to the application directory and run the host application, `Calc1Host.exe`.</span></span>  
  
2.  <span data-ttu-id="4e454-312">主機會尋找其類型的所有可用增益，並提示您選取的增益集。</span><span class="sxs-lookup"><span data-stu-id="4e454-312">The host finds all available add-ins of its type and prompts you to select an add-in.</span></span> <span data-ttu-id="4e454-313">輸入**1**唯一可用的增益集。</span><span class="sxs-lookup"><span data-stu-id="4e454-313">Enter **1** for the only available add-in.</span></span>  
  
3.  <span data-ttu-id="4e454-314">輸入的方程式計算機，例如**2 + 2**。</span><span class="sxs-lookup"><span data-stu-id="4e454-314">Enter an equation for the calculator, such as **2 + 2**.</span></span> <span data-ttu-id="4e454-315">必須要有數字和運算子之間的空格。</span><span class="sxs-lookup"><span data-stu-id="4e454-315">There must be spaces between the numbers and the operator.</span></span>  
  
4.  <span data-ttu-id="4e454-316">型別**結束**按**Enter**鍵以關閉應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e454-316">Type **exit** and press the **Enter** key to close the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e454-317">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e454-317">See Also</span></span>  
 [<span data-ttu-id="4e454-318">逐步解說： 啟用主機變更為回溯相容性</span><span class="sxs-lookup"><span data-stu-id="4e454-318">Walkthrough: Enabling Backward Compatibility as Your Host Changes</span></span>](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [<span data-ttu-id="4e454-319">主控件與增益集之間的逐步解說： 傳遞集合</span><span class="sxs-lookup"><span data-stu-id="4e454-319">Walkthrough: Passing Collections Between Hosts and Add-Ins</span></span>](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [<span data-ttu-id="4e454-320">管線開發需求</span><span class="sxs-lookup"><span data-stu-id="4e454-320">Pipeline Development Requirements</span></span>](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [<span data-ttu-id="4e454-321">合約、 檢視和配接器</span><span class="sxs-lookup"><span data-stu-id="4e454-321">Contracts, Views, and Adapters</span></span>](http://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [<span data-ttu-id="4e454-322">管線開發</span><span class="sxs-lookup"><span data-stu-id="4e454-322">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)
