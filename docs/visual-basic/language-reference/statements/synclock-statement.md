---
title: SyncLock 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: cc8706b95e0785459e36abe27ce915b5bab8711a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875195"
---
# <a name="synclock-statement"></a><span data-ttu-id="c3152-102">SyncLock 陳述式</span><span class="sxs-lookup"><span data-stu-id="c3152-102">SyncLock Statement</span></span>

<span data-ttu-id="c3152-103">在執行區塊之前，取得語句區塊的獨佔鎖定。</span><span class="sxs-lookup"><span data-stu-id="c3152-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3152-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c3152-104">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="c3152-105">組件</span><span class="sxs-lookup"><span data-stu-id="c3152-105">Parts</span></span>  

 `lockobject`  
 <span data-ttu-id="c3152-106">必要。</span><span class="sxs-lookup"><span data-stu-id="c3152-106">Required.</span></span> <span data-ttu-id="c3152-107">評估為物件參考的運算式。</span><span class="sxs-lookup"><span data-stu-id="c3152-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="c3152-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c3152-108">Optional.</span></span> <span data-ttu-id="c3152-109">取得鎖定時要執行的語句區塊。</span><span class="sxs-lookup"><span data-stu-id="c3152-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="c3152-110">終止 `SyncLock` 區塊。</span><span class="sxs-lookup"><span data-stu-id="c3152-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3152-111">備註</span><span class="sxs-lookup"><span data-stu-id="c3152-111">Remarks</span></span>  

 <span data-ttu-id="c3152-112">`SyncLock`語句可確保多個執行緒不會同時執行語句區塊。</span><span class="sxs-lookup"><span data-stu-id="c3152-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="c3152-113">`SyncLock` 防止每個執行緒進入區塊，直到沒有其他執行緒執行為止。</span><span class="sxs-lookup"><span data-stu-id="c3152-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="c3152-114">最常見的用法 `SyncLock` 是防止多個執行緒同時更新資料。</span><span class="sxs-lookup"><span data-stu-id="c3152-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="c3152-115">如果運算元據的語句必須在不中斷的情況下移至完成，請將它們放在 `SyncLock` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="c3152-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="c3152-116">獨佔鎖定所保護的語句區塊有時也稱為 *重要區段*。</span><span class="sxs-lookup"><span data-stu-id="c3152-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c3152-117">規則</span><span class="sxs-lookup"><span data-stu-id="c3152-117">Rules</span></span>  
  
- <span data-ttu-id="c3152-118">分支。</span><span class="sxs-lookup"><span data-stu-id="c3152-118">Branching.</span></span> <span data-ttu-id="c3152-119">您無法 `SyncLock` 從區塊外部分支至區塊。</span><span class="sxs-lookup"><span data-stu-id="c3152-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="c3152-120">鎖定物件的值。</span><span class="sxs-lookup"><span data-stu-id="c3152-120">Lock Object Value.</span></span> <span data-ttu-id="c3152-121">的值 `lockobject` 不能是 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="c3152-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="c3152-122">您必須先建立鎖定物件，才能在語句中使用它 `SyncLock` 。</span><span class="sxs-lookup"><span data-stu-id="c3152-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="c3152-123">`lockobject`當您執行區塊時，無法變更的值 `SyncLock` 。</span><span class="sxs-lookup"><span data-stu-id="c3152-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="c3152-124">機制要求鎖定物件保持不變。</span><span class="sxs-lookup"><span data-stu-id="c3152-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="c3152-125">您無法在區塊中使用 [Await](../operators/await-operator.md) 運算子 `SyncLock` 。</span><span class="sxs-lookup"><span data-stu-id="c3152-125">You can't use the [Await](../operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="c3152-126">行為</span><span class="sxs-lookup"><span data-stu-id="c3152-126">Behavior</span></span>  
  
- <span data-ttu-id="c3152-127">機制。</span><span class="sxs-lookup"><span data-stu-id="c3152-127">Mechanism.</span></span> <span data-ttu-id="c3152-128">當執行緒到達語句時 `SyncLock` ，它會評估 `lockobject` 運算式並暫停執行，直到它取得運算式所傳回物件的獨佔鎖定為止。</span><span class="sxs-lookup"><span data-stu-id="c3152-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="c3152-129">當另一個執行緒到達 `SyncLock` 語句時，它不會取得鎖定，直到第一個執行緒執行 `End SyncLock` 語句為止。</span><span class="sxs-lookup"><span data-stu-id="c3152-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="c3152-130">受保護的資料。</span><span class="sxs-lookup"><span data-stu-id="c3152-130">Protected Data.</span></span> <span data-ttu-id="c3152-131">如果 `lockobject` 是 `Shared` 變數，獨佔鎖定會防止類別的任何實例中的執行緒在 `SyncLock` 執行任何其他執行緒時執行區塊。</span><span class="sxs-lookup"><span data-stu-id="c3152-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="c3152-132">這會保護所有實例之間共用的資料。</span><span class="sxs-lookup"><span data-stu-id="c3152-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="c3152-133">如果 `lockobject` 是執行個體變數 (不 `Shared`) ，則鎖定會防止在目前的實例中執行的執行緒，與 `SyncLock` 相同實例中的另一個執行緒在同一時間執行區塊。</span><span class="sxs-lookup"><span data-stu-id="c3152-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="c3152-134">這可保護個別實例所維護的資料。</span><span class="sxs-lookup"><span data-stu-id="c3152-134">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="c3152-135">取得和釋放。</span><span class="sxs-lookup"><span data-stu-id="c3152-135">Acquisition and Release.</span></span> <span data-ttu-id="c3152-136">`SyncLock`區塊的行為就像是一個 `Try...Finally` 結構，其中 `Try` 區塊會取得獨佔鎖定 `lockobject` ，而 `Finally` 區塊則會釋放它。</span><span class="sxs-lookup"><span data-stu-id="c3152-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="c3152-137">因此，不論 `SyncLock` 您離開區塊的方式為何，區塊都會保證鎖定的版本。</span><span class="sxs-lookup"><span data-stu-id="c3152-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="c3152-138">即使是未處理的例外狀況，也是如此。</span><span class="sxs-lookup"><span data-stu-id="c3152-138">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="c3152-139">架構呼叫。</span><span class="sxs-lookup"><span data-stu-id="c3152-139">Framework Calls.</span></span> <span data-ttu-id="c3152-140">區塊會藉 `SyncLock` 由呼叫 `Enter` `Exit` `Monitor` 命名空間中類別的和方法，來取得和釋放獨佔鎖定 <xref:System.Threading> 。</span><span class="sxs-lookup"><span data-stu-id="c3152-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="c3152-141">程式設計實務</span><span class="sxs-lookup"><span data-stu-id="c3152-141">Programming Practices</span></span>  

 <span data-ttu-id="c3152-142">`lockobject`運算式應該一律評估為屬於您類別的物件。</span><span class="sxs-lookup"><span data-stu-id="c3152-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="c3152-143">您應宣告 `Private` 物件變數來保護屬於目前實例的資料，或使用 `Private Shared` 物件變數來保護所有實例的通用資料。</span><span class="sxs-lookup"><span data-stu-id="c3152-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="c3152-144">您不應該使用 `Me` 關鍵字來提供實例資料的鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="c3152-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="c3152-145">如果您類別的外部程式碼具有類別實例的參考，則可以使用該參考做為與您的 `SyncLock` 區塊完全不同的鎖定物件，以保護不同的資料。</span><span class="sxs-lookup"><span data-stu-id="c3152-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="c3152-146">如此一來，您的類別和其他類別可能會彼此封鎖，使其無法執行不相關的 `SyncLock` 區塊。</span><span class="sxs-lookup"><span data-stu-id="c3152-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="c3152-147">同樣地，鎖定字串可能會造成問題，因為進程中任何其他程式碼使用相同的字串將共用相同的鎖定。</span><span class="sxs-lookup"><span data-stu-id="c3152-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="c3152-148">您也不應該使用 `Me.GetType` 方法來提供共用資料的鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="c3152-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="c3152-149">這是因為 `GetType` 一律會 `Type` 針對指定的類別名稱傳回相同的物件。</span><span class="sxs-lookup"><span data-stu-id="c3152-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="c3152-150">外部程式碼可以 `GetType` 在您的類別上呼叫，並取得您所使用的相同鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="c3152-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="c3152-151">這會導致兩個類別封鎖彼此的 `SyncLock` 區塊。</span><span class="sxs-lookup"><span data-stu-id="c3152-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c3152-152">範例</span><span class="sxs-lookup"><span data-stu-id="c3152-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="c3152-153">描述</span><span class="sxs-lookup"><span data-stu-id="c3152-153">Description</span></span>  

 <span data-ttu-id="c3152-154">下列範例顯示的類別會維護簡單的訊息清單。</span><span class="sxs-lookup"><span data-stu-id="c3152-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="c3152-155">它會將訊息儲存在陣列中，並將該陣列的最後使用元素保存在變數中。</span><span class="sxs-lookup"><span data-stu-id="c3152-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="c3152-156">此程式會 `addAnotherMessage` 遞增最後一個元素，並儲存新的訊息。</span><span class="sxs-lookup"><span data-stu-id="c3152-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="c3152-157">這兩個作業會受到 `SyncLock` 和語句的保護 `End SyncLock` ，因為當最後一個專案遞增之後，必須先儲存新的訊息，其他執行緒才能再次遞增最後一個專案。</span><span class="sxs-lookup"><span data-stu-id="c3152-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="c3152-158">如果 `simpleMessageList` 類別在其所有實例之間共用一個訊息清單，則變數 `messagesList` 和會宣告 `messagesLast` 為 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="c3152-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="c3152-159">在此情況下，變數 `messagesLock` 也應該是 `Shared` ，如此一來，每個實例都會使用一個鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="c3152-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c3152-160">程式碼</span><span class="sxs-lookup"><span data-stu-id="c3152-160">Code</span></span>  

 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="c3152-161">描述</span><span class="sxs-lookup"><span data-stu-id="c3152-161">Description</span></span>  

 <span data-ttu-id="c3152-162">下列範例會使用執行緒和 `SyncLock` 。</span><span class="sxs-lookup"><span data-stu-id="c3152-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="c3152-163">只要 `SyncLock` 語句存在，語句區塊就是關鍵區段，而且 `balance` 永遠不會成為負數。</span><span class="sxs-lookup"><span data-stu-id="c3152-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="c3152-164">您可以將 `SyncLock` 和語句標記 `End SyncLock` 為批註，以查看離開關鍵字的效果 `SyncLock` 。</span><span class="sxs-lookup"><span data-stu-id="c3152-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c3152-165">程式碼</span><span class="sxs-lookup"><span data-stu-id="c3152-165">Code</span></span>  

 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="c3152-166">註解</span><span class="sxs-lookup"><span data-stu-id="c3152-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3152-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3152-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="c3152-168">同步處理原始物件概觀</span><span class="sxs-lookup"><span data-stu-id="c3152-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
