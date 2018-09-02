---
title: SyncLock 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: 6f5a89ebe359ca2fdae1d5545192dc2dcecca6a2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401371"
---
# <a name="synclock-statement"></a><span data-ttu-id="4709d-102">SyncLock 陳述式</span><span class="sxs-lookup"><span data-stu-id="4709d-102">SyncLock Statement</span></span>
<span data-ttu-id="4709d-103">執行區塊之前會取得獨佔鎖定陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="4709d-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4709d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4709d-104">Syntax</span></span>  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="4709d-105">組件</span><span class="sxs-lookup"><span data-stu-id="4709d-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="4709d-106">必要。</span><span class="sxs-lookup"><span data-stu-id="4709d-106">Required.</span></span> <span data-ttu-id="4709d-107">評估為物件參考的運算式。</span><span class="sxs-lookup"><span data-stu-id="4709d-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="4709d-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4709d-108">Optional.</span></span> <span data-ttu-id="4709d-109">屬於已取得鎖定時要執行的陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="4709d-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="4709d-110">終止`SyncLock`區塊。</span><span class="sxs-lookup"><span data-stu-id="4709d-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4709d-111">備註</span><span class="sxs-lookup"><span data-stu-id="4709d-111">Remarks</span></span>  
 <span data-ttu-id="4709d-112">`SyncLock`陳述式可確保多個執行緒不會在同時執行的陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="4709d-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="4709d-113">`SyncLock` 防止每個執行緒進入區塊，直到沒有其他執行緒正在執行它。</span><span class="sxs-lookup"><span data-stu-id="4709d-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="4709d-114">最常見的用法`SyncLock`是為了防止資料由多個執行緒同時更新。</span><span class="sxs-lookup"><span data-stu-id="4709d-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="4709d-115">如果操作資料的陳述式必須移至不受干擾完成，將它們放在`SyncLock`區塊。</span><span class="sxs-lookup"><span data-stu-id="4709d-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="4709d-116">有時稱為 「 獨佔鎖定所保護的陳述式區塊*重要區段*。</span><span class="sxs-lookup"><span data-stu-id="4709d-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4709d-117">規則</span><span class="sxs-lookup"><span data-stu-id="4709d-117">Rules</span></span>  
  
-   <span data-ttu-id="4709d-118">分支。</span><span class="sxs-lookup"><span data-stu-id="4709d-118">Branching.</span></span> <span data-ttu-id="4709d-119">您無法分支到`SyncLock`封鎖區塊外。</span><span class="sxs-lookup"><span data-stu-id="4709d-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
-   <span data-ttu-id="4709d-120">鎖定物件的值。</span><span class="sxs-lookup"><span data-stu-id="4709d-120">Lock Object Value.</span></span> <span data-ttu-id="4709d-121">值`lockobject`不能是`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="4709d-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="4709d-122">您必須先將它用於建立之鎖定物件`SyncLock`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4709d-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="4709d-123">您無法變更的值`lockobject`執行時`SyncLock`區塊。</span><span class="sxs-lookup"><span data-stu-id="4709d-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="4709d-124">這個機制需要之鎖定物件維持不變。</span><span class="sxs-lookup"><span data-stu-id="4709d-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
-   <span data-ttu-id="4709d-125">您無法使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)中的運算子`SyncLock`區塊。</span><span class="sxs-lookup"><span data-stu-id="4709d-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="4709d-126">行為</span><span class="sxs-lookup"><span data-stu-id="4709d-126">Behavior</span></span>  
  
-   <span data-ttu-id="4709d-127">機制。</span><span class="sxs-lookup"><span data-stu-id="4709d-127">Mechanism.</span></span> <span data-ttu-id="4709d-128">當執行緒到達`SyncLock`陳述式，它會評估`lockobject`運算式並暫止執行，直到它取得的運算式所傳回的物件上的獨佔鎖定。</span><span class="sxs-lookup"><span data-stu-id="4709d-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="4709d-129">當另一個執行緒到達`SyncLock`陳述式，它不會取得鎖定之前的第一個執行緒執行`End SyncLock`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4709d-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
-   <span data-ttu-id="4709d-130">受保護的資料。</span><span class="sxs-lookup"><span data-stu-id="4709d-130">Protected Data.</span></span> <span data-ttu-id="4709d-131">如果`lockobject`已`Shared`變數的獨佔鎖定可防止任何類別執行個體中的執行緒執行`SyncLock`封鎖任何其他執行緒執行它時。</span><span class="sxs-lookup"><span data-stu-id="4709d-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="4709d-132">這將保護的所有執行個體之間共用的資料。</span><span class="sxs-lookup"><span data-stu-id="4709d-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="4709d-133">如果`lockobject`是執行個體變數 (不`Shared`)，鎖定會防止執行目前的執行個體中執行的執行緒`SyncLock`與相同的執行個體中的另一個執行緒同時的區塊。</span><span class="sxs-lookup"><span data-stu-id="4709d-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="4709d-134">這可保護由個別的執行個體所維護的資料。</span><span class="sxs-lookup"><span data-stu-id="4709d-134">This protects data maintained by the individual instance.</span></span>  
  
-   <span data-ttu-id="4709d-135">取得和釋放。</span><span class="sxs-lookup"><span data-stu-id="4709d-135">Acquisition and Release.</span></span> <span data-ttu-id="4709d-136">A`SyncLock`區塊的行為類似`Try...Finally`在其中建構`Try`區塊上取得的獨佔鎖定`lockobject`而`Finally`區塊釋放它。</span><span class="sxs-lookup"><span data-stu-id="4709d-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="4709d-137">因為這個緣故，`SyncLock`區塊保證會鎖定，而不論您如何結束區塊的版本。</span><span class="sxs-lookup"><span data-stu-id="4709d-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="4709d-138">這是即使發生未處理的例外狀況，則為 true。</span><span class="sxs-lookup"><span data-stu-id="4709d-138">This is true even in the case of an unhandled exception.</span></span>  
  
-   <span data-ttu-id="4709d-139">架構會呼叫。</span><span class="sxs-lookup"><span data-stu-id="4709d-139">Framework Calls.</span></span> <span data-ttu-id="4709d-140">`SyncLock`區塊會取得和釋放獨佔鎖定，藉由呼叫`Enter`並`Exit`種`Monitor`類別<xref:System.Threading>命名空間。</span><span class="sxs-lookup"><span data-stu-id="4709d-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="4709d-141">程式設計做法</span><span class="sxs-lookup"><span data-stu-id="4709d-141">Programming Practices</span></span>  
 <span data-ttu-id="4709d-142">`lockobject`運算式應該一律評估為專屬於您類別的物件。</span><span class="sxs-lookup"><span data-stu-id="4709d-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="4709d-143">您應該宣告`Private`物件變數，以保護資料屬於目前的執行個體，或`Private Shared`物件變數，以保護通用於所有執行個體的資料。</span><span class="sxs-lookup"><span data-stu-id="4709d-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="4709d-144">您不應該使用`Me`關鍵字以提供鎖定執行個體物件資料。</span><span class="sxs-lookup"><span data-stu-id="4709d-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="4709d-145">如果您的類別之外的程式碼會有您類別的執行個體的參考，它可以使用該參考的鎖定物件為`SyncLock`區塊完全不同於您，保護不同的資料。</span><span class="sxs-lookup"><span data-stu-id="4709d-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="4709d-146">如此一來，您的類別和其他類別可能會彼此封鎖無法執行其相關`SyncLock`區塊。</span><span class="sxs-lookup"><span data-stu-id="4709d-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="4709d-147">同樣地，字串鎖定可能會造成問題，因為使用的相同字串的程序中的任何其他程式碼會共用相同的鎖定。</span><span class="sxs-lookup"><span data-stu-id="4709d-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="4709d-148">您也不應該使用`Me.GetType`共用資料的方法，以提供所需的鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="4709d-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="4709d-149">這是因為`GetType`永遠會傳回相同`Type`為指定的類別名稱的物件。</span><span class="sxs-lookup"><span data-stu-id="4709d-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="4709d-150">外部程式碼可以呼叫`GetType`上您的類別，並取得您正在使用相同的鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="4709d-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="4709d-151">這會導致封鎖彼此從兩個類別及其`SyncLock`區塊。</span><span class="sxs-lookup"><span data-stu-id="4709d-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4709d-152">範例</span><span class="sxs-lookup"><span data-stu-id="4709d-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="4709d-153">描述</span><span class="sxs-lookup"><span data-stu-id="4709d-153">Description</span></span>  
 <span data-ttu-id="4709d-154">下列範例顯示一份簡單的訊息類別。</span><span class="sxs-lookup"><span data-stu-id="4709d-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="4709d-155">它保留在陣列中的訊息和最後一個變數中使用該陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="4709d-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="4709d-156">`addAnotherMessage`程序遞增的最後一個元素，並將新的訊息。</span><span class="sxs-lookup"><span data-stu-id="4709d-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="4709d-157">這兩項作業會受到`SyncLock`和`End SyncLock`陳述式，因為任何其他執行緒可以再次遞增的最後一個元素之前，一旦已遞增的最後一個元素，必須儲存新的訊息。</span><span class="sxs-lookup"><span data-stu-id="4709d-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="4709d-158">如果`simpleMessageList`類別共用在所有執行個體，變數之間的訊息的一份`messagesList`並`messagesLast`會宣告為`Shared`。</span><span class="sxs-lookup"><span data-stu-id="4709d-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="4709d-159">在此案例中，變數`messagesLock`也應該`Shared`，如此一來，會有每個執行個體所使用的單一鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="4709d-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4709d-160">程式碼</span><span class="sxs-lookup"><span data-stu-id="4709d-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a><span data-ttu-id="4709d-161">描述</span><span class="sxs-lookup"><span data-stu-id="4709d-161">Description</span></span>  
 <span data-ttu-id="4709d-162">下列範例會使用執行緒和`SyncLock`。</span><span class="sxs-lookup"><span data-stu-id="4709d-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="4709d-163">只要`SyncLock`陳述式存在，陳述式區塊就是關鍵區段和`balance`絕對不會是負數。</span><span class="sxs-lookup"><span data-stu-id="4709d-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="4709d-164">您可以標記為註解`SyncLock`並`End SyncLock`陳述式，以查看效果留下`SyncLock`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4709d-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4709d-165">程式碼</span><span class="sxs-lookup"><span data-stu-id="4709d-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="4709d-166">註解</span><span class="sxs-lookup"><span data-stu-id="4709d-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4709d-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4709d-167">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="4709d-168">執行緒同步處理</span><span class="sxs-lookup"><span data-stu-id="4709d-168">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="4709d-169">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="4709d-169">Threading</span></span>](../../programming-guide/concepts/threading/index.md)
