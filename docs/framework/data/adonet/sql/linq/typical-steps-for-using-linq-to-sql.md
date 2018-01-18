---
title: "LINQ to SQL 的典型使用步驟"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3aedef610d8ad3f743b346a46059b15d917cf7ca
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="typical-steps-for-using-linq-to-sql"></a><span data-ttu-id="af8f5-102">LINQ to SQL 的典型使用步驟</span><span class="sxs-lookup"><span data-stu-id="af8f5-102">Typical Steps for Using LINQ to SQL</span></span>
<span data-ttu-id="af8f5-103">若要實作 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式，請遵循本主題稍後所說明的步驟。</span><span class="sxs-lookup"><span data-stu-id="af8f5-103">To implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application, you follow the steps described later in this topic.</span></span> <span data-ttu-id="af8f5-104">請注意，許多步驟都是選擇性的步驟。</span><span class="sxs-lookup"><span data-stu-id="af8f5-104">Note that many steps are optional.</span></span> <span data-ttu-id="af8f5-105">您可以放心使用預設狀態下的物件模型。</span><span class="sxs-lookup"><span data-stu-id="af8f5-105">It is very possible that you can use your object model in its default state.</span></span>  
  
 <span data-ttu-id="af8f5-106">若要快速學會，請使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來建立物件模型並且開始撰寫查詢的程式碼。</span><span class="sxs-lookup"><span data-stu-id="af8f5-106">For a really fast start, use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model and start coding your queries.</span></span>  
  
## <a name="creating-the-object-model"></a><span data-ttu-id="af8f5-107">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="af8f5-107">Creating the Object Model</span></span>  
 <span data-ttu-id="af8f5-108">第一步是從現有關聯式資料庫的中繼資料 (Metadata) 建立物件模型。</span><span class="sxs-lookup"><span data-stu-id="af8f5-108">The first step is to create an object model from the metadata of an existing relational database.</span></span> <span data-ttu-id="af8f5-109">物件模型會根據開發人員的程式設計語言來表示資料庫。</span><span class="sxs-lookup"><span data-stu-id="af8f5-109">The object model represents the database according to the programming language of the developer.</span></span> <span data-ttu-id="af8f5-110">如需詳細資訊，請參閱[LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="af8f5-110">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
### <a name="1-select-a-tool-to-create-the-model"></a><span data-ttu-id="af8f5-111">1.選取用以建立模型的工具。</span><span class="sxs-lookup"><span data-stu-id="af8f5-111">1. Select a tool to create the model.</span></span>  
 <span data-ttu-id="af8f5-112">用於建立模型的工具有三種。</span><span class="sxs-lookup"><span data-stu-id="af8f5-112">Three tools are available for creating the model.</span></span>  
  
-   <span data-ttu-id="af8f5-113">[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af8f5-113">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]</span></span>  
  
     <span data-ttu-id="af8f5-114">這個設計工具提供了豐富的使用者介面，可用於從現有資料庫建立物件模型。</span><span class="sxs-lookup"><span data-stu-id="af8f5-114">This designer provides a rich user interface for creating an object model from an existing database.</span></span> <span data-ttu-id="af8f5-115">這項工具屬於 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] IDE 的一部分，最適合用於小型或中型資料庫。</span><span class="sxs-lookup"><span data-stu-id="af8f5-115">This tool is part of the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] IDE, and is best suited to small or medium databases.</span></span>  
  
-   <span data-ttu-id="af8f5-116">SQLMetal 程式碼產生工具</span><span class="sxs-lookup"><span data-stu-id="af8f5-116">The SQLMetal code-generation tool</span></span>  
  
     <span data-ttu-id="af8f5-117">這個命令列公用程式提供了與 [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]稍有不同的一組選項。</span><span class="sxs-lookup"><span data-stu-id="af8f5-117">This command-line utility provides a slightly different set of options from the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span></span> <span data-ttu-id="af8f5-118">若要建立大型資料庫的模型，使用這項工具最適合。</span><span class="sxs-lookup"><span data-stu-id="af8f5-118">Modeling large databases is best done by using this tool.</span></span> <span data-ttu-id="af8f5-119">如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="af8f5-119">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
-   <span data-ttu-id="af8f5-120">程式碼編輯器</span><span class="sxs-lookup"><span data-stu-id="af8f5-120">A code editor</span></span>  
  
     <span data-ttu-id="af8f5-121">您可以使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 程式碼編輯器或其他編輯器，撰寫自己的程式碼。</span><span class="sxs-lookup"><span data-stu-id="af8f5-121">You can write your own code by using either the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] code editor or another editor.</span></span> <span data-ttu-id="af8f5-122">當您具有現有的資料庫而且可使用 [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]或 SQLMetal 工具時，則不建議這種方法，因為很容易發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="af8f5-122">We do not recommend this approach, which can be prone to errors, when you have an existing database and can use either the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] or the SQLMetal tool.</span></span> <span data-ttu-id="af8f5-123">但是，程式碼編輯器很適合用於調整您已經使用其他工具所產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="af8f5-123">However, the code editor can be valuable for refining or modifying code you have already generated by using other tools.</span></span> <span data-ttu-id="af8f5-124">如需詳細資訊，請參閱[How to： 使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="af8f5-124">For more information, see [How to: Customize Entity Classes by Using the Code Editor](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md).</span></span>  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a><span data-ttu-id="af8f5-125">2.選取您要產生的程式碼種類。</span><span class="sxs-lookup"><span data-stu-id="af8f5-125">2. Select the kind of code you want to generate.</span></span>  
  
-   <span data-ttu-id="af8f5-126">C# 或 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 原始程式碼檔：適用於以屬性為基礎的對應。</span><span class="sxs-lookup"><span data-stu-id="af8f5-126">A C# or [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] source code file for attribute-based mapping.</span></span>  
  
     <span data-ttu-id="af8f5-127">您可以接著在 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 專案中包含這個程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="af8f5-127">You then include this code file in your [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] project.</span></span> <span data-ttu-id="af8f5-128">如需詳細資訊，請參閱[屬性架構對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="af8f5-128">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
-   <span data-ttu-id="af8f5-129">XML 檔：適用於外部對應。</span><span class="sxs-lookup"><span data-stu-id="af8f5-129">An XML file for external mapping.</span></span>  
  
     <span data-ttu-id="af8f5-130">使用這種方法，您可以將對應中繼資料留在應用程式程式碼外。</span><span class="sxs-lookup"><span data-stu-id="af8f5-130">By using this approach, you can keep the mapping metadata out of your application code.</span></span> <span data-ttu-id="af8f5-131">如需詳細資訊，請參閱[外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="af8f5-131">For more information, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="af8f5-132">[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]不支援產生外部對應檔案。</span><span class="sxs-lookup"><span data-stu-id="af8f5-132">The [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] does not support the generation of external mapping files.</span></span> <span data-ttu-id="af8f5-133">您必須使用 SQLMetal 工具來實作這項功能。</span><span class="sxs-lookup"><span data-stu-id="af8f5-133">You must use the SQLMetal tool to implement this feature.</span></span>  
  
-   <span data-ttu-id="af8f5-134">DBML 檔：您可以在產生最終程式碼檔之前修改這個檔案。</span><span class="sxs-lookup"><span data-stu-id="af8f5-134">A DBML file, which you can modify before generating a final code file.</span></span>  
  
     <span data-ttu-id="af8f5-135">這是一項進階功能。</span><span class="sxs-lookup"><span data-stu-id="af8f5-135">This is an advanced feature.</span></span>  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a><span data-ttu-id="af8f5-136">3.修改程式碼檔，以反映您的應用程式需求。</span><span class="sxs-lookup"><span data-stu-id="af8f5-136">3. Refine the code file to reflect the needs of your application.</span></span>  
 <span data-ttu-id="af8f5-137">針對此目的，您可以使用 [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]或程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="af8f5-137">For this purpose, you can use either the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] or the code editor.</span></span>  
  
## <a name="using-the-object-model"></a><span data-ttu-id="af8f5-138">使用物件模型</span><span class="sxs-lookup"><span data-stu-id="af8f5-138">Using the Object Model</span></span>  
 <span data-ttu-id="af8f5-139">下圖顯示在兩層式案例中，開發人員和資料之間的關係。</span><span class="sxs-lookup"><span data-stu-id="af8f5-139">The following illustration shows the relationship between the developer and the data in a two-tier scenario.</span></span> <span data-ttu-id="af8f5-140">如需其他案例中，請參閱[N-tier 和遠端的應用程式以及 LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="af8f5-140">For other scenarios, see [N-Tier and Remote Applications with LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="af8f5-141">![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")</span><span class="sxs-lookup"><span data-stu-id="af8f5-141">![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")</span></span>  
  
 <span data-ttu-id="af8f5-142">您現在有了物件模型，接著就可以描述資訊要求以及操作該模型內的資料。</span><span class="sxs-lookup"><span data-stu-id="af8f5-142">Now that you have the object model, you describe information requests and manipulate data within that model.</span></span> <span data-ttu-id="af8f5-143">您會由物件模型中的物件和屬性觀點思考，而不是由資料庫的資料列和資料行觀點思考。</span><span class="sxs-lookup"><span data-stu-id="af8f5-143">You think in terms of the objects and properties in your object model and not in terms of the rows and columns of the database.</span></span> <span data-ttu-id="af8f5-144">您不會直接處理資料庫。</span><span class="sxs-lookup"><span data-stu-id="af8f5-144">You do not deal directly with the database.</span></span>  
  
 <span data-ttu-id="af8f5-145">當您指示[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]設為 執行查詢所述或呼叫`SubmitChanges()`您管理的資料上[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]與資料庫的語言中的資料庫進行通訊。</span><span class="sxs-lookup"><span data-stu-id="af8f5-145">When you instruct [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to either execute a query that you have described or call `SubmitChanges()` on data that you have manipulated, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] communicates with the database in the language of the database.</span></span>  
  
 <span data-ttu-id="af8f5-146">下列表示使用所建立之物件模型的一般步驟。</span><span class="sxs-lookup"><span data-stu-id="af8f5-146">The following represents typical steps for using the object model that you have created.</span></span>  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a><span data-ttu-id="af8f5-147">1.建立查詢，以從資料庫擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="af8f5-147">1. Create queries to retrieve information from the database.</span></span>  
 <span data-ttu-id="af8f5-148">如需詳細資訊，請參閱[查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)和[查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="af8f5-148">For more information, see [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md) and [Query Examples](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md).</span></span>  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a><span data-ttu-id="af8f5-149">2.覆寫 Insert、Update 和 Delete 的預設行為。</span><span class="sxs-lookup"><span data-stu-id="af8f5-149">2. Override default behaviors for Insert, Update, and Delete.</span></span>  
 <span data-ttu-id="af8f5-150">此步驟是具選擇性的。</span><span class="sxs-lookup"><span data-stu-id="af8f5-150">This step is optional.</span></span> <span data-ttu-id="af8f5-151">如需詳細資訊，請參閱[自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="af8f5-151">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a><span data-ttu-id="af8f5-152">3.設定適當選項，以偵測和報告並行衝突。</span><span class="sxs-lookup"><span data-stu-id="af8f5-152">3. Set appropriate options to detect and report concurrency conflicts.</span></span>  
 <span data-ttu-id="af8f5-153">您可以讓模型保有處理並行衝突時所用的預設值，也可加以變更以符合您的目的。</span><span class="sxs-lookup"><span data-stu-id="af8f5-153">You can leave your model with its default values for handling concurrency conflicts, or you can change it to suit your purposes.</span></span> <span data-ttu-id="af8f5-154">如需詳細資訊，請參閱[How to： 指定的成員會用於測試並行衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)和[How to： 指定當並行存取例外狀況擲回](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)。</span><span class="sxs-lookup"><span data-stu-id="af8f5-154">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) and [How to: Specify When Concurrency Exceptions are Thrown](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).</span></span>  
  
### <a name="4-establish-an-inheritance-hierarchy"></a><span data-ttu-id="af8f5-155">4.建立繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="af8f5-155">4. Establish an inheritance hierarchy.</span></span>  
 <span data-ttu-id="af8f5-156">此步驟是具選擇性的。</span><span class="sxs-lookup"><span data-stu-id="af8f5-156">This step is optional.</span></span> <span data-ttu-id="af8f5-157">如需詳細資訊，請參閱[繼承支援](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)。</span><span class="sxs-lookup"><span data-stu-id="af8f5-157">For more information, see [Inheritance Support](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).</span></span>  
  
### <a name="5-provide-an-appropriate-user-interface"></a><span data-ttu-id="af8f5-158">5.提供適當的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="af8f5-158">5. Provide an appropriate user interface.</span></span>  
 <span data-ttu-id="af8f5-159">這個步驟是選擇性的步驟，要視應用程式的使用方式而定。</span><span class="sxs-lookup"><span data-stu-id="af8f5-159">This step is optional, and depends on how your application will be used.</span></span>  
  
### <a name="6-debug-and-test-your-application"></a><span data-ttu-id="af8f5-160">6.偵錯和測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="af8f5-160">6. Debug and test your application.</span></span>  
 <span data-ttu-id="af8f5-161">如需詳細資訊，請參閱[偵錯支援](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)。</span><span class="sxs-lookup"><span data-stu-id="af8f5-161">For more information, see [Debugging Support](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af8f5-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="af8f5-162">See Also</span></span>  
 [<span data-ttu-id="af8f5-163">快速入門</span><span class="sxs-lookup"><span data-stu-id="af8f5-163">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 [<span data-ttu-id="af8f5-164">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="af8f5-164">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="af8f5-165">預存程序</span><span class="sxs-lookup"><span data-stu-id="af8f5-165">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
