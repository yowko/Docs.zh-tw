---
title: "物件識別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 97c07ce351de5b7939bdcaf441bc46dac50a8c23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="object-identity"></a><span data-ttu-id="1abe2-102">物件識別</span><span class="sxs-lookup"><span data-stu-id="1abe2-102">Object Identity</span></span>
<span data-ttu-id="1abe2-103">執行階段中的物件具有唯一的識別 (Identity)。</span><span class="sxs-lookup"><span data-stu-id="1abe2-103">Objects in the runtime have unique identities.</span></span> <span data-ttu-id="1abe2-104">兩個參考相同物件的變數實際上是參考相同的物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="1abe2-104">Two variables that refer to the same object actually refer to the same instance of the object.</span></span> <span data-ttu-id="1abe2-105">因此，透過經過其中一個變數的路徑進行的變更，可以透過另一個變數立即看到。</span><span class="sxs-lookup"><span data-stu-id="1abe2-105">Because of this fact, changes that you make by way of a path through one variable are immediately visible through the other.</span></span>  
  
 <span data-ttu-id="1abe2-106">關聯式資料庫資料表中的資料列並沒有唯一的識別。</span><span class="sxs-lookup"><span data-stu-id="1abe2-106">Rows in a relational database table do not have unique identities.</span></span> <span data-ttu-id="1abe2-107">因為每個資料列都會有唯一的主索引鍵，所以兩個資料列不會共用相同的索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="1abe2-107">Because each row has a unique primary key, no two rows share the same key value.</span></span> <span data-ttu-id="1abe2-108">不過，這只限於資料庫資料表的內容。</span><span class="sxs-lookup"><span data-stu-id="1abe2-108">However, this fact constrains only the contents of the database table.</span></span>  
  
 <span data-ttu-id="1abe2-109">實際上，最常發生的狀況是從資料庫取出資料，接著將資料放入不同層級，而應用程式會在這些層級中處理資料。</span><span class="sxs-lookup"><span data-stu-id="1abe2-109">In reality, data is most often brought out of the database and into a different tier, where an application works with it.</span></span> <span data-ttu-id="1abe2-110">這是 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援的模型。</span><span class="sxs-lookup"><span data-stu-id="1abe2-110">This is the model that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports.</span></span> <span data-ttu-id="1abe2-111">從資料庫中取出資料並放入資料列時，代表相同資料的兩個資料列實際上並不會對應至相同的資料列執行個體。</span><span class="sxs-lookup"><span data-stu-id="1abe2-111">When data is brought out of the database as rows, you have no expectation that two rows that represent the same data actually correspond to the same row instances.</span></span> <span data-ttu-id="1abe2-112">如果查詢特定客戶兩次，便會有兩列資料。</span><span class="sxs-lookup"><span data-stu-id="1abe2-112">If you query for a specific customer two times, you get two rows of data.</span></span> <span data-ttu-id="1abe2-113">而每個資料列會包含相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="1abe2-113">Each row contains the same information.</span></span>  
  
 <span data-ttu-id="1abe2-114">利用物件時，所進行的方式則相當不同。</span><span class="sxs-lookup"><span data-stu-id="1abe2-114">With objects you expect something very different.</span></span> <span data-ttu-id="1abe2-115">如果重複向 <xref:System.Data.Linq.DataContext> 要求相同資訊，則實際上提供給您的會是相同的物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="1abe2-115">You expect that if you ask the <xref:System.Data.Linq.DataContext> for the same information repeatedly, it will in fact give you the same object instance.</span></span> <span data-ttu-id="1abe2-116">因為物件對您的應用程式有特殊意義，而您預期它們會像物件一樣作業，所以您預期會發生上述行為。</span><span class="sxs-lookup"><span data-stu-id="1abe2-116">You expect this behavior because objects have special meaning for your application and you expect them to behave like objects.</span></span> <span data-ttu-id="1abe2-117">您已將它們設計為階層架構或圖形。</span><span class="sxs-lookup"><span data-stu-id="1abe2-117">You designed them as hierarchies or graphs.</span></span> <span data-ttu-id="1abe2-118">因為您多次要求相同的事項，所以希望以這類方式擷取它們，而不要接收已複寫執行個體的各個部分。</span><span class="sxs-lookup"><span data-stu-id="1abe2-118">You expect to retrieve them as such and not to receive multitudes of replicated instances just because you asked for the same thing more than one time.</span></span>  
  
 <span data-ttu-id="1abe2-119">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Data.Linq.DataContext> 會管理物件識別。</span><span class="sxs-lookup"><span data-stu-id="1abe2-119">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.DataContext> manages object identity.</span></span> <span data-ttu-id="1abe2-120">只要從資料庫擷取新的資料列，就會根據該資料列的主索引鍵將該資料列記錄到識別表中，而且會建立新的物件。</span><span class="sxs-lookup"><span data-stu-id="1abe2-120">Whenever you retrieve a new row from the database, the row is logged in an identity table by its primary key, and a new object is created.</span></span> <span data-ttu-id="1abe2-121">每次擷取那個相同的資料列時，就會將原始物件執行個體交還給應用程式。</span><span class="sxs-lookup"><span data-stu-id="1abe2-121">Whenever you retrieve that same row, the original object instance is handed back to the application.</span></span> <span data-ttu-id="1abe2-122">利用這種方式，<xref:System.Data.Linq.DataContext> 會將資料庫看到的識別概念 (即主索引鍵) 轉譯為語言看到的識別概念 (即執行個體)。</span><span class="sxs-lookup"><span data-stu-id="1abe2-122">In this manner the <xref:System.Data.Linq.DataContext> translates the concept of identity as seen by the database (that is, primary keys) into the concept of identity seen by the language (that is, instances).</span></span> <span data-ttu-id="1abe2-123">而應用程式只會看到物件在它第一次擷取物件時的狀態。</span><span class="sxs-lookup"><span data-stu-id="1abe2-123">The application only sees the object in the state that it was first retrieved.</span></span> <span data-ttu-id="1abe2-124">如果新資料的狀態不同則會予以捨棄。</span><span class="sxs-lookup"><span data-stu-id="1abe2-124">The new data, if different, is discarded.</span></span> <span data-ttu-id="1abe2-125">如需詳細資訊，請參閱[擷取物件從識別快取](../../../../../../docs/framework/data/adonet/sql/linq/retrieving-objects-from-the-identity-cache.md)。</span><span class="sxs-lookup"><span data-stu-id="1abe2-125">For more information, see [Retrieving Objects from the Identity Cache](../../../../../../docs/framework/data/adonet/sql/linq/retrieving-objects-from-the-identity-cache.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1abe2-126">您可以使用此方式來管理本機物件的完整性，以便支援開放式的更新。</span><span class="sxs-lookup"><span data-stu-id="1abe2-126"> uses this approach to manage the integrity of local objects in order to support optimistic updates.</span></span> <span data-ttu-id="1abe2-127">因為只有在第一次建立物件之後發生的變更才是應用程式進行的變更，所以應用程式的意圖十分清楚。</span><span class="sxs-lookup"><span data-stu-id="1abe2-127">Because the only changes that occur after the object is at first created are those made by the application, the intent of the application is clear.</span></span> <span data-ttu-id="1abe2-128">如果外部群體在其間也進行了變更，則會在呼叫 `SubmitChanges()` 時識別這些變更。</span><span class="sxs-lookup"><span data-stu-id="1abe2-128">If changes by an outside party have occurred in the interim, they are identified at the time `SubmitChanges()` is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1abe2-129">如果查詢要求的物件可以輕易識別為已擷取的物件，則不會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="1abe2-129">If the object requested by the query is easily identifiable as one already retrieved, no query is executed.</span></span> <span data-ttu-id="1abe2-130">識別表是當成所有先前擷取過物件的快取。</span><span class="sxs-lookup"><span data-stu-id="1abe2-130">The identity table acts as a cache of all previously retrieved objects.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1abe2-131">範例</span><span class="sxs-lookup"><span data-stu-id="1abe2-131">Examples</span></span>  
  
### <a name="object-caching-example-1"></a><span data-ttu-id="1abe2-132">物件快取範例 1</span><span class="sxs-lookup"><span data-stu-id="1abe2-132">Object Caching Example 1</span></span>  
 <span data-ttu-id="1abe2-133">在這個範例中，如果執行相同的查詢兩次，則每次都會接收到記憶體中相同物件的參考。</span><span class="sxs-lookup"><span data-stu-id="1abe2-133">In this example, if you execute the same query two times, you receive a reference to the same object in memory every time.</span></span>  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a><span data-ttu-id="1abe2-134">物件快取範例 2</span><span class="sxs-lookup"><span data-stu-id="1abe2-134">Object Caching Example 2</span></span>  
 <span data-ttu-id="1abe2-135">在這個範例中，如果執行不同的查詢從資料庫中傳回相同的資料列，則每次都會接收到記憶體中相同物件的參考。</span><span class="sxs-lookup"><span data-stu-id="1abe2-135">In this example, if you execute different queries that return the same row from the database, you receive a reference to the same object in memory every time.</span></span>  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1abe2-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1abe2-136">See Also</span></span>  
 [<span data-ttu-id="1abe2-137">背景資訊</span><span class="sxs-lookup"><span data-stu-id="1abe2-137">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
