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
ms.openlocfilehash: cf2aad9ec2ba67200d175fbcddfcb49afeac6efc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604974"
---
# <a name="synclock-statement"></a><span data-ttu-id="1a9a8-102">SyncLock 陳述式</span><span class="sxs-lookup"><span data-stu-id="1a9a8-102">SyncLock Statement</span></span>
<span data-ttu-id="1a9a8-103">取得陳述式區塊的獨佔鎖定之前執行的區塊。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a9a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="1a9a8-104">Syntax</span></span>  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="1a9a8-105">組件</span><span class="sxs-lookup"><span data-stu-id="1a9a8-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="1a9a8-106">必要。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-106">Required.</span></span> <span data-ttu-id="1a9a8-107">評估為物件參考的運算式。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="1a9a8-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-108">Optional.</span></span> <span data-ttu-id="1a9a8-109">屬於已取得鎖定時要執行的陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="1a9a8-110">終止`SyncLock`區塊。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a9a8-111">備註</span><span class="sxs-lookup"><span data-stu-id="1a9a8-111">Remarks</span></span>  
 <span data-ttu-id="1a9a8-112">`SyncLock`陳述式可確保多個執行緒不會在同時執行的陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="1a9a8-113">`SyncLock` 每個執行緒可防止輸入區塊，直到沒有其他執行緒正在執行它。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="1a9a8-114">最常見的用法`SyncLock`是為了防止資料由多個執行緒同時更新。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="1a9a8-115">如果操作資料的陳述式必須移至不受干擾完成，請將它們放在`SyncLock`區塊。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="1a9a8-116">有時稱為陳述式區塊的獨佔鎖定所保護*關鍵區段*。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="1a9a8-117">規則</span><span class="sxs-lookup"><span data-stu-id="1a9a8-117">Rules</span></span>  
  
-   <span data-ttu-id="1a9a8-118">分支。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-118">Branching.</span></span> <span data-ttu-id="1a9a8-119">您無法分支到`SyncLock`封鎖到區塊之外。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
-   <span data-ttu-id="1a9a8-120">鎖定物件的值。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-120">Lock Object Value.</span></span> <span data-ttu-id="1a9a8-121">值`lockobject`不可`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="1a9a8-122">您必須建立之鎖定物件，再使用它在`SyncLock`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="1a9a8-123">您無法變更的值`lockobject`執行時`SyncLock`區塊。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="1a9a8-124">這個機制需要之鎖定物件維持不變。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
-   <span data-ttu-id="1a9a8-125">您無法使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)中的運算子`SyncLock`區塊。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="1a9a8-126">行為</span><span class="sxs-lookup"><span data-stu-id="1a9a8-126">Behavior</span></span>  
  
-   <span data-ttu-id="1a9a8-127">機制。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-127">Mechanism.</span></span> <span data-ttu-id="1a9a8-128">當執行緒到達`SyncLock`陳述式，它會評估`lockobject`運算式並暫止執行，直到它取得運算式所傳回的物件上的獨佔鎖定。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="1a9a8-129">當另一個執行緒到達`SyncLock`陳述式，它不會取得鎖定的第一個執行緒執行直到`End SyncLock`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
-   <span data-ttu-id="1a9a8-130">受保護的資料。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-130">Protected Data.</span></span> <span data-ttu-id="1a9a8-131">如果`lockobject`是`Shared`變數的獨佔鎖定可防止任何類別執行個體中的執行緒執行`SyncLock`封鎖其他任何執行緒執行它時。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="1a9a8-132">如此可保護的所有執行個體之間共用的資料。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="1a9a8-133">如果`lockobject`是執行個體變數 (不`Shared`)，鎖定可預防執行目前的執行個體中執行的執行緒`SyncLock`封鎖在相同的執行個體中的另一個執行緒在同時間。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="1a9a8-134">如此可保護的個別執行個體所保留的資料。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-134">This protects data maintained by the individual instance.</span></span>  
  
-   <span data-ttu-id="1a9a8-135">取得和釋放。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-135">Acquisition and Release.</span></span> <span data-ttu-id="1a9a8-136">A`SyncLock`區塊的行為類似`Try...Finally`所在建構`Try`區塊上取得的獨佔鎖定`lockobject`和`Finally`區塊釋放它。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="1a9a8-137">因為這個緣故，`SyncLock`區塊保證會釋放鎖定，不論您如何結束區塊。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="1a9a8-138">這是即使有未處理的例外狀況，則為 true。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-138">This is true even in the case of an unhandled exception.</span></span>  
  
-   <span data-ttu-id="1a9a8-139">架構會呼叫。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-139">Framework Calls.</span></span> <span data-ttu-id="1a9a8-140">`SyncLock`區塊會取得和釋放獨佔鎖定，藉由呼叫`Enter`和`Exit`方法`Monitor`類別<xref:System.Threading>命名空間。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="1a9a8-141">程式設計做法</span><span class="sxs-lookup"><span data-stu-id="1a9a8-141">Programming Practices</span></span>  
 <span data-ttu-id="1a9a8-142">`lockobject`運算式應該一律等於專屬於您的類別的物件。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="1a9a8-143">您應該宣告`Private`物件變數，以保護資料屬於目前的執行個體，或`Private Shared`物件變數，以保護資料通用於所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="1a9a8-144">您不應該使用`Me`關鍵字來提供鎖定物件執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="1a9a8-145">如果您的類別之外的程式碼類別的執行個體的參考，它可以使用該參考的鎖定物件為`SyncLock`區塊完全不同於您，保護不同的資料。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="1a9a8-146">如此一來，您的類別和其他類別可能會彼此封鎖無法執行其相關`SyncLock`區塊。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="1a9a8-147">同樣地，字串鎖定可能會有問題，因為處理序使用相同的字串中的任何其他程式碼會共用相同的鎖定。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="1a9a8-148">您也不應該使用`Me.GetType`方法以提供所需的鎖定物件的共用資料。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="1a9a8-149">這是因為`GetType`一律傳回相同`Type`指定的類別名稱的物件。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="1a9a8-150">外部程式碼可以呼叫`GetType`針對您的類別，並取得您正在使用相同的鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="1a9a8-151">這會導致封鎖彼此從兩個類別其`SyncLock`區塊。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1a9a8-152">範例</span><span class="sxs-lookup"><span data-stu-id="1a9a8-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="1a9a8-153">描述</span><span class="sxs-lookup"><span data-stu-id="1a9a8-153">Description</span></span>  
 <span data-ttu-id="1a9a8-154">下列範例會維護訊息的簡單清單的類別。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="1a9a8-155">陣列中保留訊息和最後一個變數中使用該陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="1a9a8-156">`addAnotherMessage`程序遞增的最後一個元素，並將新的訊息。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="1a9a8-157">這兩項作業會受到`SyncLock`和`End SyncLock`陳述式，因為其他任何執行緒可以一次遞增的最後一個元素之前，一旦已遞增的最後一個元素，必須儲存新的訊息。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="1a9a8-158">如果`simpleMessageList`類別共用所有的執行個體，變數之間的訊息傳遞一份清單`messagesList`和`messagesLast`會宣告為`Shared`。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="1a9a8-159">在此情況下，變數`messagesLock`也應該`Shared`，因此會有每個執行個體所使用的單一鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1a9a8-160">程式碼</span><span class="sxs-lookup"><span data-stu-id="1a9a8-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a><span data-ttu-id="1a9a8-161">描述</span><span class="sxs-lookup"><span data-stu-id="1a9a8-161">Description</span></span>  
 <span data-ttu-id="1a9a8-162">下列範例會使用執行緒和`SyncLock`。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="1a9a8-163">只要`SyncLock`陳述式存在，陳述式區塊是關鍵區段和`balance`絕對不會是負數值。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="1a9a8-164">您可以註解`SyncLock`和`End SyncLock`陳述式，以查看留下的效果`SyncLock`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1a9a8-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1a9a8-165">程式碼</span><span class="sxs-lookup"><span data-stu-id="1a9a8-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="1a9a8-166">註解</span><span class="sxs-lookup"><span data-stu-id="1a9a8-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a9a8-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a9a8-167">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="1a9a8-168">執行緒同步處理</span><span class="sxs-lookup"><span data-stu-id="1a9a8-168">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="1a9a8-169">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="1a9a8-169">Threading</span></span>](../../programming-guide/concepts/threading/index.md)
