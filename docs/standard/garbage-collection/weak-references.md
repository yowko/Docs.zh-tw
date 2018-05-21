---
title: 弱式參考
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03da36090c255f635036a9bd518bdacd99404ed4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="weak-references"></a><span data-ttu-id="bed65-102">弱式參考</span><span class="sxs-lookup"><span data-stu-id="bed65-102">Weak References</span></span>
<span data-ttu-id="bed65-103">在應用程式碼可以存取使用中物件時，記憶體回收行程無法透過應用程式回收該物件。</span><span class="sxs-lookup"><span data-stu-id="bed65-103">The garbage collector cannot collect an object in use by an application while the application's code can reach that object.</span></span> <span data-ttu-id="bed65-104">應用程式即具有物件的強式參考。</span><span class="sxs-lookup"><span data-stu-id="bed65-104">The application is said to have a strong reference to the object.</span></span>  
  
 <span data-ttu-id="bed65-105">弱式參考允許記憶體回收行程回收物件，同時仍然允許應用程式存取物件。</span><span class="sxs-lookup"><span data-stu-id="bed65-105">A weak reference permits the garbage collector to collect the object while still allowing the application to access the object.</span></span> <span data-ttu-id="bed65-106">沒有強式參考時，除非回收物件，否則弱式參考僅在時間量不定期間才有效。</span><span class="sxs-lookup"><span data-stu-id="bed65-106">A weak reference is valid only during the indeterminate amount of time until the object is collected when no strong references exist.</span></span> <span data-ttu-id="bed65-107">當您使用弱式參考時，應用程式仍然可以取得物件的強式參考，以防止回收該物件。</span><span class="sxs-lookup"><span data-stu-id="bed65-107">When you use a weak reference, the application can still obtain a strong reference to the object, which prevents it from being collected.</span></span> <span data-ttu-id="bed65-108">不過，記憶體回收行程在重新建立強式參考之前之前先取得物件，一定有其風險。</span><span class="sxs-lookup"><span data-stu-id="bed65-108">However, there is always the risk that the garbage collector will get to the object first before a strong reference is reestablished.</span></span>  
  
 <span data-ttu-id="bed65-109">弱式參考適用於使用大量記憶體的物件，但可以在透過記憶體回收對其進行回收時輕鬆地予以重建。</span><span class="sxs-lookup"><span data-stu-id="bed65-109">Weak references are useful for objects that use a lot of memory, but can be recreated easily if they are reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="bed65-110">假設 Windows Forms 應用程式中的樹狀檢視會向使用者顯示複雜的階層式選項。</span><span class="sxs-lookup"><span data-stu-id="bed65-110">Suppose a tree view in a Windows Forms application displays a complex hierarchical choice of options to the user.</span></span> <span data-ttu-id="bed65-111">如果基礎資料很大，則使用者參與應用程式中的其他作業時，將樹狀結構保留在記憶體不具效率。</span><span class="sxs-lookup"><span data-stu-id="bed65-111">If the underlying data is large, keeping the tree in memory is inefficient when the user is involved with something else in the application.</span></span>  
  
 <span data-ttu-id="bed65-112">當使用者切換到應用程式的另一個部分時，您可以使用 <xref:System.WeakReference> 類別來建立樹狀結構的弱式參考，並終結所有強式參考。</span><span class="sxs-lookup"><span data-stu-id="bed65-112">When the user switches away to another part of the application, you can use the <xref:System.WeakReference> class to create a weak reference to the tree and destroy all strong references.</span></span> <span data-ttu-id="bed65-113">使用者切換回樹狀結構時，應用程式會嘗試取得樹狀結構的強式參考，如果成功，可以避免重新建構樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="bed65-113">When the user switches back to the tree, the application attempts to obtain a strong reference to the tree and, if successful, avoids reconstructing the tree.</span></span>  
  
 <span data-ttu-id="bed65-114">若要建立物件的弱式參考，請使用要追蹤之物件的執行個體來建立 <xref:System.WeakReference>。</span><span class="sxs-lookup"><span data-stu-id="bed65-114">To establish a weak reference with an object, you create a <xref:System.WeakReference> using the instance of the object to be tracked.</span></span> <span data-ttu-id="bed65-115">接著將 <xref:System.WeakReference.Target%2A> 屬性設定為該物件，並將物件的原始參考設定為 `null`。</span><span class="sxs-lookup"><span data-stu-id="bed65-115">You then set the <xref:System.WeakReference.Target%2A> property to that object and set the original reference to the object to `null`.</span></span> <span data-ttu-id="bed65-116">如需程式碼範例，請參閱類別庫中的 <xref:System.WeakReference>。</span><span class="sxs-lookup"><span data-stu-id="bed65-116">For a code example, see <xref:System.WeakReference> in the class library.</span></span>  
  
## <a name="short-and-long-weak-references"></a><span data-ttu-id="bed65-117">簡短和完整弱式參考</span><span class="sxs-lookup"><span data-stu-id="bed65-117">Short and Long Weak References</span></span>  
 <span data-ttu-id="bed65-118">您可以建立簡短弱式參考或完整弱式參考︰</span><span class="sxs-lookup"><span data-stu-id="bed65-118">You can create a short weak reference or a long weak reference:</span></span>  
  
-   <span data-ttu-id="bed65-119">Short</span><span class="sxs-lookup"><span data-stu-id="bed65-119">Short</span></span>  
  
     <span data-ttu-id="bed65-120">透過記憶體回收回收物件時，簡短弱式參考的目標會變成 `null`。</span><span class="sxs-lookup"><span data-stu-id="bed65-120">The target of a short weak reference becomes `null` when the object is reclaimed by garbage collection.</span></span> <span data-ttu-id="bed65-121">弱式參考本身是 Managed 物件，而且很容易進行記憶體回收，就像任何其他 Managed 物件一樣。</span><span class="sxs-lookup"><span data-stu-id="bed65-121">The weak reference is itself a managed object, and is subject to garbage collection just like any other managed object.</span></span>  <span data-ttu-id="bed65-122">簡短弱式參考是 <xref:System.WeakReference> 的預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="bed65-122">A short weak reference is the default constructor for <xref:System.WeakReference>.</span></span>  
  
-   <span data-ttu-id="bed65-123">Long</span><span class="sxs-lookup"><span data-stu-id="bed65-123">Long</span></span>  
  
     <span data-ttu-id="bed65-124">在呼叫物件的 <xref:System.Object.Finalize%2A> 方法之後，會保留完整弱式參考。</span><span class="sxs-lookup"><span data-stu-id="bed65-124">A long weak reference is retained after the object's <xref:System.Object.Finalize%2A> method has been called.</span></span> <span data-ttu-id="bed65-125">這樣會重建物件，但是物件的狀態仍然無法預測。</span><span class="sxs-lookup"><span data-stu-id="bed65-125">This allows the object to be recreated, but the state of the object remains unpredictable.</span></span> <span data-ttu-id="bed65-126">若要使用完整參考，請在 <xref:System.WeakReference> 建構函式中指定 `true`。</span><span class="sxs-lookup"><span data-stu-id="bed65-126">To use a long reference, specify `true` in the <xref:System.WeakReference> constructor.</span></span>  
  
     <span data-ttu-id="bed65-127">如果物件的類型沒有 <xref:System.Object.Finalize%2A> 方法，則會套用簡短的弱式參考功能，而且弱式參考只在回收目標之前有效，而目標的回收可以在執行完成項之後隨時執行。</span><span class="sxs-lookup"><span data-stu-id="bed65-127">If the object's type does not have a <xref:System.Object.Finalize%2A> method, the short weak reference functionality applies and the weak reference is valid only until the target is collected, which can occur anytime after the finalizer is run.</span></span>  
  
 <span data-ttu-id="bed65-128">若要建立強式參考，並再次使用物件，請將 <xref:System.WeakReference> 的 <xref:System.WeakReference.Target%2A> 屬性轉換為物件的類型。</span><span class="sxs-lookup"><span data-stu-id="bed65-128">To establish a strong reference and use the object again, cast the <xref:System.WeakReference.Target%2A> property of a <xref:System.WeakReference> to the type of the object.</span></span> <span data-ttu-id="bed65-129">如果 <xref:System.WeakReference.Target%2A> 屬性傳回 `null`，則已回收物件；否則，您可以繼續使用物件，因為應用程式已重新取得其強式參考。</span><span class="sxs-lookup"><span data-stu-id="bed65-129">If the <xref:System.WeakReference.Target%2A> property returns `null`, the object was collected; otherwise, you can continue to use the object because the application has regained a strong reference to it.</span></span>  
  
## <a name="guidelines-for-using-weak-references"></a><span data-ttu-id="bed65-130">使用弱式參考的指導方針</span><span class="sxs-lookup"><span data-stu-id="bed65-130">Guidelines for Using Weak References</span></span>  
 <span data-ttu-id="bed65-131">只在物件狀態於完成之後無法預期時，才會在必要時使用完整弱式參考。</span><span class="sxs-lookup"><span data-stu-id="bed65-131">Use long weak references only when necessary as the state of the object is unpredictable after finalization.</span></span>  
  
 <span data-ttu-id="bed65-132">請避免使用小型物件的弱式參考，因為指標本身可能一樣大或較大。</span><span class="sxs-lookup"><span data-stu-id="bed65-132">Avoid using weak references to small objects because the pointer itself may be as large or larger.</span></span>  
  
 <span data-ttu-id="bed65-133">請避免使用弱式參考作為記憶體管理問題的自動解決方案。</span><span class="sxs-lookup"><span data-stu-id="bed65-133">Avoid using weak references as an automatic solution to memory management problems.</span></span> <span data-ttu-id="bed65-134">相反地，開發有效的快取原則來處理您的應用程式物件。</span><span class="sxs-lookup"><span data-stu-id="bed65-134">Instead, develop an effective caching policy for handling your application's objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bed65-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="bed65-135">See Also</span></span>  
 [<span data-ttu-id="bed65-136">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="bed65-136">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
