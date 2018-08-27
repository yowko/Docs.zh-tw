---
title: 開放式並行存取
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: 0b4cdfa7bab1f41f80926b20da3e63a72a2d165d
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "42911996"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="ee8ac-102">開放式並行存取</span><span class="sxs-lookup"><span data-stu-id="ee8ac-102">Optimistic Concurrency</span></span>
<span data-ttu-id="ee8ac-103">在多使用者環境中，更新資料庫中的資料時，有兩種模型可供使用：開放式並行存取和封閉式並行存取。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-103">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="ee8ac-104"><xref:System.Data.DataSet> 物件的設計是要鼓勵使用者在進行長時間的活動 (如遠端處理資料以及與資料進行互動) 時，採用開放式同步存取。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-104">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="ee8ac-105">封閉式同步存取涉及鎖定資料來源的資料列，以免其他使用者修改資料而影響目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-105">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="ee8ac-106">在封閉式模型中，當使用者執行某項作業而造成鎖定時，其他使用者在鎖定擁有人解除鎖定前，都無法執行會與鎖定衝突的動作。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-106">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="ee8ac-107">這個模型主要應用的環境是經常爭用資料，其鎖定保護資料的成本低於發生並行衝突時復原交易的成本。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-107">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="ee8ac-108">因此在封閉式並行存取模型中，使用者若更新資料列，即會造成鎖定。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-108">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="ee8ac-109">使用者尚未完成更新並解除鎖定前，其他人都不能變更這個資料列。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-109">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="ee8ac-110">因此，封閉式同步存取最適合應用於鎖定時間短的情況，就像以程式設計的方式處理記錄的情況。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-110">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="ee8ac-111">由於使用者與資料互動時，會使記錄被鎖定較長的時間，因此封閉式同步存取方式的彈性並不高。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-111">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee8ac-112">如果您需要在相同作業中更新多個資料列，則建立交易是比使用封閉式鎖定 (Pessimistic Locking) 更具擴充性的選項。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-112">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="ee8ac-113">相較下，採用開放式同步存取的使用者不需要鎖定資料列即可進行讀取。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-113">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="ee8ac-114">使用者想要更新資料列時，應用程式必須判斷該資料列自從上次讀取後，是否已由另一位使用者變更。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-114">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="ee8ac-115">開放式同步存取一般用於不常爭用資料的環境。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-115">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="ee8ac-116">開放式同步存取不需鎖定記錄，因此能改善效能，而鎖定記錄則需要額外的伺服器資源。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-116">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="ee8ac-117">此外，為了保持記錄鎖定，必須要持續連接至資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-117">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="ee8ac-118">由於開放式同步存取模型沒有這種限制，因此可讓數量龐大的用戶端花費更少的時間連接至伺服器。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-118">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="ee8ac-119">開放式同步存取模型中，如果使用者甲已收到來自資料庫的值，而這時使用者乙搶在使用者甲之前修改這個值，便會被視為發生違規。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-119">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="ee8ac-120">若要瞭解伺服器解決並行存取違規的方式，最好先從下列範例的說明開始。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-120">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="ee8ac-121">下列表格代表開放式同步存取的範例。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-121">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="ee8ac-122">在下午 1:00 時，User1 從資料庫讀取出資料列，取得下列的值：</span><span class="sxs-lookup"><span data-stu-id="ee8ac-122">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="ee8ac-123">**CustID LastName FirstName**</span><span class="sxs-lookup"><span data-stu-id="ee8ac-123">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="ee8ac-124">101 Smith Bob</span><span class="sxs-lookup"><span data-stu-id="ee8ac-124">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="ee8ac-125">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="ee8ac-125">Column name</span></span>|<span data-ttu-id="ee8ac-126">原始值</span><span class="sxs-lookup"><span data-stu-id="ee8ac-126">Original value</span></span>|<span data-ttu-id="ee8ac-127">目前值</span><span class="sxs-lookup"><span data-stu-id="ee8ac-127">Current value</span></span>|<span data-ttu-id="ee8ac-128">資料庫中的值</span><span class="sxs-lookup"><span data-stu-id="ee8ac-128">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="ee8ac-129">CustID</span><span class="sxs-lookup"><span data-stu-id="ee8ac-129">CustID</span></span>|<span data-ttu-id="ee8ac-130">101</span><span class="sxs-lookup"><span data-stu-id="ee8ac-130">101</span></span>|<span data-ttu-id="ee8ac-131">101</span><span class="sxs-lookup"><span data-stu-id="ee8ac-131">101</span></span>|<span data-ttu-id="ee8ac-132">101</span><span class="sxs-lookup"><span data-stu-id="ee8ac-132">101</span></span>|  
|<span data-ttu-id="ee8ac-133">LastName</span><span class="sxs-lookup"><span data-stu-id="ee8ac-133">LastName</span></span>|<span data-ttu-id="ee8ac-134">Smith</span><span class="sxs-lookup"><span data-stu-id="ee8ac-134">Smith</span></span>|<span data-ttu-id="ee8ac-135">Smith</span><span class="sxs-lookup"><span data-stu-id="ee8ac-135">Smith</span></span>|<span data-ttu-id="ee8ac-136">Smith</span><span class="sxs-lookup"><span data-stu-id="ee8ac-136">Smith</span></span>|  
|<span data-ttu-id="ee8ac-137">FirstName</span><span class="sxs-lookup"><span data-stu-id="ee8ac-137">FirstName</span></span>|<span data-ttu-id="ee8ac-138">Bob</span><span class="sxs-lookup"><span data-stu-id="ee8ac-138">Bob</span></span>|<span data-ttu-id="ee8ac-139">Bob</span><span class="sxs-lookup"><span data-stu-id="ee8ac-139">Bob</span></span>|<span data-ttu-id="ee8ac-140">Bob</span><span class="sxs-lookup"><span data-stu-id="ee8ac-140">Bob</span></span>|  
  
 <span data-ttu-id="ee8ac-141">在下午 1:01 時，User2 讀取同一資料列。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-141">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="ee8ac-142">在下午 1:03 時，變更 User2 **FirstName**從"Bob"為"Robert"，並更新資料庫。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-142">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="ee8ac-143">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="ee8ac-143">Column name</span></span>|<span data-ttu-id="ee8ac-144">原始值</span><span class="sxs-lookup"><span data-stu-id="ee8ac-144">Original value</span></span>|<span data-ttu-id="ee8ac-145">目前值</span><span class="sxs-lookup"><span data-stu-id="ee8ac-145">Current value</span></span>|<span data-ttu-id="ee8ac-146">資料庫中的值</span><span class="sxs-lookup"><span data-stu-id="ee8ac-146">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="ee8ac-147">CustID</span><span class="sxs-lookup"><span data-stu-id="ee8ac-147">CustID</span></span>|<span data-ttu-id="ee8ac-148">101</span><span class="sxs-lookup"><span data-stu-id="ee8ac-148">101</span></span>|<span data-ttu-id="ee8ac-149">101</span><span class="sxs-lookup"><span data-stu-id="ee8ac-149">101</span></span>|<span data-ttu-id="ee8ac-150">101</span><span class="sxs-lookup"><span data-stu-id="ee8ac-150">101</span></span>|  
|<span data-ttu-id="ee8ac-151">LastName</span><span class="sxs-lookup"><span data-stu-id="ee8ac-151">LastName</span></span>|<span data-ttu-id="ee8ac-152">Smith</span><span class="sxs-lookup"><span data-stu-id="ee8ac-152">Smith</span></span>|<span data-ttu-id="ee8ac-153">Smith</span><span class="sxs-lookup"><span data-stu-id="ee8ac-153">Smith</span></span>|<span data-ttu-id="ee8ac-154">Smith</span><span class="sxs-lookup"><span data-stu-id="ee8ac-154">Smith</span></span>|  
|<span data-ttu-id="ee8ac-155">FirstName</span><span class="sxs-lookup"><span data-stu-id="ee8ac-155">FirstName</span></span>|<span data-ttu-id="ee8ac-156">Bob</span><span class="sxs-lookup"><span data-stu-id="ee8ac-156">Bob</span></span>|<span data-ttu-id="ee8ac-157">Robert</span><span class="sxs-lookup"><span data-stu-id="ee8ac-157">Robert</span></span>|<span data-ttu-id="ee8ac-158">Bob</span><span class="sxs-lookup"><span data-stu-id="ee8ac-158">Bob</span></span>|  
  
 <span data-ttu-id="ee8ac-159">更新成功，因為更新時資料庫中的值符合 User2 擁有的原始值。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-159">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="ee8ac-160">在下午 1:05 時，User1 將 "Bob" 的名字變更為 "James"，並嘗試更新資料列。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-160">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="ee8ac-161">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="ee8ac-161">Column name</span></span>|<span data-ttu-id="ee8ac-162">原始值</span><span class="sxs-lookup"><span data-stu-id="ee8ac-162">Original value</span></span>|<span data-ttu-id="ee8ac-163">目前值</span><span class="sxs-lookup"><span data-stu-id="ee8ac-163">Current value</span></span>|<span data-ttu-id="ee8ac-164">資料庫中的值</span><span class="sxs-lookup"><span data-stu-id="ee8ac-164">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="ee8ac-165">CustID</span><span class="sxs-lookup"><span data-stu-id="ee8ac-165">CustID</span></span>|<span data-ttu-id="ee8ac-166">101</span><span class="sxs-lookup"><span data-stu-id="ee8ac-166">101</span></span>|<span data-ttu-id="ee8ac-167">101</span><span class="sxs-lookup"><span data-stu-id="ee8ac-167">101</span></span>|<span data-ttu-id="ee8ac-168">101</span><span class="sxs-lookup"><span data-stu-id="ee8ac-168">101</span></span>|  
|<span data-ttu-id="ee8ac-169">LastName</span><span class="sxs-lookup"><span data-stu-id="ee8ac-169">LastName</span></span>|<span data-ttu-id="ee8ac-170">Smith</span><span class="sxs-lookup"><span data-stu-id="ee8ac-170">Smith</span></span>|<span data-ttu-id="ee8ac-171">Smith</span><span class="sxs-lookup"><span data-stu-id="ee8ac-171">Smith</span></span>|<span data-ttu-id="ee8ac-172">Smith</span><span class="sxs-lookup"><span data-stu-id="ee8ac-172">Smith</span></span>|  
|<span data-ttu-id="ee8ac-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="ee8ac-173">FirstName</span></span>|<span data-ttu-id="ee8ac-174">Bob</span><span class="sxs-lookup"><span data-stu-id="ee8ac-174">Bob</span></span>|<span data-ttu-id="ee8ac-175">James</span><span class="sxs-lookup"><span data-stu-id="ee8ac-175">James</span></span>|<span data-ttu-id="ee8ac-176">Robert</span><span class="sxs-lookup"><span data-stu-id="ee8ac-176">Robert</span></span>|  
  
 <span data-ttu-id="ee8ac-177">此時，User1 發生了開放式並行存取違規的情況，因為資料庫中的值 ("Robert") 不再符合 User1 原先預期的原始值 ("Bob")。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-177">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="ee8ac-178">並行違規只是讓您瞭解更新失敗。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-178">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="ee8ac-179">現在必須決定要用 User1 所做的變更覆寫 User2 的變更，或是取消 User1 做的變更。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-179">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="ee8ac-180">測試開放式同步存取違規</span><span class="sxs-lookup"><span data-stu-id="ee8ac-180">Testing for Optimistic Concurrency Violations</span></span>  
 <span data-ttu-id="ee8ac-181">有數種技巧可測試開放式同步存取違規。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-181">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="ee8ac-182">其中一種是將時間戳記資料行納入資料表中。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-182">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="ee8ac-183">資料庫一般會提供時間戳記功能，可用來辨識記錄上回更新的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-183">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="ee8ac-184">採用這項技巧時，資料表定義會包含時間戳記資料行。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-184">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="ee8ac-185">只要記錄一更新，時間戳記便會隨之更新以反映目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-185">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="ee8ac-186">開放式同步存取違規測試中，時間戳記資料行會隨著資料表的任何內容查詢傳回。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-186">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="ee8ac-187">嘗試更新時，資料庫中時間戳記的值便會與修改過之資料列中所含的原始時間戳記值比較。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-187">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="ee8ac-188">若兩值相符，就會執行更新，並以目前的時間來更新時間戳記資料行的值以反映更新。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-188">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="ee8ac-189">若兩值不符，就會發生開放式同步存取違規。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-189">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="ee8ac-190">另一個測試開放式同步存取違規的技巧，是驗證資料列內所有原始資料行的值是否仍然符合資料庫中的值。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-190">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="ee8ac-191">例如，請考量下列查詢：</span><span class="sxs-lookup"><span data-stu-id="ee8ac-191">For example, consider the following query:</span></span>  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="ee8ac-192">若要更新中的資料列時，測試開放式同步存取違規**Table1**，您可以發出下列 UPDATE 陳述式：</span><span class="sxs-lookup"><span data-stu-id="ee8ac-192">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="ee8ac-193">只要原始值符合資料庫中的值，便會執行更新。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-193">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="ee8ac-194">若值已經修改，更新作業不會修改資料列，因為 WHERE 子句找不到符合的項目。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-194">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="ee8ac-195">請注意，建議您永遠在查詢中傳回唯一的主索引鍵值；</span><span class="sxs-lookup"><span data-stu-id="ee8ac-195">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="ee8ac-196">否則，之前的 UPDATE 陳述式可能更新一個以上的資料列，而這可能與您的意圖相違。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-196">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="ee8ac-197">若您資料來源內的資料行允許 Null，則可能必須擴充 WHERE 子句，以檢查區域資料表和資料來源內是否有相符的 Null 參考。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-197">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="ee8ac-198">例如，下列 UPDATE 陳述式驗證區域資料列中的 Null 參考仍然與資料來源的 Null 參考相符，或是區域資料列的值仍然與資料來源的值相符。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-198">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="ee8ac-199">使用開放式同步存取模型時，您也可以選擇套用較寬鬆的準則。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-199">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="ee8ac-200">例如，在 WHERE 子句中僅使用主索引鍵資料行時，不論另一個資料行在上次查詢後是否曾更新，都會覆寫資料。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-200">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="ee8ac-201">您也可以只在特定資料行套用 WHERE 子句，以覆寫資料 (除非特定欄位在上次查詢後已經更新)。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-201">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="ee8ac-202">DataAdapter.RowUpdated 事件</span><span class="sxs-lookup"><span data-stu-id="ee8ac-202">The DataAdapter.RowUpdated Event</span></span>  
 <span data-ttu-id="ee8ac-203">**RowUpdated**事件的<xref:System.Data.Common.DataAdapter>物件可以搭配使用，技巧如先前所述，以提供您的應用程式的開放式並行存取違規的通知。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-203">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="ee8ac-204">**RowUpdated**每次嘗試更新之後，就會發生**Modified**中的資料列**DataSet**。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-204">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="ee8ac-205">如此可讓您加入特殊處理程式碼，包括發生例外狀況時的處理、加入自訂錯誤資訊、加入重試邏輯等等。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-205">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="ee8ac-206"><xref:System.Data.Common.RowUpdatedEventArgs>物件會傳回**RecordsAffected**屬性包含所修改的資料列，資料表中的特定更新命令影響的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-206">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="ee8ac-207">藉由設定更新命令以測試開放式同步存取**RecordsAffected**屬性會如此一來，傳回值為 0 時已經發生開放式同步存取違規，因為已不更新的任何記錄。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-207">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="ee8ac-208">若發生這種情況，就會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-208">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="ee8ac-209">**RowUpdated**事件可讓您處理這項問題，並避免例外狀況的設定適當**RowUpdatedEventArgs.Status**值，例如**UpdateStatus.SkipCurrentRow**。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-209">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="ee8ac-210">如需詳細資訊**RowUpdated**事件，請參閱[處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-210">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="ee8ac-211">（選擇性） 您可以設定**DataAdapter.ContinueUpdateOnError**要 **，則為 true**，然後再呼叫**Update**，並回應錯誤資訊儲存在**RowError**屬性的特定資料列時**更新**完成。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-211">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="ee8ac-212">如需詳細資訊，請參閱 <<c0> [ 資料列錯誤資訊](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-212">For more information, see [Row Error Information](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="ee8ac-213">開放式同步存取範例</span><span class="sxs-lookup"><span data-stu-id="ee8ac-213">Optimistic Concurrency Example</span></span>  
 <span data-ttu-id="ee8ac-214">以下是簡單的範例，以設定**UpdateCommand**的**DataAdapter**以測試開放式同步存取，然後使用**RowUpdated**事件以測試開放式同步存取違規。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-214">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="ee8ac-215">發生開放式同步存取違規時，應用程式設定**RowError**更新以反映開放式同步存取違規，所發出的資料列。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-215">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="ee8ac-216">請注意，傳遞至更新命令的 WHERE 子句的參數值會對應至**原始**其各自的資料行的值。</span><span class="sxs-lookup"><span data-stu-id="ee8ac-216">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = dataSet.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then   
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)   
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee8ac-217">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee8ac-217">See Also</span></span>  
 [<span data-ttu-id="ee8ac-218">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="ee8ac-218">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="ee8ac-219">使用 DataAdapter 更新資料來源</span><span class="sxs-lookup"><span data-stu-id="ee8ac-219">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="ee8ac-220">資料列錯誤資訊</span><span class="sxs-lookup"><span data-stu-id="ee8ac-220">Row Error Information</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 [<span data-ttu-id="ee8ac-221">異動和並行存取</span><span class="sxs-lookup"><span data-stu-id="ee8ac-221">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="ee8ac-222">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="ee8ac-222">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
