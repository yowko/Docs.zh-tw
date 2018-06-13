---
title: 逐步解說：跨關聯性查詢 (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: aa98a823a5d97d86144ea2f76953e990cde8edec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355200"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="647cf-102">逐步解說：跨關聯性查詢 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="647cf-102">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>
<span data-ttu-id="647cf-103">本逐步解說示範如何使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]*關聯*表示在資料庫中的外部索引鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="647cf-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="647cf-104">這個逐步解說是使用 Visual Basic 開發設定所撰寫。</span><span class="sxs-lookup"><span data-stu-id="647cf-104">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="647cf-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="647cf-105">Prerequisites</span></span>  
 <span data-ttu-id="647cf-106">您必須先完成[逐步解說： 簡單的物件模型和查詢 (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="647cf-106">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="647cf-107">本逐步解決建置於該逐步解決之上，包含存在於 c:\linqtest 中的 northwnd.mdf 檔。</span><span class="sxs-lookup"><span data-stu-id="647cf-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="647cf-108">概觀</span><span class="sxs-lookup"><span data-stu-id="647cf-108">Overview</span></span>  
 <span data-ttu-id="647cf-109">此逐步解說包含三項主要工作：</span><span class="sxs-lookup"><span data-stu-id="647cf-109">This walkthrough consists of three main tasks:</span></span>  
  
-   <span data-ttu-id="647cf-110">加入實體類別，以表示 Northwind 範例資料庫中的 Orders 資料表。</span><span class="sxs-lookup"><span data-stu-id="647cf-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
-   <span data-ttu-id="647cf-111">補充 `Customer` 類別的附註，以加強 `Customer` 和 `Order` 類別之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="647cf-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
-   <span data-ttu-id="647cf-112">建立和執行查詢，以測試使用 `Order` 類別取得 `Customer` 資訊的處理序。</span><span class="sxs-lookup"><span data-stu-id="647cf-112">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="647cf-113">跨資料表對應關聯性</span><span class="sxs-lookup"><span data-stu-id="647cf-113">Mapping Relationships across Tables</span></span>  
 <span data-ttu-id="647cf-114">在 `Customer` 類別定義之後，建立包含下列程式碼的 `Order` 實體類別定義，這表示 `Orders.Customer` 為 `Customers.CustomerID` 的外部索引鍵。</span><span class="sxs-lookup"><span data-stu-id="647cf-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="647cf-115">若要加入 Order 實體類別</span><span class="sxs-lookup"><span data-stu-id="647cf-115">To add the Order entity class</span></span>  
  
-   <span data-ttu-id="647cf-116">在 `Customer` 類別之後輸入或貼上下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="647cf-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="647cf-117">加入 Customer 類別的附註</span><span class="sxs-lookup"><span data-stu-id="647cf-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="647cf-118">在這個步驟中，您會加入 `Customer` 類別的附註，指出其與 `Order` 類別的關聯性</span><span class="sxs-lookup"><span data-stu-id="647cf-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="647cf-119">(此加入動作並非絕對必要，因為定義任一方向的關聯性就足以建立連結。</span><span class="sxs-lookup"><span data-stu-id="647cf-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="647cf-120">但加入此附註確實可讓您輕易地以任一方向巡覽物件)。</span><span class="sxs-lookup"><span data-stu-id="647cf-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="647cf-121">若要加入 Customer 類別的附註</span><span class="sxs-lookup"><span data-stu-id="647cf-121">To annotate the Customer class</span></span>  
  
-   <span data-ttu-id="647cf-122">將下列程式碼輸入或貼到 `Customer` 類別中：</span><span class="sxs-lookup"><span data-stu-id="647cf-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="647cf-123">建立和執行客戶-訂單關聯性的查詢</span><span class="sxs-lookup"><span data-stu-id="647cf-123">Creating and Running a Query across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="647cf-124">您現在可以直接從 `Order` 物件存取 `Customer` 物件，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="647cf-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="647cf-125">您不需要明確*聯結*customers 與 orders 之間。</span><span class="sxs-lookup"><span data-stu-id="647cf-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="647cf-126">若要使用 Customer 物件存取 Order 物件</span><span class="sxs-lookup"><span data-stu-id="647cf-126">To access Order objects by using Customer objects</span></span>  
  
1.  <span data-ttu-id="647cf-127">將下列程式碼輸入或貼到 `Sub Main` 方法，進而修改此方法：</span><span class="sxs-lookup"><span data-stu-id="647cf-127">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2.  <span data-ttu-id="647cf-128">按 F5 對應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="647cf-128">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="647cf-129">訊息方塊中會出現兩個名稱，而主控台視窗則會顯示所產生的 SQL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="647cf-129">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3.  <span data-ttu-id="647cf-130">關閉訊息方塊以停止偵錯。</span><span class="sxs-lookup"><span data-stu-id="647cf-130">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="647cf-131">建立資料庫的強型別檢視</span><span class="sxs-lookup"><span data-stu-id="647cf-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="647cf-132">從資料庫的強型別檢視著手會容易許多。</span><span class="sxs-lookup"><span data-stu-id="647cf-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="647cf-133">透過建立強型別 <xref:System.Data.Linq.DataContext> 物件，您就不需要呼叫 <xref:System.Data.Linq.DataContext.GetTable%2A>。</span><span class="sxs-lookup"><span data-stu-id="647cf-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="647cf-134">當您使用強型別 <xref:System.Data.Linq.DataContext> 物件時，可以在所有查詢中使用強型別資料表。</span><span class="sxs-lookup"><span data-stu-id="647cf-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="647cf-135">在下列步驟中，您會將 `Customers` 建立為強型別資料表，以對應資料庫中的 Customers 資料表。</span><span class="sxs-lookup"><span data-stu-id="647cf-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="647cf-136">若要建立強型別 DataContext 物件</span><span class="sxs-lookup"><span data-stu-id="647cf-136">To strongly type the DataContext object</span></span>  
  
1.  <span data-ttu-id="647cf-137">在 `Customer` 類別宣告之上加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="647cf-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2.  <span data-ttu-id="647cf-138">修改 `Sub Main` 以使用強型別 <xref:System.Data.Linq.DataContext>，如下所示：</span><span class="sxs-lookup"><span data-stu-id="647cf-138">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3.  <span data-ttu-id="647cf-139">按 F5 對應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="647cf-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="647cf-140">主控台視窗輸出為：</span><span class="sxs-lookup"><span data-stu-id="647cf-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4.  <span data-ttu-id="647cf-141">在 [主控台] 視窗中按 Enter 鍵，以關閉應用程式。</span><span class="sxs-lookup"><span data-stu-id="647cf-141">Press Enter in the Console window to close the application.</span></span>  
  
5.  <span data-ttu-id="647cf-142">在**檔案**功能表上，按一下 **全部儲存**如果您想要儲存此應用程式。</span><span class="sxs-lookup"><span data-stu-id="647cf-142">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="647cf-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="647cf-143">Next Steps</span></span>  
 <span data-ttu-id="647cf-144">下一個逐步解說 ([逐步解說： 操作資料 (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) 示範如何處理資料。</span><span class="sxs-lookup"><span data-stu-id="647cf-144">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="647cf-145">該逐步解說並不要求您儲存這系列中已完成的兩個逐步解說。</span><span class="sxs-lookup"><span data-stu-id="647cf-145">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="647cf-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="647cf-146">See Also</span></span>  
 [<span data-ttu-id="647cf-147">依逐步解說學習</span><span class="sxs-lookup"><span data-stu-id="647cf-147">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
