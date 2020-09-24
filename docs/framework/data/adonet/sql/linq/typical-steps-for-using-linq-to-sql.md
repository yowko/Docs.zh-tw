---
title: LINQ to SQL 的典型使用步驟
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: dc8c4be1e895ee5c4c7947e6311e5bf71008490f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164256"
---
# <a name="typical-steps-for-using-linq-to-sql"></a><span data-ttu-id="47c5b-102">LINQ to SQL 的典型使用步驟</span><span class="sxs-lookup"><span data-stu-id="47c5b-102">Typical Steps for Using LINQ to SQL</span></span>

<span data-ttu-id="47c5b-103">若要實作 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式，請遵循本主題稍後所說明的步驟。</span><span class="sxs-lookup"><span data-stu-id="47c5b-103">To implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application, you follow the steps described later in this topic.</span></span> <span data-ttu-id="47c5b-104">請注意，許多步驟都是選擇性的步驟。</span><span class="sxs-lookup"><span data-stu-id="47c5b-104">Note that many steps are optional.</span></span> <span data-ttu-id="47c5b-105">您可以放心使用預設狀態下的物件模型。</span><span class="sxs-lookup"><span data-stu-id="47c5b-105">It is very possible that you can use your object model in its default state.</span></span>  
  
 <span data-ttu-id="47c5b-106">若要快速開始使用，請使用物件關聯式設計工具建立您的物件模型，並開始撰寫查詢的程式碼。</span><span class="sxs-lookup"><span data-stu-id="47c5b-106">For a really fast start, use the Object Relational Designer to create your object model and start coding your queries.</span></span>  
  
## <a name="creating-the-object-model"></a><span data-ttu-id="47c5b-107">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="47c5b-107">Creating the Object Model</span></span>  

 <span data-ttu-id="47c5b-108">第一步是從現有關聯式資料庫的中繼資料 (Metadata) 建立物件模型。</span><span class="sxs-lookup"><span data-stu-id="47c5b-108">The first step is to create an object model from the metadata of an existing relational database.</span></span> <span data-ttu-id="47c5b-109">物件模型會根據開發人員的程式設計語言來表示資料庫。</span><span class="sxs-lookup"><span data-stu-id="47c5b-109">The object model represents the database according to the programming language of the developer.</span></span> <span data-ttu-id="47c5b-110">如需詳細資訊，請參閱 [LINQ to SQL 物件模型](the-linq-to-sql-object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="47c5b-110">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
### <a name="1-select-a-tool-to-create-the-model"></a><span data-ttu-id="47c5b-111">1. 選取用來建立模型的工具。</span><span class="sxs-lookup"><span data-stu-id="47c5b-111">1. Select a tool to create the model.</span></span>  

 <span data-ttu-id="47c5b-112">用於建立模型的工具有三種。</span><span class="sxs-lookup"><span data-stu-id="47c5b-112">Three tools are available for creating the model.</span></span>  
  
- <span data-ttu-id="47c5b-113">物件關聯式設計工具</span><span class="sxs-lookup"><span data-stu-id="47c5b-113">The Object Relational Designer</span></span>  
  
     <span data-ttu-id="47c5b-114">這個設計工具提供了豐富的使用者介面，可用於從現有資料庫建立物件模型。</span><span class="sxs-lookup"><span data-stu-id="47c5b-114">This designer provides a rich user interface for creating an object model from an existing database.</span></span> <span data-ttu-id="47c5b-115">此工具是 Visual Studio IDE 的一部分，最適合用於小型或中型資料庫。</span><span class="sxs-lookup"><span data-stu-id="47c5b-115">This tool is part of the Visual Studio IDE, and is best suited to small or medium databases.</span></span>  
  
- <span data-ttu-id="47c5b-116">SQLMetal 程式碼產生工具</span><span class="sxs-lookup"><span data-stu-id="47c5b-116">The SQLMetal code-generation tool</span></span>  
  
     <span data-ttu-id="47c5b-117">此命令列公用程式提供與 O/R 設計工具稍微不同的選項組。</span><span class="sxs-lookup"><span data-stu-id="47c5b-117">This command-line utility provides a slightly different set of options from the O/R Designer.</span></span> <span data-ttu-id="47c5b-118">若要建立大型資料庫的模型，使用這項工具最適合。</span><span class="sxs-lookup"><span data-stu-id="47c5b-118">Modeling large databases is best done by using this tool.</span></span> <span data-ttu-id="47c5b-119">如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="47c5b-119">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
- <span data-ttu-id="47c5b-120">程式碼編輯器</span><span class="sxs-lookup"><span data-stu-id="47c5b-120">A code editor</span></span>  
  
     <span data-ttu-id="47c5b-121">您可以使用 [Visual Studio 程式碼編輯器] 或其他編輯器來撰寫自己的程式碼。</span><span class="sxs-lookup"><span data-stu-id="47c5b-121">You can write your own code by using either the Visual Studio code editor or another editor.</span></span> <span data-ttu-id="47c5b-122">當您有現有的資料庫，而且可以使用 O/R 設計工具或 SQLMetal 工具時，不建議使用這種方法，這種方法可能會很容易發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="47c5b-122">We do not recommend this approach, which can be prone to errors, when you have an existing database and can use either the O/R Designer or the SQLMetal tool.</span></span> <span data-ttu-id="47c5b-123">但是，程式碼編輯器很適合用於調整您已經使用其他工具所產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="47c5b-123">However, the code editor can be valuable for refining or modifying code you have already generated by using other tools.</span></span> <span data-ttu-id="47c5b-124">如需詳細資訊，請參閱 [如何：使用程式碼編輯器自訂實體類別](how-to-customize-entity-classes-by-using-the-code-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="47c5b-124">For more information, see [How to: Customize Entity Classes by Using the Code Editor](how-to-customize-entity-classes-by-using-the-code-editor.md).</span></span>  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a><span data-ttu-id="47c5b-125">2. 選取您要產生的程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="47c5b-125">2. Select the kind of code you want to generate.</span></span>  
  
- <span data-ttu-id="47c5b-126">C # 或 Visual Basic 原始程式碼檔，用於以屬性為基礎的對應。</span><span class="sxs-lookup"><span data-stu-id="47c5b-126">A C# or Visual Basic source code file for attribute-based mapping.</span></span>  
  
     <span data-ttu-id="47c5b-127">然後，您會在 Visual Studio 專案中包含這個程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="47c5b-127">You then include this code file in your Visual Studio project.</span></span> <span data-ttu-id="47c5b-128">如需詳細資訊，請參閱以 [屬性為基礎的對應](attribute-based-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="47c5b-128">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="47c5b-129">XML 檔：適用於外部對應。</span><span class="sxs-lookup"><span data-stu-id="47c5b-129">An XML file for external mapping.</span></span>  
  
     <span data-ttu-id="47c5b-130">使用這種方法，您可以將對應中繼資料留在應用程式程式碼外。</span><span class="sxs-lookup"><span data-stu-id="47c5b-130">By using this approach, you can keep the mapping metadata out of your application code.</span></span> <span data-ttu-id="47c5b-131">如需詳細資訊，請參閱 [外部對應](external-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="47c5b-131">For more information, see [External Mapping](external-mapping.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="47c5b-132">O/R 設計工具不支援產生外部對應檔案。</span><span class="sxs-lookup"><span data-stu-id="47c5b-132">The O/R Designer does not support the generation of external mapping files.</span></span> <span data-ttu-id="47c5b-133">您必須使用 SQLMetal 工具來實作這項功能。</span><span class="sxs-lookup"><span data-stu-id="47c5b-133">You must use the SQLMetal tool to implement this feature.</span></span>  
  
- <span data-ttu-id="47c5b-134">DBML 檔：您可以在產生最終程式碼檔之前修改這個檔案。</span><span class="sxs-lookup"><span data-stu-id="47c5b-134">A DBML file, which you can modify before generating a final code file.</span></span>  
  
     <span data-ttu-id="47c5b-135">這是一項進階功能。</span><span class="sxs-lookup"><span data-stu-id="47c5b-135">This is an advanced feature.</span></span>  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a><span data-ttu-id="47c5b-136">3. 精簡程式碼檔案，以反映應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="47c5b-136">3. Refine the code file to reflect the needs of your application.</span></span>  

 <span data-ttu-id="47c5b-137">基於這個目的，您可以使用 O/R 設計工具或程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="47c5b-137">For this purpose, you can use either the O/R Designer or the code editor.</span></span>  
  
## <a name="using-the-object-model"></a><span data-ttu-id="47c5b-138">使用物件模型</span><span class="sxs-lookup"><span data-stu-id="47c5b-138">Using the Object Model</span></span>  

 <span data-ttu-id="47c5b-139">下圖顯示在兩層式案例中，開發人員和資料之間的關係。</span><span class="sxs-lookup"><span data-stu-id="47c5b-139">The following illustration shows the relationship between the developer and the data in a two-tier scenario.</span></span> <span data-ttu-id="47c5b-140">針對其他案例，請參閱 [具有 LINQ to SQL 的多層式和遠端應用程式](n-tier-and-remote-applications-with-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="47c5b-140">For other scenarios, see [N-Tier and Remote Applications with LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md).</span></span>  
  
 ![顯示 Linq 物件模型的螢幕擷取畫面。](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 <span data-ttu-id="47c5b-142">您現在有了物件模型，接著就可以描述資訊要求以及操作該模型內的資料。</span><span class="sxs-lookup"><span data-stu-id="47c5b-142">Now that you have the object model, you describe information requests and manipulate data within that model.</span></span> <span data-ttu-id="47c5b-143">您會由物件模型中的物件和屬性觀點思考，而不是由資料庫的資料列和資料行觀點思考。</span><span class="sxs-lookup"><span data-stu-id="47c5b-143">You think in terms of the objects and properties in your object model and not in terms of the rows and columns of the database.</span></span> <span data-ttu-id="47c5b-144">您不會直接處理資料庫。</span><span class="sxs-lookup"><span data-stu-id="47c5b-144">You do not deal directly with the database.</span></span>  
  
 <span data-ttu-id="47c5b-145">當您指示 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 執行所述的查詢，或呼叫 `SubmitChanges()` 您已操作的資料時，會以 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 資料庫的語言與資料庫進行通訊。</span><span class="sxs-lookup"><span data-stu-id="47c5b-145">When you instruct [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to either execute a query that you have described or call `SubmitChanges()` on data that you have manipulated, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] communicates with the database in the language of the database.</span></span>  
  
 <span data-ttu-id="47c5b-146">下列表示使用所建立之物件模型的一般步驟。</span><span class="sxs-lookup"><span data-stu-id="47c5b-146">The following represents typical steps for using the object model that you have created.</span></span>  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a><span data-ttu-id="47c5b-147">1. 建立查詢以從資料庫中取出資訊。</span><span class="sxs-lookup"><span data-stu-id="47c5b-147">1. Create queries to retrieve information from the database.</span></span>  

 <span data-ttu-id="47c5b-148">如需詳細資訊，請參閱 [查詢概念](query-concepts.md) 和 [查詢範例](query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="47c5b-148">For more information, see [Query Concepts](query-concepts.md) and [Query Examples](query-examples.md).</span></span>  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a><span data-ttu-id="47c5b-149">2. 覆寫 Insert、Update 和 Delete 的預設行為。</span><span class="sxs-lookup"><span data-stu-id="47c5b-149">2. Override default behaviors for Insert, Update, and Delete.</span></span>  

 <span data-ttu-id="47c5b-150">這是選擇性步驟。</span><span class="sxs-lookup"><span data-stu-id="47c5b-150">This step is optional.</span></span> <span data-ttu-id="47c5b-151">如需詳細資訊，請參閱 [自訂插入、更新和刪除作業](customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="47c5b-151">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a><span data-ttu-id="47c5b-152">3. 設定適當的選項來偵測和報告並行衝突。</span><span class="sxs-lookup"><span data-stu-id="47c5b-152">3. Set appropriate options to detect and report concurrency conflicts.</span></span>  

 <span data-ttu-id="47c5b-153">您可以讓模型保有處理並行衝突時所用的預設值，也可加以變更以符合您的目的。</span><span class="sxs-lookup"><span data-stu-id="47c5b-153">You can leave your model with its default values for handling concurrency conflicts, or you can change it to suit your purposes.</span></span> <span data-ttu-id="47c5b-154">如需詳細資訊，請參閱 [如何：指定測試並行衝突的成員](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) 和 [如何：指定並行例外狀況的](how-to-specify-when-concurrency-exceptions-are-thrown.md)擲回時機。</span><span class="sxs-lookup"><span data-stu-id="47c5b-154">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) and [How to: Specify When Concurrency Exceptions are Thrown](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span></span>  
  
### <a name="4-establish-an-inheritance-hierarchy"></a><span data-ttu-id="47c5b-155">4. 建立繼承階層。</span><span class="sxs-lookup"><span data-stu-id="47c5b-155">4. Establish an inheritance hierarchy.</span></span>  

 <span data-ttu-id="47c5b-156">這是選擇性步驟。</span><span class="sxs-lookup"><span data-stu-id="47c5b-156">This step is optional.</span></span> <span data-ttu-id="47c5b-157">如需詳細資訊，請參閱 [繼承支援](inheritance-support.md)。</span><span class="sxs-lookup"><span data-stu-id="47c5b-157">For more information, see [Inheritance Support](inheritance-support.md).</span></span>  
  
### <a name="5-provide-an-appropriate-user-interface"></a><span data-ttu-id="47c5b-158">5. 提供適當的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="47c5b-158">5. Provide an appropriate user interface.</span></span>  

 <span data-ttu-id="47c5b-159">這個步驟是選擇性的步驟，要視應用程式的使用方式而定。</span><span class="sxs-lookup"><span data-stu-id="47c5b-159">This step is optional, and depends on how your application will be used.</span></span>  
  
### <a name="6-debug-and-test-your-application"></a><span data-ttu-id="47c5b-160">6. 針對您的應用程式進行 Debug 和 test。</span><span class="sxs-lookup"><span data-stu-id="47c5b-160">6. Debug and test your application.</span></span>  

 <span data-ttu-id="47c5b-161">如需詳細資訊，請參閱 [偵錯工具支援](debugging-support.md)。</span><span class="sxs-lookup"><span data-stu-id="47c5b-161">For more information, see [Debugging Support](debugging-support.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c5b-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47c5b-162">See also</span></span>

- [<span data-ttu-id="47c5b-163">快速入門</span><span class="sxs-lookup"><span data-stu-id="47c5b-163">Getting Started</span></span>](getting-started.md)
- [<span data-ttu-id="47c5b-164">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="47c5b-164">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="47c5b-165">預存程序</span><span class="sxs-lookup"><span data-stu-id="47c5b-165">Stored Procedures</span></span>](stored-procedures.md)
