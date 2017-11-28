---
title: "開發人員覆寫預設行為的責任"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4792967bb21912e475c32c0f37149b89a838b133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a><span data-ttu-id="07186-102">開發人員覆寫預設行為的責任</span><span class="sxs-lookup"><span data-stu-id="07186-102">Responsibilities of the Developer In Overriding Default Behavior</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="07186-103">不會強制下列需求，但如果不滿足這些需求，行為是未定義。</span><span class="sxs-lookup"><span data-stu-id="07186-103"> does not enforce the following requirements, but behavior is undefined if these requirements are not satisfied.</span></span>  
  
-   <span data-ttu-id="07186-104">覆寫方法不得呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 或 <xref:System.Data.Linq.Table%601.Attach%2A>。</span><span class="sxs-lookup"><span data-stu-id="07186-104">The overriding method must not call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> or <xref:System.Data.Linq.Table%601.Attach%2A>.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="07186-105">如果覆寫方法中呼叫這些方法時，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="07186-105"> throws an exception if these methods are called in an override method.</span></span>  
  
-   <span data-ttu-id="07186-106">覆寫方法不可以用來啟動、認可或停止交易。</span><span class="sxs-lookup"><span data-stu-id="07186-106">Override methods cannot be used to start, commit, or stop a transaction.</span></span> <span data-ttu-id="07186-107"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> 作業是在交易下執行。</span><span class="sxs-lookup"><span data-stu-id="07186-107">The <xref:System.Data.Linq.DataContext.SubmitChanges%2A> operation is performed under a transaction.</span></span> <span data-ttu-id="07186-108">而內部巢狀交易會干擾外部交易。</span><span class="sxs-lookup"><span data-stu-id="07186-108">An inner nested transaction can interfere with the outer transaction.</span></span> <span data-ttu-id="07186-109">只有在載入覆寫方法判斷作業未在 <xref:System.Transactions.Transaction> 中執行之後，載入覆寫方法才可以啟動交易。</span><span class="sxs-lookup"><span data-stu-id="07186-109">Load override methods can start a transaction only after they determine that the operation is not being performed in a <xref:System.Transactions.Transaction>.</span></span>  
  
-   <span data-ttu-id="07186-110">需要有覆寫方法，才能遵循適用的開放式並行存取 (Optimistic Concurrency) 對應。</span><span class="sxs-lookup"><span data-stu-id="07186-110">Override methods are expected to follow the applicable optimistic concurrency mapping.</span></span> <span data-ttu-id="07186-111">開放式並行存取發生衝突時，覆寫方法應該會擲回 <xref:System.Data.Linq.ChangeConflictException>。</span><span class="sxs-lookup"><span data-stu-id="07186-111">The override method is expected to throw a <xref:System.Data.Linq.ChangeConflictException> when an optimistic concurrency conflict occurs.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="07186-112">會攔截此例外狀況，以便您可以正確地處理<xref:System.Data.Linq.DataContext.SubmitChanges%2A>上提供選項<xref:System.Data.Linq.DataContext.SubmitChanges%2A>。</span><span class="sxs-lookup"><span data-stu-id="07186-112"> catches this exception so that you can correctly process the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> option provided on <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span>  
  
-   <span data-ttu-id="07186-113">作業順利完成時，則需要建立 (`Insert`) 和 `Update` 覆寫方法將資料庫所產生的資料行值送回給對應的物件成員。</span><span class="sxs-lookup"><span data-stu-id="07186-113">Create (`Insert`) and `Update` override methods are expected to flow back the values for database-generated columns to corresponding object members when the operation is successfully completed.</span></span>  
  
     <span data-ttu-id="07186-114">例如，如果`Order.OrderID`對應至識別資料行 (*autoincrement*主索引鍵)，則`InsertOrder()`覆寫方法必須擷取資料庫產生的識別碼，並設定`Order.OrderID`成員為該 id。</span><span class="sxs-lookup"><span data-stu-id="07186-114">For example, if `Order.OrderID` is mapped to an identity column (*autoincrement* primary key), then the `InsertOrder()` override method must retrieve the database-generated ID and set the `Order.OrderID` member to that ID.</span></span> <span data-ttu-id="07186-115">同樣地，必須將時間戳記成員更新為資料庫產生的時間戳記值，以確定更新的物件一致。</span><span class="sxs-lookup"><span data-stu-id="07186-115">Likewise, timestamp members must be updated to the database-generated timestamp values to make sure that the updated objects are consistent.</span></span> <span data-ttu-id="07186-116">散佈資料庫產生的值失敗，會造成資料庫與 <xref:System.Data.Linq.DataContext> 追蹤的物件不一致。</span><span class="sxs-lookup"><span data-stu-id="07186-116">Failure to propagate the database-generated values can cause an inconsistency between the database and the objects tracked by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
-   <span data-ttu-id="07186-117">使用者必須負責叫用 (Invoke) 正確的動態 API。</span><span class="sxs-lookup"><span data-stu-id="07186-117">It is the user's responsibility to invoke the correct dynamic API.</span></span> <span data-ttu-id="07186-118">例如，在更新覆寫方法中，您只能呼叫 <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A>。</span><span class="sxs-lookup"><span data-stu-id="07186-118">For example, in the update override method, only the <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> can be called.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="07186-119"> 並不會偵測或驗證所叫用的動態方法是否符合適用的作業。</span><span class="sxs-lookup"><span data-stu-id="07186-119"> does not detect or verify whether the invoked dynamic method matches the applicable operation.</span></span> <span data-ttu-id="07186-120">如果呼叫不適用的方法 (例如，對要更新的物件呼叫 <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A>)，則會產生無法定義的結果。</span><span class="sxs-lookup"><span data-stu-id="07186-120">If an inapplicable method is called (for example, <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> for an object to be updated), the results are undefined.</span></span>  
  
-   <span data-ttu-id="07186-121">最後，需要有覆寫方法才能執行陳述的作業。</span><span class="sxs-lookup"><span data-stu-id="07186-121">Finally, the overriding method is expected to perform the stated operation.</span></span> <span data-ttu-id="07186-122">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 作業 (例如立即載入、延後載入和 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) 的語意 (Semantics) 需要有覆寫，才能提供陳述的服務。</span><span class="sxs-lookup"><span data-stu-id="07186-122">The semantics of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] operations such as eager loading, deferred loading, and <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) require the overrides to provide the stated service.</span></span> <span data-ttu-id="07186-123">例如，只傳回空集合而不檢查資料庫內容的載入覆寫，可能會導致資料不一致。</span><span class="sxs-lookup"><span data-stu-id="07186-123">For example, a load override that just returns an empty collection without checking the contents in the database will likely lead to inconsistent data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07186-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07186-124">See Also</span></span>  
 [<span data-ttu-id="07186-125">自訂插入、 更新和刪除作業</span><span class="sxs-lookup"><span data-stu-id="07186-125">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
