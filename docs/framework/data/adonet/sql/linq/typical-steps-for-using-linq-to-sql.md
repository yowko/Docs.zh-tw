---
title: LINQ to SQL 的典型使用步驟
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: c7964c821a838e027302cddce704d86cc6a34f66
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792335"
---
# <a name="typical-steps-for-using-linq-to-sql"></a><span data-ttu-id="dcda1-102">LINQ to SQL 的典型使用步驟</span><span class="sxs-lookup"><span data-stu-id="dcda1-102">Typical Steps for Using LINQ to SQL</span></span>
<span data-ttu-id="dcda1-103">若要實作 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式，請遵循本主題稍後所說明的步驟。</span><span class="sxs-lookup"><span data-stu-id="dcda1-103">To implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application, you follow the steps described later in this topic.</span></span> <span data-ttu-id="dcda1-104">請注意，許多步驟都是選擇性的步驟。</span><span class="sxs-lookup"><span data-stu-id="dcda1-104">Note that many steps are optional.</span></span> <span data-ttu-id="dcda1-105">您可以放心使用預設狀態下的物件模型。</span><span class="sxs-lookup"><span data-stu-id="dcda1-105">It is very possible that you can use your object model in its default state.</span></span>  
  
 <span data-ttu-id="dcda1-106">若要快速開始，請使用物件關聯式設計工具建立您的物件模型，並開始撰寫查詢的程式碼。</span><span class="sxs-lookup"><span data-stu-id="dcda1-106">For a really fast start, use the Object Relational Designer to create your object model and start coding your queries.</span></span>  
  
## <a name="creating-the-object-model"></a><span data-ttu-id="dcda1-107">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="dcda1-107">Creating the Object Model</span></span>  
 <span data-ttu-id="dcda1-108">第一步是從現有關聯式資料庫的中繼資料 (Metadata) 建立物件模型。</span><span class="sxs-lookup"><span data-stu-id="dcda1-108">The first step is to create an object model from the metadata of an existing relational database.</span></span> <span data-ttu-id="dcda1-109">物件模型會根據開發人員的程式設計語言來表示資料庫。</span><span class="sxs-lookup"><span data-stu-id="dcda1-109">The object model represents the database according to the programming language of the developer.</span></span> <span data-ttu-id="dcda1-110">如需詳細資訊，請參閱[LINQ to SQL 物件模型](the-linq-to-sql-object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="dcda1-110">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
### <a name="1-select-a-tool-to-create-the-model"></a><span data-ttu-id="dcda1-111">1.選取用以建立模型的工具。</span><span class="sxs-lookup"><span data-stu-id="dcda1-111">1. Select a tool to create the model.</span></span>  
 <span data-ttu-id="dcda1-112">用於建立模型的工具有三種。</span><span class="sxs-lookup"><span data-stu-id="dcda1-112">Three tools are available for creating the model.</span></span>  
  
- <span data-ttu-id="dcda1-113">物件關聯式設計工具</span><span class="sxs-lookup"><span data-stu-id="dcda1-113">The Object Relational Designer</span></span>  
  
     <span data-ttu-id="dcda1-114">這個設計工具提供了豐富的使用者介面，可用於從現有資料庫建立物件模型。</span><span class="sxs-lookup"><span data-stu-id="dcda1-114">This designer provides a rich user interface for creating an object model from an existing database.</span></span> <span data-ttu-id="dcda1-115">這項工具是 Visual Studio IDE 的一部分，最適合用於小型或中型資料庫。</span><span class="sxs-lookup"><span data-stu-id="dcda1-115">This tool is part of the Visual Studio IDE, and is best suited to small or medium databases.</span></span>  
  
- <span data-ttu-id="dcda1-116">SQLMetal 程式碼產生工具</span><span class="sxs-lookup"><span data-stu-id="dcda1-116">The SQLMetal code-generation tool</span></span>  
  
     <span data-ttu-id="dcda1-117">這個命令列公用程式提供了一組與 O/R 設計工具稍微不同的選項。</span><span class="sxs-lookup"><span data-stu-id="dcda1-117">This command-line utility provides a slightly different set of options from the O/R Designer.</span></span> <span data-ttu-id="dcda1-118">若要建立大型資料庫的模型，使用這項工具最適合。</span><span class="sxs-lookup"><span data-stu-id="dcda1-118">Modeling large databases is best done by using this tool.</span></span> <span data-ttu-id="dcda1-119">如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="dcda1-119">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
- <span data-ttu-id="dcda1-120">程式碼編輯器</span><span class="sxs-lookup"><span data-stu-id="dcda1-120">A code editor</span></span>  
  
     <span data-ttu-id="dcda1-121">您可以使用 Visual Studio 程式碼編輯器或其他編輯器，撰寫自己的程式碼。</span><span class="sxs-lookup"><span data-stu-id="dcda1-121">You can write your own code by using either the Visual Studio code editor or another editor.</span></span> <span data-ttu-id="dcda1-122">當您有現有的資料庫，而且可以使用 O/R 設計工具或 SQLMetal 工具時，我們不建議採用這種方法，這可能會容易發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="dcda1-122">We do not recommend this approach, which can be prone to errors, when you have an existing database and can use either the O/R Designer or the SQLMetal tool.</span></span> <span data-ttu-id="dcda1-123">但是，程式碼編輯器很適合用於調整您已經使用其他工具所產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="dcda1-123">However, the code editor can be valuable for refining or modifying code you have already generated by using other tools.</span></span> <span data-ttu-id="dcda1-124">如需詳細資訊，請參閱[如何：使用程式碼編輯器](how-to-customize-entity-classes-by-using-the-code-editor.md)自訂實體類別。</span><span class="sxs-lookup"><span data-stu-id="dcda1-124">For more information, see [How to: Customize Entity Classes by Using the Code Editor](how-to-customize-entity-classes-by-using-the-code-editor.md).</span></span>  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a><span data-ttu-id="dcda1-125">2.選取您要產生的程式碼種類。</span><span class="sxs-lookup"><span data-stu-id="dcda1-125">2. Select the kind of code you want to generate.</span></span>  
  
- <span data-ttu-id="dcda1-126">C#或 Visual Basic 原始程式碼檔，用於以屬性為基礎的對應。</span><span class="sxs-lookup"><span data-stu-id="dcda1-126">A C# or Visual Basic source code file for attribute-based mapping.</span></span>  
  
     <span data-ttu-id="dcda1-127">接著，您會在 Visual Studio 專案中包含這個程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="dcda1-127">You then include this code file in your Visual Studio project.</span></span> <span data-ttu-id="dcda1-128">如需詳細資訊，請參閱以[屬性為基礎的對應](attribute-based-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="dcda1-128">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="dcda1-129">XML 檔：適用於外部對應。</span><span class="sxs-lookup"><span data-stu-id="dcda1-129">An XML file for external mapping.</span></span>  
  
     <span data-ttu-id="dcda1-130">使用這種方法，您可以將對應中繼資料留在應用程式程式碼外。</span><span class="sxs-lookup"><span data-stu-id="dcda1-130">By using this approach, you can keep the mapping metadata out of your application code.</span></span> <span data-ttu-id="dcda1-131">如需詳細資訊，請參閱[外部對應](external-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="dcda1-131">For more information, see [External Mapping](external-mapping.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="dcda1-132">O/R 設計工具不支援產生外部對應檔案。</span><span class="sxs-lookup"><span data-stu-id="dcda1-132">The O/R Designer does not support the generation of external mapping files.</span></span> <span data-ttu-id="dcda1-133">您必須使用 SQLMetal 工具來實作這項功能。</span><span class="sxs-lookup"><span data-stu-id="dcda1-133">You must use the SQLMetal tool to implement this feature.</span></span>  
  
- <span data-ttu-id="dcda1-134">DBML 檔：您可以在產生最終程式碼檔之前修改這個檔案。</span><span class="sxs-lookup"><span data-stu-id="dcda1-134">A DBML file, which you can modify before generating a final code file.</span></span>  
  
     <span data-ttu-id="dcda1-135">這是一項進階功能。</span><span class="sxs-lookup"><span data-stu-id="dcda1-135">This is an advanced feature.</span></span>  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a><span data-ttu-id="dcda1-136">3.修改程式碼檔，以反映您的應用程式需求。</span><span class="sxs-lookup"><span data-stu-id="dcda1-136">3. Refine the code file to reflect the needs of your application.</span></span>  
 <span data-ttu-id="dcda1-137">基於此目的，您可以使用 O/R 設計工具或程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="dcda1-137">For this purpose, you can use either the O/R Designer or the code editor.</span></span>  
  
## <a name="using-the-object-model"></a><span data-ttu-id="dcda1-138">使用物件模型</span><span class="sxs-lookup"><span data-stu-id="dcda1-138">Using the Object Model</span></span>  
 <span data-ttu-id="dcda1-139">下圖顯示在兩層式案例中，開發人員和資料之間的關係。</span><span class="sxs-lookup"><span data-stu-id="dcda1-139">The following illustration shows the relationship between the developer and the data in a two-tier scenario.</span></span> <span data-ttu-id="dcda1-140">如需其他案例，請參閱[使用 LINQ to SQL 的多層式和遠端應用程式](n-tier-and-remote-applications-with-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="dcda1-140">For other scenarios, see [N-Tier and Remote Applications with LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md).</span></span>  
  
 ![顯示 Linq 物件模型的螢幕擷取畫面。](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 <span data-ttu-id="dcda1-142">您現在有了物件模型，接著就可以描述資訊要求以及操作該模型內的資料。</span><span class="sxs-lookup"><span data-stu-id="dcda1-142">Now that you have the object model, you describe information requests and manipulate data within that model.</span></span> <span data-ttu-id="dcda1-143">您會由物件模型中的物件和屬性觀點思考，而不是由資料庫的資料列和資料行觀點思考。</span><span class="sxs-lookup"><span data-stu-id="dcda1-143">You think in terms of the objects and properties in your object model and not in terms of the rows and columns of the database.</span></span> <span data-ttu-id="dcda1-144">您不會直接處理資料庫。</span><span class="sxs-lookup"><span data-stu-id="dcda1-144">You do not deal directly with the database.</span></span>  
  
 <span data-ttu-id="dcda1-145">當您指示[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]執行您已在操作的資料上描述或呼叫`SubmitChanges()`的查詢時， [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]會以資料庫的語言與資料庫進行通訊。</span><span class="sxs-lookup"><span data-stu-id="dcda1-145">When you instruct [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to either execute a query that you have described or call `SubmitChanges()` on data that you have manipulated, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] communicates with the database in the language of the database.</span></span>  
  
 <span data-ttu-id="dcda1-146">下列表示使用所建立之物件模型的一般步驟。</span><span class="sxs-lookup"><span data-stu-id="dcda1-146">The following represents typical steps for using the object model that you have created.</span></span>  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a><span data-ttu-id="dcda1-147">1.建立查詢，以從資料庫擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="dcda1-147">1. Create queries to retrieve information from the database.</span></span>  
 <span data-ttu-id="dcda1-148">如需詳細資訊，請參閱[查詢概念](query-concepts.md)和[查詢範例](query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="dcda1-148">For more information, see [Query Concepts](query-concepts.md) and [Query Examples](query-examples.md).</span></span>  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a><span data-ttu-id="dcda1-149">2.覆寫 Insert、Update 和 Delete 的預設行為。</span><span class="sxs-lookup"><span data-stu-id="dcda1-149">2. Override default behaviors for Insert, Update, and Delete.</span></span>  
 <span data-ttu-id="dcda1-150">此步驟是具選擇性的。</span><span class="sxs-lookup"><span data-stu-id="dcda1-150">This step is optional.</span></span> <span data-ttu-id="dcda1-151">如需詳細資訊，請參閱[自訂插入、更新和刪除作業](customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="dcda1-151">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a><span data-ttu-id="dcda1-152">3.設定適當選項，以偵測和報告並行衝突。</span><span class="sxs-lookup"><span data-stu-id="dcda1-152">3. Set appropriate options to detect and report concurrency conflicts.</span></span>  
 <span data-ttu-id="dcda1-153">您可以讓模型保有處理並行衝突時所用的預設值，也可加以變更以符合您的目的。</span><span class="sxs-lookup"><span data-stu-id="dcda1-153">You can leave your model with its default values for handling concurrency conflicts, or you can change it to suit your purposes.</span></span> <span data-ttu-id="dcda1-154">如需詳細資訊，請參閱[如何：指定測試並行衝突](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)的成員，以及[如何：指定並行例外狀況的](how-to-specify-when-concurrency-exceptions-are-thrown.md)擲回時機。</span><span class="sxs-lookup"><span data-stu-id="dcda1-154">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) and [How to: Specify When Concurrency Exceptions are Thrown](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span></span>  
  
### <a name="4-establish-an-inheritance-hierarchy"></a><span data-ttu-id="dcda1-155">4.建立繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="dcda1-155">4. Establish an inheritance hierarchy.</span></span>  
 <span data-ttu-id="dcda1-156">此步驟是具選擇性的。</span><span class="sxs-lookup"><span data-stu-id="dcda1-156">This step is optional.</span></span> <span data-ttu-id="dcda1-157">如需詳細資訊，請參閱[繼承支援](inheritance-support.md)。</span><span class="sxs-lookup"><span data-stu-id="dcda1-157">For more information, see [Inheritance Support](inheritance-support.md).</span></span>  
  
### <a name="5-provide-an-appropriate-user-interface"></a><span data-ttu-id="dcda1-158">5.提供適當的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="dcda1-158">5. Provide an appropriate user interface.</span></span>  
 <span data-ttu-id="dcda1-159">這個步驟是選擇性的步驟，要視應用程式的使用方式而定。</span><span class="sxs-lookup"><span data-stu-id="dcda1-159">This step is optional, and depends on how your application will be used.</span></span>  
  
### <a name="6-debug-and-test-your-application"></a><span data-ttu-id="dcda1-160">6.偵錯和測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="dcda1-160">6. Debug and test your application.</span></span>  
 <span data-ttu-id="dcda1-161">如需詳細資訊，請參閱[偵錯工具支援](debugging-support.md)。</span><span class="sxs-lookup"><span data-stu-id="dcda1-161">For more information, see [Debugging Support](debugging-support.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcda1-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcda1-162">See also</span></span>

- [<span data-ttu-id="dcda1-163">快速入門</span><span class="sxs-lookup"><span data-stu-id="dcda1-163">Getting Started</span></span>](getting-started.md)
- [<span data-ttu-id="dcda1-164">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="dcda1-164">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="dcda1-165">預存程序</span><span class="sxs-lookup"><span data-stu-id="dcda1-165">Stored Procedures</span></span>](stored-procedures.md)
