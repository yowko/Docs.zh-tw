---
title: 逐步解說：建立可延伸應用程式
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d2aaeaffaf3abbe1e8efcdb57d40e6ae60f89b5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080718"
---
# <a name="walkthrough-creating-an-extensible-application"></a><span data-ttu-id="8d66a-102">逐步解說：建立可延伸應用程式</span><span class="sxs-lookup"><span data-stu-id="8d66a-102">Walkthrough: Creating an Extensible Application</span></span>
<span data-ttu-id="8d66a-103">本逐步解說描述如何建立增益集執行簡單的計算機功能的管線。</span><span class="sxs-lookup"><span data-stu-id="8d66a-103">This walkthrough describes how to create a pipeline for an add-in that performs simple calculator functions.</span></span> <span data-ttu-id="8d66a-104">它不會示範真實世界的案例;相反地，它會示範管線和如何增益集可以提供服務主機的基本的功能。</span><span class="sxs-lookup"><span data-stu-id="8d66a-104">It does not demonstrate a real-world scenario; rather, it demonstrates the basic functionality of a pipeline and how an add-in can provide services for a host.</span></span>  
  
 <span data-ttu-id="8d66a-105">此逐步解說將說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="8d66a-105">This walkthrough describes the following tasks:</span></span>  
  
-   <span data-ttu-id="8d66a-106">建立 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-106">Creating a Visual Studio solution.</span></span>  
  
-   <span data-ttu-id="8d66a-107">建立管線目錄結構。</span><span class="sxs-lookup"><span data-stu-id="8d66a-107">Creating the pipeline directory structure.</span></span>  
  
-   <span data-ttu-id="8d66a-108">正在建立的合約和檢視表。</span><span class="sxs-lookup"><span data-stu-id="8d66a-108">Creating the contract and views.</span></span>  
  
-   <span data-ttu-id="8d66a-109">建立增益集端配接器。</span><span class="sxs-lookup"><span data-stu-id="8d66a-109">Creating the add-in-side adapter.</span></span>  
  
-   <span data-ttu-id="8d66a-110">建立主應用程式端配接器。</span><span class="sxs-lookup"><span data-stu-id="8d66a-110">Creating the host-side adapter.</span></span>  
  
-   <span data-ttu-id="8d66a-111">建立主應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d66a-111">Creating the host.</span></span>  
  
-   <span data-ttu-id="8d66a-112">建立增益集。</span><span class="sxs-lookup"><span data-stu-id="8d66a-112">Creating the add-in.</span></span>  
  
-   <span data-ttu-id="8d66a-113">部署管線。</span><span class="sxs-lookup"><span data-stu-id="8d66a-113">Deploying the pipeline.</span></span>  
  
-   <span data-ttu-id="8d66a-114">執行主應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d66a-114">Running the host application.</span></span>  
  
 <span data-ttu-id="8d66a-115">這個管線會將傳遞的可序列化的型別 (<xref:System.Double>和<xref:System.String>)、 主機和增益集之間。</span><span class="sxs-lookup"><span data-stu-id="8d66a-115">This pipeline passes only serializable types (<xref:System.Double> and <xref:System.String>), between the host and the add-in.</span></span> <span data-ttu-id="8d66a-116">如需示範如何將複雜資料型別集合的範例，請參閱[逐步解說： 將集合之間的主機和增益集](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-116">For an example that shows how to pass collections of complex data types, see [Walkthrough: Passing Collections Between Hosts and Add-Ins](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span></span>  
  
 <span data-ttu-id="8d66a-117">此管線的合約會定義四個數學運算的物件模型： 新增、 減、 乘、 和分割。</span><span class="sxs-lookup"><span data-stu-id="8d66a-117">The contract for this pipeline defines an object model of four arithmetic operations: add, subtract, multiply, and divide.</span></span> <span data-ttu-id="8d66a-118">與方程式來計算，例如 2 + 2，主機會提供增益集和增益集將結果傳回至主應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d66a-118">The host provides the add-in with an equation to calculate, such as 2 + 2, and the add-in returns the result to the host.</span></span>  
  
 <span data-ttu-id="8d66a-119">計算機增益集的第 2 版提供更多計算的可能性，並示範了版本控制。</span><span class="sxs-lookup"><span data-stu-id="8d66a-119">Version 2 of the calculator add-in provides more calculating possibilities and demonstrates versioning.</span></span> <span data-ttu-id="8d66a-120">所述[逐步解說： 為您的主機變更啟用回溯相容性](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-120">It is described in [Walkthrough: Enabling Backward Compatibility as Your Host Changes](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8d66a-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="8d66a-121">Prerequisites</span></span>  
 <span data-ttu-id="8d66a-122">您需要下列項目才能完成本逐步解說：</span><span class="sxs-lookup"><span data-stu-id="8d66a-122">You need the following to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="8d66a-123">Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8d66a-123">Visual Studio.</span></span>  
  
## <a name="creating-a-visual-studio-solution"></a><span data-ttu-id="8d66a-124">建立 Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="8d66a-124">Creating a Visual Studio Solution</span></span>  
 <span data-ttu-id="8d66a-125">使用 Visual Studio 中的解決方案，以包含您管線區段的專案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-125">Use a solution in Visual Studio to contain the projects of your pipeline segments.</span></span>  
  
#### <a name="to-create-the-pipeline-solution"></a><span data-ttu-id="8d66a-126">若要建立管線的方案</span><span class="sxs-lookup"><span data-stu-id="8d66a-126">To create the pipeline solution</span></span>  
  
1.  <span data-ttu-id="8d66a-127">在 Visual Studio 中建立新的專案，名為`Calc1Contract`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-127">In Visual Studio, create a new project named `Calc1Contract`.</span></span> <span data-ttu-id="8d66a-128">它的基礎**類別庫**範本。</span><span class="sxs-lookup"><span data-stu-id="8d66a-128">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="8d66a-129">將方案命名為`CalculatorV1`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-129">Name the solution `CalculatorV1`.</span></span>  
  
## <a name="creating-the-pipeline-directory-structure"></a><span data-ttu-id="8d66a-130">建立管線目錄結構</span><span class="sxs-lookup"><span data-stu-id="8d66a-130">Creating the Pipeline Directory Structure</span></span>  
 <span data-ttu-id="8d66a-131">增益集模型要求管線區段組件放在指定的目錄結構。</span><span class="sxs-lookup"><span data-stu-id="8d66a-131">The add-in model requires the pipeline segment assemblies to be placed in a specified directory structure.</span></span> <span data-ttu-id="8d66a-132">如需有關管線結構的詳細資訊，請參閱[管線開發需求](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-132">For more information about the pipeline structure, see [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
#### <a name="to-create-the-pipeline-directory-structure"></a><span data-ttu-id="8d66a-133">若要建立管線目錄結構</span><span class="sxs-lookup"><span data-stu-id="8d66a-133">To create the pipeline directory structure</span></span>  
  
1.  <span data-ttu-id="8d66a-134">在您的電腦上的任何位置建立應用程式資料夾。</span><span class="sxs-lookup"><span data-stu-id="8d66a-134">Create an application folder anywhere on your computer.</span></span>  
  
2.  <span data-ttu-id="8d66a-135">在該資料夾中，建立下列結構：</span><span class="sxs-lookup"><span data-stu-id="8d66a-135">In that folder, create the following structure:</span></span>  
  
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
  
     <span data-ttu-id="8d66a-136">不需要在您的應用程式的資料夾; 中放入管線資料夾結構此處作法僅是為了方便起見。</span><span class="sxs-lookup"><span data-stu-id="8d66a-136">It is not necessary to put the pipeline folder structure in your application folder; it is done here only for convenience.</span></span> <span data-ttu-id="8d66a-137">在適當的步驟，逐步解說會說明如何變更程式碼，如果管線資料夾結構是在不同的位置。</span><span class="sxs-lookup"><span data-stu-id="8d66a-137">At the appropriate step, the walkthrough explains how to change the code if the pipeline folder structure is in a different location.</span></span> <span data-ttu-id="8d66a-138">請參閱中的管線目錄需求的討論[管線開發需求](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-138">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8d66a-139">`CalcV2`資料夾不會用於本逐步解說，它是一個預留位置，如[逐步解說： 為您的主機變更啟用回溯相容性](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-139">The `CalcV2` folder is not used in this walkthrough; it is a placeholder for [Walkthrough: Enabling Backward Compatibility as Your Host Changes](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="creating-the-contract-and-views"></a><span data-ttu-id="8d66a-140">建立合約和檢視</span><span class="sxs-lookup"><span data-stu-id="8d66a-140">Creating the Contract and Views</span></span>  
 <span data-ttu-id="8d66a-141">此管線的合約區段會定義`ICalc1Contract`介面，定義四種方法： `add`， `subtract`， `multiply`，和`divide`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-141">The contract segment for this pipeline defines the `ICalc1Contract` interface, which defines four methods: `add`, `subtract`, `multiply`, and `divide`.</span></span>  
  
#### <a name="to-create-the-contract"></a><span data-ttu-id="8d66a-142">若要建立合約</span><span class="sxs-lookup"><span data-stu-id="8d66a-142">To create the contract</span></span>  
  
1.  <span data-ttu-id="8d66a-143">在 Visual Studio 方案中名為`CalculatorV1`，開啟`Calc1Contract`專案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-143">In the Visual Studio solution named `CalculatorV1`, open the `Calc1Contract` project.</span></span>  
  
2.  <span data-ttu-id="8d66a-144">在 [**方案總管] 中**，將參考加入至下列組件`Calc1Contract`專案：</span><span class="sxs-lookup"><span data-stu-id="8d66a-144">In **Solution Explorer**, add references to the following assemblies to the `Calc1Contract` project:</span></span>  
  
     <span data-ttu-id="8d66a-145">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="8d66a-145">System.AddIn.Contract.dll</span></span>  
  
     <span data-ttu-id="8d66a-146">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="8d66a-146">System.AddIn.dll</span></span>  
  
3.  <span data-ttu-id="8d66a-147">在 **方案總管**，排除新加入的預設類別**類別庫**專案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-147">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects.</span></span>  
  
4.  <span data-ttu-id="8d66a-148">在 **方案總管**，將新的項目新增至專案中，使用**介面**範本。</span><span class="sxs-lookup"><span data-stu-id="8d66a-148">In **Solution Explorer**, add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="8d66a-149">在 [**加入新項目**] 對話方塊中，介面名稱`ICalc1Contract`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-149">In the **Add New Item** dialog box, name the interface `ICalc1Contract`.</span></span>  
  
5.  <span data-ttu-id="8d66a-150">在介面檔案中加入命名空間的參考<xref:System.AddIn.Contract>和<xref:System.AddIn.Pipeline>。</span><span class="sxs-lookup"><span data-stu-id="8d66a-150">In the interface file, add namespace references to <xref:System.AddIn.Contract> and <xref:System.AddIn.Pipeline>.</span></span>  
  
6.  <span data-ttu-id="8d66a-151">您可以使用下列程式碼來完成此合約區段。</span><span class="sxs-lookup"><span data-stu-id="8d66a-151">Use the following code to complete this contract segment.</span></span> <span data-ttu-id="8d66a-152">請注意，此介面必須<xref:System.AddIn.Pipeline.AddInContractAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="8d66a-152">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInContractAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  <span data-ttu-id="8d66a-153">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-153">Optionally, build the Visual Studio solution.</span></span> <span data-ttu-id="8d66a-154">方案無法執行，直到最後的程序，但每個程序可確保每個專案之後，請建置它修正。</span><span class="sxs-lookup"><span data-stu-id="8d66a-154">The solution cannot be run until the final procedure, but building it after each procedure ensures that each project is correct.</span></span>  
  
 <span data-ttu-id="8d66a-155">由於增益集 檢視和主應用程式檢視的增益集通常會有相同的程式碼，尤其是在增益集的第一個版本，您可以輕鬆在同一時間建立檢視。</span><span class="sxs-lookup"><span data-stu-id="8d66a-155">Because the add-in view and the host view of the add-in usually have the same code, especially in the first version of an add-in, you can easily create the views at the same time.</span></span> <span data-ttu-id="8d66a-156">它們只能有一個因數的差異： 增益集檢視需要<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性，而主應用程式檢視的增益集不需要任何屬性。</span><span class="sxs-lookup"><span data-stu-id="8d66a-156">They differ by only one factor: the add-in view requires the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute, while the host view of the add-in does not require any attributes.</span></span>  
  
#### <a name="to-create-the-add-in-view"></a><span data-ttu-id="8d66a-157">若要建立增益集檢視</span><span class="sxs-lookup"><span data-stu-id="8d66a-157">To create the add-in view</span></span>  
  
1.  <span data-ttu-id="8d66a-158">加入新的專案，名為`Calc1AddInView`至`CalculatorV1`解決方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-158">Add a new project named `Calc1AddInView` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="8d66a-159">它的基礎**類別庫**範本。</span><span class="sxs-lookup"><span data-stu-id="8d66a-159">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="8d66a-160">在 **方案總管**，將參考加入至 System.AddIn.dll`Calc1AddInView`專案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-160">In **Solution Explorer**, add a reference to System.AddIn.dll to the `Calc1AddInView` project.</span></span>  
  
3.  <span data-ttu-id="8d66a-161">在 [**方案總管] 中**，排除新加入的預設類別**類別庫**專案，並將新的項目新增至專案中，使用**介面**範本。</span><span class="sxs-lookup"><span data-stu-id="8d66a-161">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="8d66a-162">在 [**加入新項目**] 對話方塊中，介面名稱`ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-162">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
4.  <span data-ttu-id="8d66a-163">在介面檔案中新增的命名空間參考<xref:System.AddIn.Pipeline>。</span><span class="sxs-lookup"><span data-stu-id="8d66a-163">In the interface file, add a namespace reference to <xref:System.AddIn.Pipeline>.</span></span>  
  
5.  <span data-ttu-id="8d66a-164">您可以使用下列程式碼來完成此增益集檢視。</span><span class="sxs-lookup"><span data-stu-id="8d66a-164">Use the following code to complete this add-in view.</span></span> <span data-ttu-id="8d66a-165">請注意，此介面必須<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="8d66a-165">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  <span data-ttu-id="8d66a-166">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-166">Optionally, build the Visual Studio solution.</span></span>  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a><span data-ttu-id="8d66a-167">若要建立的增益集的 [主機] 檢視</span><span class="sxs-lookup"><span data-stu-id="8d66a-167">To create the host view of the add-in</span></span>  
  
1.  <span data-ttu-id="8d66a-168">加入新的專案，名為`Calc1HVA`至`CalculatorV1`解決方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-168">Add a new project named `Calc1HVA` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="8d66a-169">它的基礎**類別庫**範本。</span><span class="sxs-lookup"><span data-stu-id="8d66a-169">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="8d66a-170">在 [**方案總管] 中**，排除新加入的預設類別**類別庫**專案，並將新的項目新增至專案中，使用**介面**範本。</span><span class="sxs-lookup"><span data-stu-id="8d66a-170">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="8d66a-171">在 [**加入新項目**] 對話方塊中，介面名稱`ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-171">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
3.  <span data-ttu-id="8d66a-172">在介面檔案中，使用下列程式碼來完成增益集的 [主機] 檢視。</span><span class="sxs-lookup"><span data-stu-id="8d66a-172">In the interface file, use the following code to complete the host view of the add-in.</span></span>  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  <span data-ttu-id="8d66a-173">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-173">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in-side-adapter"></a><span data-ttu-id="8d66a-174">建立增益集端配接器</span><span class="sxs-lookup"><span data-stu-id="8d66a-174">Creating the Add-in-side Adapter</span></span>  
 <span data-ttu-id="8d66a-175">此增益集端配接器是由一個檢視至合約配接器所組成。</span><span class="sxs-lookup"><span data-stu-id="8d66a-175">This add-in-side adapter consists of one view-to-contract adapter.</span></span> <span data-ttu-id="8d66a-176">此管線區段會轉換的類型從增益集檢視的合約。</span><span class="sxs-lookup"><span data-stu-id="8d66a-176">This pipeline segment converts the types from the add-in view to the contract.</span></span>  
  
 <span data-ttu-id="8d66a-177">在此管線中，增益集提供服務給主機，及類型流程從增益集主應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d66a-177">In this pipeline, the add-in provides a service to the host, and the types flow from the add-in to the host.</span></span> <span data-ttu-id="8d66a-178">由於沒有型別從主機到增益集，您不必包含在此管線的增益集端上的合約至檢視配接器。</span><span class="sxs-lookup"><span data-stu-id="8d66a-178">Because no types flow from the host to the add-in, you do not have to include a contract-to-view adapter on the add-in side of this pipeline.</span></span>  
  
#### <a name="to-create-the-add-in-side-adapter"></a><span data-ttu-id="8d66a-179">若要建立增益集端配接器</span><span class="sxs-lookup"><span data-stu-id="8d66a-179">To create the add-in-side adapter</span></span>  
  
1.  <span data-ttu-id="8d66a-180">加入新的專案，名為`Calc1AddInSideAdapter`至`CalculatorV1`解決方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-180">Add a new project named `Calc1AddInSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="8d66a-181">它的基礎**類別庫**範本。</span><span class="sxs-lookup"><span data-stu-id="8d66a-181">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="8d66a-182">在 [**方案總管] 中**，將參考加入至下列組件`Calc1AddInSideAdapter`專案：</span><span class="sxs-lookup"><span data-stu-id="8d66a-182">In **Solution Explorer**, add references to the following assemblies to the `Calc1AddInSideAdapter` project:</span></span>  
  
     <span data-ttu-id="8d66a-183">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="8d66a-183">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="8d66a-184">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="8d66a-184">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="8d66a-185">將專案參考加入專案相鄰的管線區段：</span><span class="sxs-lookup"><span data-stu-id="8d66a-185">Add project references to the projects for the adjacent pipeline segments:</span></span>  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  <span data-ttu-id="8d66a-186">選取每個專案參考，然後在**屬性**設定**複製到本機**來**False**。</span><span class="sxs-lookup"><span data-stu-id="8d66a-186">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="8d66a-187">在 Visual Basic 中使用**參考**索引標籤**專案屬性**設**複製到本機**至**False**為兩個專案參考。</span><span class="sxs-lookup"><span data-stu-id="8d66a-187">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="8d66a-188">重新命名專案的預設類別`CalculatorViewToContractAddInSideAdapter`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-188">Rename the project's default class `CalculatorViewToContractAddInSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="8d66a-189">在類別檔案中，加入命名空間參考<xref:System.AddIn.Pipeline>。</span><span class="sxs-lookup"><span data-stu-id="8d66a-189">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="8d66a-190">在類別檔案中，加入相鄰的區段的命名空間參考：`CalcAddInViews`和`CalculatorContracts`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-190">In the class file, add namespace references for the adjacent segments: `CalcAddInViews` and `CalculatorContracts`.</span></span> <span data-ttu-id="8d66a-191">(在 Visual Basic 中為這些命名空間參考`Calc1AddInView.CalcAddInViews`和`Calc1Contract.CalculatorContracts`，除非您已在 Visual Basic 專案中關閉預設的命名空間。)</span><span class="sxs-lookup"><span data-stu-id="8d66a-191">(In Visual Basic, these namespace references are `Calc1AddInView.CalcAddInViews` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="8d66a-192">適用於<xref:System.AddIn.Pipeline.AddInAdapterAttribute>屬性設定為`CalculatorViewToContractAddInSideAdapter`類別，將其識別為增益集端配接器。</span><span class="sxs-lookup"><span data-stu-id="8d66a-192">Apply the <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute to the `CalculatorViewToContractAddInSideAdapter` class, to identify it as the add-in-side adapter.</span></span>  
  
9. <span data-ttu-id="8d66a-193">製作`CalculatorViewToContractAddInSideAdapter`類別繼承<xref:System.AddIn.Pipeline.ContractBase>，以提供的預設實作<xref:System.AddIn.Contract.IContract>介面，並實作合約介面，將管線`ICalc1Contract`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-193">Make the `CalculatorViewToContractAddInSideAdapter` class inherit <xref:System.AddIn.Pipeline.ContractBase>, which provides a default implementation of the <xref:System.AddIn.Contract.IContract> interface, and implement the contract interface for the pipeline, `ICalc1Contract`.</span></span>  
  
10. <span data-ttu-id="8d66a-194">新增公用建構函式可接受`ICalculator`，在私用欄位中，將其快取，並呼叫基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="8d66a-194">Add a public constructor that accepts an `ICalculator`, caches it in a private field, and calls the base class constructor.</span></span>  
  
11. <span data-ttu-id="8d66a-195">若要實作的成員`ICalc1Contract`，只要呼叫的對應成員`ICalculator`會傳遞至建構函式，並傳回結果的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d66a-195">To implement the members of `ICalc1Contract`, simply call the corresponding members of the `ICalculator` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="8d66a-196">這會適應檢視 (`ICalculator`) 的合約 (`ICalc1Contract`)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-196">This adapts the view (`ICalculator`) to the contract (`ICalc1Contract`).</span></span>  
  
     <span data-ttu-id="8d66a-197">下列程式碼會顯示已完成的增益集端配接器。</span><span class="sxs-lookup"><span data-stu-id="8d66a-197">The following code shows the completed add-in-side adapter.</span></span>  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. <span data-ttu-id="8d66a-198">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-198">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host-side-adapter"></a><span data-ttu-id="8d66a-199">建立主應用程式端配接器</span><span class="sxs-lookup"><span data-stu-id="8d66a-199">Creating the Host-side Adapter</span></span>  
 <span data-ttu-id="8d66a-200">這個主應用程式端配接器是由一個合約至檢視配接器所組成。</span><span class="sxs-lookup"><span data-stu-id="8d66a-200">This host-side adapter consists of one contract-to-view adapter.</span></span> <span data-ttu-id="8d66a-201">此區段會適應增益集的 [主機] 檢視的合約。</span><span class="sxs-lookup"><span data-stu-id="8d66a-201">This segment adapts the contract to the host view of the add-in.</span></span>  
  
 <span data-ttu-id="8d66a-202">在此管線中，增益集提供服務主機和類型的流程從增益集主應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d66a-202">In this pipeline, the add-in provides a service to the host and the types flow from the add-in to the host.</span></span> <span data-ttu-id="8d66a-203">由於沒有型別從主機到增益集，您不必包含檢視至合約配接器。</span><span class="sxs-lookup"><span data-stu-id="8d66a-203">Because no types flow from the host to the add-in, you do not have to include a view-to-contract adapter.</span></span>  
  
 <span data-ttu-id="8d66a-204">若要實作存留期管理，請使用<xref:System.AddIn.Pipeline.ContractHandle>將存留期語彙基元新增至合約的物件。</span><span class="sxs-lookup"><span data-stu-id="8d66a-204">To implement lifetime management, use a <xref:System.AddIn.Pipeline.ContractHandle> object to attach a lifetime token to the contract.</span></span> <span data-ttu-id="8d66a-205">為了讓工作的存留期管理，您必須保持此控制代碼的參考。</span><span class="sxs-lookup"><span data-stu-id="8d66a-205">You must keep a reference to this handle in order for lifetime management to work.</span></span> <span data-ttu-id="8d66a-206">套用權杖之後，任何其他的程式設計需要不，因為增益集系統可處置物件時不會再使用，讓它們可供記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="8d66a-206">After the token is applied, no additional programming is required because the add-in system can dispose of objects when they are no longer being used and make them available for garbage collection.</span></span> <span data-ttu-id="8d66a-207">如需詳細資訊，請參閱 <<c0> [ 存留期管理](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-207">For more information, see [Lifetime Management](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
#### <a name="to-create-the-host-side-adapter"></a><span data-ttu-id="8d66a-208">若要建立主應用程式端配接器</span><span class="sxs-lookup"><span data-stu-id="8d66a-208">To create the host-side adapter</span></span>  
  
1.  <span data-ttu-id="8d66a-209">加入新的專案，名為`Calc1HostSideAdapter`至`CalculatorV1`解決方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-209">Add a new project named `Calc1HostSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="8d66a-210">它的基礎**類別庫**範本。</span><span class="sxs-lookup"><span data-stu-id="8d66a-210">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="8d66a-211">在 [**方案總管] 中**，將參考加入至下列組件`Calc1HostSideAdapter`專案：</span><span class="sxs-lookup"><span data-stu-id="8d66a-211">In **Solution Explorer**, add references to the following assemblies to the `Calc1HostSideAdapter` project:</span></span>  
  
     <span data-ttu-id="8d66a-212">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="8d66a-212">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="8d66a-213">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="8d66a-213">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="8d66a-214">將專案參考加入專案相鄰的區段：</span><span class="sxs-lookup"><span data-stu-id="8d66a-214">Add project references to the projects for the adjacent segments:</span></span>  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  <span data-ttu-id="8d66a-215">選取每個專案參考，然後在**屬性**設定**複製到本機**來**False**。</span><span class="sxs-lookup"><span data-stu-id="8d66a-215">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="8d66a-216">在 Visual Basic 中使用**參考**索引標籤**專案屬性**設**複製到本機**至**False**為兩個專案參考。</span><span class="sxs-lookup"><span data-stu-id="8d66a-216">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="8d66a-217">重新命名專案的預設類別`CalculatorContractToViewHostSideAdapter`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-217">Rename the project's default class `CalculatorContractToViewHostSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="8d66a-218">在類別檔案中，加入命名空間參考<xref:System.AddIn.Pipeline>。</span><span class="sxs-lookup"><span data-stu-id="8d66a-218">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="8d66a-219">在類別檔案中，加入相鄰的區段的命名空間參考：`CalcHVAs`和`CalculatorContracts`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-219">In the class file, add namespace references for the adjacent segments: `CalcHVAs` and `CalculatorContracts`.</span></span> <span data-ttu-id="8d66a-220">(在 Visual Basic 中為這些命名空間參考`Calc1HVA.CalcHVAs`和`Calc1Contract.CalculatorContracts`，除非您已在 Visual Basic 專案中關閉預設的命名空間。)</span><span class="sxs-lookup"><span data-stu-id="8d66a-220">(In Visual Basic, these namespace references are `Calc1HVA.CalcHVAs` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="8d66a-221">適用於<xref:System.AddIn.Pipeline.HostAdapterAttribute>屬性設定為`CalculatorContractToViewHostSideAdapter`類別，將其識別為主應用程式端配接器區段。</span><span class="sxs-lookup"><span data-stu-id="8d66a-221">Apply the <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribute to the `CalculatorContractToViewHostSideAdapter` class, to identify it as the host-side adapter segment.</span></span>  
  
9. <span data-ttu-id="8d66a-222">製作`CalculatorContractToViewHostSideAdapter`類別實作介面，代表增益集的 [主機] 檢視： `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-222">Make the `CalculatorContractToViewHostSideAdapter` class implement the interface that represents the host view of the add-in: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` in Visual Basic).</span></span>  
  
10. <span data-ttu-id="8d66a-223">新增公用建構函式可接受管線的合約型別， `ICalc1Contract`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-223">Add a public constructor that accepts the pipeline contract type, `ICalc1Contract`.</span></span> <span data-ttu-id="8d66a-224">建構函式必須快取之合約的參考。</span><span class="sxs-lookup"><span data-stu-id="8d66a-224">The constructor must cache the reference to the contract.</span></span> <span data-ttu-id="8d66a-225">它也必須建立並快取新<xref:System.AddIn.Pipeline.ContractHandle>合約，若要管理的增益集的存留期。</span><span class="sxs-lookup"><span data-stu-id="8d66a-225">It must also create and cache a new <xref:System.AddIn.Pipeline.ContractHandle> for the contract, to manage the lifetime of the add-in.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8d66a-226"><xref:System.AddIn.Pipeline.ContractHandle>務必存留期管理。</span><span class="sxs-lookup"><span data-stu-id="8d66a-226">The <xref:System.AddIn.Pipeline.ContractHandle> is critical to lifetime management.</span></span> <span data-ttu-id="8d66a-227">如果您無法將參考<xref:System.AddIn.Pipeline.ContractHandle>物件，記憶體回收會回收，而且管線時您的程式不會預期它將會關機。</span><span class="sxs-lookup"><span data-stu-id="8d66a-227">If you fail to keep a reference to the <xref:System.AddIn.Pipeline.ContractHandle> object, garbage collection will reclaim it, and the pipeline will shut down when your program does not expect it.</span></span> <span data-ttu-id="8d66a-228">這可能會導致很難進行診斷，這類的錯誤<xref:System.AppDomainUnloadedException>。</span><span class="sxs-lookup"><span data-stu-id="8d66a-228">This can lead to errors that are difficult to diagnose, such as <xref:System.AppDomainUnloadedException>.</span></span> <span data-ttu-id="8d66a-229">關閉是管線的正常，生命週期階段，因此沒有任何方法來偵測這種情況，會產生錯誤的存留期管理程式碼。</span><span class="sxs-lookup"><span data-stu-id="8d66a-229">Shutdown is a normal stage in the life of a pipeline, so there is no way for the lifetime management code to detect that this condition is an error.</span></span>  
  
11. <span data-ttu-id="8d66a-230">若要實作的成員`ICalculator`，只要呼叫的對應成員`ICalc1Contract`會傳遞至建構函式，並傳回結果的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d66a-230">To implement the members of `ICalculator`, simply call the corresponding members of the `ICalc1Contract` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="8d66a-231">這會適應合約 (`ICalc1Contract`) 來檢視 (`ICalculator`)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-231">This adapts the contract (`ICalc1Contract`) to the view (`ICalculator`).</span></span>  
  
     <span data-ttu-id="8d66a-232">下列程式碼會顯示已完成的主應用程式端配接器。</span><span class="sxs-lookup"><span data-stu-id="8d66a-232">The following code shows the completed host-side adapter.</span></span>  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. <span data-ttu-id="8d66a-233">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-233">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host"></a><span data-ttu-id="8d66a-234">建立主應用程式</span><span class="sxs-lookup"><span data-stu-id="8d66a-234">Creating the Host</span></span>  
 <span data-ttu-id="8d66a-235">主應用程式互動的增益集透過增益集的 [主機] 檢視。</span><span class="sxs-lookup"><span data-stu-id="8d66a-235">A host application interacts with the add-in through the host view of the add-in.</span></span> <span data-ttu-id="8d66a-236">它會使用增益集探索和啟動方法所提供<xref:System.AddIn.Hosting.AddInStore>和<xref:System.AddIn.Hosting.AddInToken>類別來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8d66a-236">It uses add-in discovery and activation methods provided by the <xref:System.AddIn.Hosting.AddInStore> and <xref:System.AddIn.Hosting.AddInToken> classes to do the following:</span></span>  
  
-   <span data-ttu-id="8d66a-237">更新快取的管線和增益集的資訊。</span><span class="sxs-lookup"><span data-stu-id="8d66a-237">Update the cache of pipeline and add-in information.</span></span>  
  
-   <span data-ttu-id="8d66a-238">尋找增益集主應用程式檢視型別， `ICalculator`，指定的管線的根目錄下。</span><span class="sxs-lookup"><span data-stu-id="8d66a-238">Find add-ins of the host view type, `ICalculator`, under the specified pipeline root directory.</span></span>  
  
-   <span data-ttu-id="8d66a-239">提示使用者指定的增益集使用。</span><span class="sxs-lookup"><span data-stu-id="8d66a-239">Prompt the user to specify which add-in to use.</span></span>  
  
-   <span data-ttu-id="8d66a-240">啟用所選增益集在新的應用程式定義域，以指定的安全性信任層級。</span><span class="sxs-lookup"><span data-stu-id="8d66a-240">Activate the selected add-in in a new application domain with a specified security trust level.</span></span>  
  
-   <span data-ttu-id="8d66a-241">執行自訂`RunCalculator`方法，它會呼叫增益集的增益集的 [主機] 檢視所指定的方法。</span><span class="sxs-lookup"><span data-stu-id="8d66a-241">Run the custom `RunCalculator` method, which calls the add-in's methods as specified by the host view of the add-in.</span></span>  
  
#### <a name="to-create-the-host"></a><span data-ttu-id="8d66a-242">若要建立主應用程式</span><span class="sxs-lookup"><span data-stu-id="8d66a-242">To create the host</span></span>  
  
1.  <span data-ttu-id="8d66a-243">加入新的專案，名為`Calc1Host`至`CalculatorV1`解決方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-243">Add a new project named `Calc1Host` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="8d66a-244">它的基礎**主控台應用程式**範本。</span><span class="sxs-lookup"><span data-stu-id="8d66a-244">Base it on the **Console Application** template.</span></span>  
  
2.  <span data-ttu-id="8d66a-245">在 [**方案總管] 中**，將參考加入 System.AddIn.dll 組件，以`Calc1Host`專案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-245">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the `Calc1Host` project.</span></span>  
  
3.  <span data-ttu-id="8d66a-246">加入專案參考`Calc1HVA`專案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-246">Add a project reference to the `Calc1HVA` project.</span></span> <span data-ttu-id="8d66a-247">選取該專案的參考，然後在**屬性**設定**複製到本機**來**False**。</span><span class="sxs-lookup"><span data-stu-id="8d66a-247">Select the project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="8d66a-248">在 Visual Basic 中使用**參考**索引標籤**專案屬性**設**複製到本機**至**False**。</span><span class="sxs-lookup"><span data-stu-id="8d66a-248">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False**.</span></span>  
  
4.  <span data-ttu-id="8d66a-249">重新命名類別檔案 （在 Visual Basic 中的模組） `MathHost1`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-249">Rename the class file (module in Visual Basic) `MathHost1`.</span></span>  
  
5.  <span data-ttu-id="8d66a-250">在 Visual Basic 中使用**應用程式**索引標籤**專案屬性**對話方塊，即可設定**啟始物件**至**Sub Main**。</span><span class="sxs-lookup"><span data-stu-id="8d66a-250">In Visual Basic, use the **Application** tab of the **Project Properties** dialog box to set **Startup object** to **Sub Main**.</span></span>  
  
6.  <span data-ttu-id="8d66a-251">在類別或模組檔案中新增的命名空間參考<xref:System.AddIn.Hosting>。</span><span class="sxs-lookup"><span data-stu-id="8d66a-251">In the class or module file, add a namespace reference to <xref:System.AddIn.Hosting>.</span></span>  
  
7.  <span data-ttu-id="8d66a-252">在類別或模組檔案中，加入 增益集的 主機 檢視的命名空間參考： `CalcHVAs`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-252">In the class or module file, add a namespace reference for the host view of the add-in: `CalcHVAs`.</span></span> <span data-ttu-id="8d66a-253">(在 Visual Basic 中為此命名空間參考`Calc1HVA.CalcHVAs`，除非您已在 Visual Basic 專案中關閉預設的命名空間。)</span><span class="sxs-lookup"><span data-stu-id="8d66a-253">(In Visual Basic, this namespace reference is `Calc1HVA.CalcHVAs`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="8d66a-254">中**方案總管**，選取方案並從**專案**功能表中選擇 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="8d66a-254">In **Solution Explorer**, select the solution and from the **Project** menu choose **Properties**.</span></span> <span data-ttu-id="8d66a-255">在 [**方案屬性頁**] 對話方塊中，將**單一啟始專案**是這個主應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-255">In the **Solution Property Pages** dialog box, set the **Single Startup Project** to be this host application project.</span></span>  
  
9. <span data-ttu-id="8d66a-256">在類別或模組檔案中，使用<xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType>方法來更新快取。</span><span class="sxs-lookup"><span data-stu-id="8d66a-256">In the class or module file, use the <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> method to update the cache.</span></span> <span data-ttu-id="8d66a-257">使用 <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType>方法來取得語彙基元的集合，並使用<xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType>方法來啟動增益集。</span><span class="sxs-lookup"><span data-stu-id="8d66a-257">Use the <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> method to get a collection of tokens, and use the <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> method to activate an add-in.</span></span>  
  
     <span data-ttu-id="8d66a-258">下列程式碼會顯示已完成的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d66a-258">The following code shows the completed host application.</span></span>  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="8d66a-259">此程式碼會假設管線資料夾結構位於應用程式資料夾中。</span><span class="sxs-lookup"><span data-stu-id="8d66a-259">This code assumes that the pipeline folder structure is located in the application folder.</span></span> <span data-ttu-id="8d66a-260">如果您位於其他地方，變更設定的程式碼行`addInRoot`變數，使該變數包含您管線目錄結構的路徑。</span><span class="sxs-lookup"><span data-stu-id="8d66a-260">If you located it elsewhere, change the line of code that sets the `addInRoot` variable, so that the variable contains the path to your pipeline directory structure.</span></span>  
  
     <span data-ttu-id="8d66a-261">此程式碼使用`ChooseCalculator`方法清單的權杖，並提示使用者選擇增益集。</span><span class="sxs-lookup"><span data-stu-id="8d66a-261">The code uses a `ChooseCalculator` method to list the tokens and to prompt the user to choose an add-in.</span></span> <span data-ttu-id="8d66a-262">`RunCalculator`方法提示使用者提供簡單的數學運算式，會使用運算式的剖析`Parser`類別，而且會顯示增益集所傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="8d66a-262">The `RunCalculator` method prompts the user for simple math expressions, parses the expressions using the `Parser` class, and displays the results returned by the add-in.</span></span>  
  
10. <span data-ttu-id="8d66a-263">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-263">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in"></a><span data-ttu-id="8d66a-264">建立增益集</span><span class="sxs-lookup"><span data-stu-id="8d66a-264">Creating the Add-In</span></span>  
 <span data-ttu-id="8d66a-265">增益集實作增益集檢視所指定的方法。</span><span class="sxs-lookup"><span data-stu-id="8d66a-265">An add-in implements the methods specified by the add-in view.</span></span> <span data-ttu-id="8d66a-266">此增益集實作`Add`， `Subtract`， `Multiply`，和`Divide`作業並將結果傳回到主應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d66a-266">This add-in implements the `Add`, `Subtract`, `Multiply`, and `Divide` operations and returns the results to the host.</span></span>  
  
#### <a name="to-create-the-add-in"></a><span data-ttu-id="8d66a-267">若要建立增益集</span><span class="sxs-lookup"><span data-stu-id="8d66a-267">To create the add-in</span></span>  
  
1.  <span data-ttu-id="8d66a-268">加入新的專案，名為`AddInCalcV1`至`CalculatorV1`解決方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-268">Add a new project named `AddInCalcV1` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="8d66a-269">它的基礎**類別庫**範本。</span><span class="sxs-lookup"><span data-stu-id="8d66a-269">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="8d66a-270">在 [**方案總管] 中**，System.AddIn.dll 組件的參考加入專案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-270">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the project.</span></span>  
  
3.  <span data-ttu-id="8d66a-271">加入專案參考`Calc1AddInView`專案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-271">Add a project reference to the `Calc1AddInView` project.</span></span> <span data-ttu-id="8d66a-272">選取該專案的參考，然後在**屬性**，將**複製到本機**來**False**。</span><span class="sxs-lookup"><span data-stu-id="8d66a-272">Select the project reference, and in **Properties**, set **Copy Local** to **False**.</span></span> <span data-ttu-id="8d66a-273">在 Visual Basic 中使用**參考**索引標籤**專案屬性**設**複製到本機**至**False**專案參考。</span><span class="sxs-lookup"><span data-stu-id="8d66a-273">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the project reference.</span></span>  
  
4.  <span data-ttu-id="8d66a-274">將類別重新命名`AddInCalcV1`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-274">Rename the class `AddInCalcV1`.</span></span>  
  
5.  <span data-ttu-id="8d66a-275">在類別檔案中新增的命名空間參考<xref:System.AddIn>與增益集檢視區段： `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-275">In the class file, add a namespace reference to <xref:System.AddIn> and the add-in view segment: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` in Visual Basic).</span></span>  
  
6.  <span data-ttu-id="8d66a-276">適用於<xref:System.AddIn.AddInAttribute>屬性設定為`AddInCalcV1`類別，以將類別識別為增益集。</span><span class="sxs-lookup"><span data-stu-id="8d66a-276">Apply the <xref:System.AddIn.AddInAttribute> attribute to the `AddInCalcV1` class, to identify the class as an add-in.</span></span>  
  
7.  <span data-ttu-id="8d66a-277">製作`AddInCalcV1`類別實作代表增益集檢視的介面： `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-277">Make the `AddInCalcV1` class implement the interface that represents the add-in view: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` in Visual Basic).</span></span>  
  
8.  <span data-ttu-id="8d66a-278">實作的成員`ICalculator`藉由傳回適當的計算的結果。</span><span class="sxs-lookup"><span data-stu-id="8d66a-278">Implement the members of `ICalculator` by returning the results of the appropriate calculations.</span></span>  
  
     <span data-ttu-id="8d66a-279">下列程式碼顯示已完成的增益集。</span><span class="sxs-lookup"><span data-stu-id="8d66a-279">The following code shows the completed add-in.</span></span>  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. <span data-ttu-id="8d66a-280">（選擇性） 建置的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-280">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="deploying-the-pipeline"></a><span data-ttu-id="8d66a-281">部署管線</span><span class="sxs-lookup"><span data-stu-id="8d66a-281">Deploying the Pipeline</span></span>  
 <span data-ttu-id="8d66a-282">您現在已準備好建置及部署必要的管線目錄結構的增益集的區段。</span><span class="sxs-lookup"><span data-stu-id="8d66a-282">You are now ready to build and deploy the add-in segments to the required pipeline directory structure.</span></span>  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a><span data-ttu-id="8d66a-283">將區段部署至管線</span><span class="sxs-lookup"><span data-stu-id="8d66a-283">To deploy the segments to the pipeline</span></span>  
  
1.  <span data-ttu-id="8d66a-284">在方案中每個專案都使用**建置**索引標籤**專案屬性**(**編譯** 索引標籤，在 Visual Basic 中的) 設定的值**輸出路徑** (**建置輸出路徑**Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-284">For each project in the solution, use the **Build** tab of **Project Properties** (the **Compile** tab in Visual Basic) to set the value of the **Output path** (the **Build output path** in Visual Basic).</span></span> <span data-ttu-id="8d66a-285">如果您已命名為您的應用程式資料夾`MyApp`，比方說，您的專案會建置到下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="8d66a-285">If you named your application folder `MyApp`, for example, your projects would build into the following folders:</span></span>  
  
    |<span data-ttu-id="8d66a-286">專案</span><span class="sxs-lookup"><span data-stu-id="8d66a-286">Project</span></span>|<span data-ttu-id="8d66a-287">路徑</span><span class="sxs-lookup"><span data-stu-id="8d66a-287">Path</span></span>|  
    |-------------|----------|  
    |<span data-ttu-id="8d66a-288">AddInCalcV1</span><span class="sxs-lookup"><span data-stu-id="8d66a-288">AddInCalcV1</span></span>|<span data-ttu-id="8d66a-289">MyApp\Pipeline\AddIns\CalcV1</span><span class="sxs-lookup"><span data-stu-id="8d66a-289">MyApp\Pipeline\AddIns\CalcV1</span></span>|  
    |<span data-ttu-id="8d66a-290">Calc1AddInSideAdapter</span><span class="sxs-lookup"><span data-stu-id="8d66a-290">Calc1AddInSideAdapter</span></span>|<span data-ttu-id="8d66a-291">MyApp\Pipeline\AddInSideAdapters</span><span class="sxs-lookup"><span data-stu-id="8d66a-291">MyApp\Pipeline\AddInSideAdapters</span></span>|  
    |<span data-ttu-id="8d66a-292">Calc1AddInView</span><span class="sxs-lookup"><span data-stu-id="8d66a-292">Calc1AddInView</span></span>|<span data-ttu-id="8d66a-293">MyApp\Pipeline\AddInViews</span><span class="sxs-lookup"><span data-stu-id="8d66a-293">MyApp\Pipeline\AddInViews</span></span>|  
    |<span data-ttu-id="8d66a-294">Calc1Contract</span><span class="sxs-lookup"><span data-stu-id="8d66a-294">Calc1Contract</span></span>|<span data-ttu-id="8d66a-295">MyApp\Pipeline\Contracts</span><span class="sxs-lookup"><span data-stu-id="8d66a-295">MyApp\Pipeline\Contracts</span></span>|  
    |<span data-ttu-id="8d66a-296">Calc1Host</span><span class="sxs-lookup"><span data-stu-id="8d66a-296">Calc1Host</span></span>|<span data-ttu-id="8d66a-297">MyApp</span><span class="sxs-lookup"><span data-stu-id="8d66a-297">MyApp</span></span>|  
    |<span data-ttu-id="8d66a-298">Calc1HostSideAdapter</span><span class="sxs-lookup"><span data-stu-id="8d66a-298">Calc1HostSideAdapter</span></span>|<span data-ttu-id="8d66a-299">MyApp\Pipeline\HostSideAdapters</span><span class="sxs-lookup"><span data-stu-id="8d66a-299">MyApp\Pipeline\HostSideAdapters</span></span>|  
    |<span data-ttu-id="8d66a-300">Calc1HVA</span><span class="sxs-lookup"><span data-stu-id="8d66a-300">Calc1HVA</span></span>|<span data-ttu-id="8d66a-301">MyApp</span><span class="sxs-lookup"><span data-stu-id="8d66a-301">MyApp</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="8d66a-302">如果您決定要將您的管線資料夾結構放在您的應用程式資料夾以外的位置，您必須修改資料表中顯示的對應路徑。</span><span class="sxs-lookup"><span data-stu-id="8d66a-302">If you decided to put your pipeline folder structure in a location other than your application folder, you must modify the paths shown in the table accordingly.</span></span> <span data-ttu-id="8d66a-303">請參閱中的管線目錄需求的討論[管線開發需求](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-303">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
2.  <span data-ttu-id="8d66a-304">建置 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="8d66a-304">Build the Visual Studio solution.</span></span>  
  
3.  <span data-ttu-id="8d66a-305">請檢查以確保組件已複製到正確的目錄，而且沒有額外的複本，組件已安裝錯誤的資料夾中的應用程式和管線的目錄。</span><span class="sxs-lookup"><span data-stu-id="8d66a-305">Check the application and pipeline directories to ensure that the assemblies were copied to the correct directories and that no extra copies of assemblies were installed in the wrong folders.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8d66a-306">如果您沒有變更**複製到本機**要**False** for`Calc1AddInView`專案中的參考`AddInCalcV1`專案中，載入器內容的問題會阻礙增益集位於。</span><span class="sxs-lookup"><span data-stu-id="8d66a-306">If you did not change **Copy Local** to **False** for the `Calc1AddInView` project reference in the `AddInCalcV1` project, loader context problems will prevent the add-in from being located.</span></span>  
  
     <span data-ttu-id="8d66a-307">如需部署到管線的相關資訊，請參閱[管線開發需求](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。</span><span class="sxs-lookup"><span data-stu-id="8d66a-307">For information about deploying to the pipeline, see [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
## <a name="running-the-host-application"></a><span data-ttu-id="8d66a-308">執行主應用程式</span><span class="sxs-lookup"><span data-stu-id="8d66a-308">Running the Host Application</span></span>  
 <span data-ttu-id="8d66a-309">您現在已準備好執行主機和增益集與互動。</span><span class="sxs-lookup"><span data-stu-id="8d66a-309">You are now ready to run the host and interact with the add-in.</span></span>  
  
#### <a name="to-run-the-host-application"></a><span data-ttu-id="8d66a-310">若要執行主應用程式</span><span class="sxs-lookup"><span data-stu-id="8d66a-310">To run the host application</span></span>  
  
1.  <span data-ttu-id="8d66a-311">在命令提示字元中，移至應用程式目錄並執行主應用程式， `Calc1Host.exe`。</span><span class="sxs-lookup"><span data-stu-id="8d66a-311">At the command prompt, go to the application directory and run the host application, `Calc1Host.exe`.</span></span>  
  
2.  <span data-ttu-id="8d66a-312">主應用程式會尋找其類型的所有可用增益，並提示您選取的增益集。</span><span class="sxs-lookup"><span data-stu-id="8d66a-312">The host finds all available add-ins of its type and prompts you to select an add-in.</span></span> <span data-ttu-id="8d66a-313">請輸入**1** for 唯一可用的增益集。</span><span class="sxs-lookup"><span data-stu-id="8d66a-313">Enter **1** for the only available add-in.</span></span>  
  
3.  <span data-ttu-id="8d66a-314">這類計算機中，輸入一個方程式**2 + 2**。</span><span class="sxs-lookup"><span data-stu-id="8d66a-314">Enter an equation for the calculator, such as **2 + 2**.</span></span> <span data-ttu-id="8d66a-315">必須有數字和運算子之間的空格。</span><span class="sxs-lookup"><span data-stu-id="8d66a-315">There must be spaces between the numbers and the operator.</span></span>  
  
4.  <span data-ttu-id="8d66a-316">型別**結束**然後按**Enter**鍵以關閉應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d66a-316">Type **exit** and press the **Enter** key to close the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d66a-317">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d66a-317">See Also</span></span>  
 [<span data-ttu-id="8d66a-318">逐步解說： 啟用主應用程式變更的回溯相容性</span><span class="sxs-lookup"><span data-stu-id="8d66a-318">Walkthrough: Enabling Backward Compatibility as Your Host Changes</span></span>](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [<span data-ttu-id="8d66a-319">主機和增益集之間的逐步解說： 將集合</span><span class="sxs-lookup"><span data-stu-id="8d66a-319">Walkthrough: Passing Collections Between Hosts and Add-Ins</span></span>](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [<span data-ttu-id="8d66a-320">管線開發需求</span><span class="sxs-lookup"><span data-stu-id="8d66a-320">Pipeline Development Requirements</span></span>](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [<span data-ttu-id="8d66a-321">合約、 檢視和配接器</span><span class="sxs-lookup"><span data-stu-id="8d66a-321">Contracts, Views, and Adapters</span></span>](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [<span data-ttu-id="8d66a-322">管線開發</span><span class="sxs-lookup"><span data-stu-id="8d66a-322">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)
