---
title: "執行緒區域儲存區：執行緒相關的靜態欄位和資料位置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 39dd80d378171563f2aadadaa146278e8a417d32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a><span data-ttu-id="2039a-102">執行緒區域儲存區：執行緒相關的靜態欄位和資料位置</span><span class="sxs-lookup"><span data-stu-id="2039a-102">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>
<span data-ttu-id="2039a-103">您可以使用 managed 的執行緒區域儲存區 (TLS) 來儲存資料的唯一執行緒和應用程式網域。</span><span class="sxs-lookup"><span data-stu-id="2039a-103">You can use managed thread local storage (TLS) to store data that is unique to a thread and application domain.</span></span> <span data-ttu-id="2039a-104">.NET Framework 提供兩種方式使用受管理的 TLS： 執行緒相關靜態欄位和資料位置。</span><span class="sxs-lookup"><span data-stu-id="2039a-104">The .NET Framework provides two ways to use managed TLS: thread-relative static fields and data slots.</span></span>  
  
-   <span data-ttu-id="2039a-105">使用執行緒相關的靜態欄位 (執行緒相關`Shared`在 Visual Basic 中的欄位) 如果您可以預期會在編譯時期的確切需求。</span><span class="sxs-lookup"><span data-stu-id="2039a-105">Use thread-relative static fields (thread-relative `Shared` fields in Visual Basic) if you can anticipate your exact needs at compile time.</span></span> <span data-ttu-id="2039a-106">執行緒相關的靜態欄位會提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="2039a-106">Thread-relative static fields provide the best performance.</span></span> <span data-ttu-id="2039a-107">它們也提供編譯階段類型檢查的好處。</span><span class="sxs-lookup"><span data-stu-id="2039a-107">They also give you the benefits of compile-time type checking.</span></span>  
  
-   <span data-ttu-id="2039a-108">實際的需求可能會發現只能在執行階段時，請使用 資料位置。</span><span class="sxs-lookup"><span data-stu-id="2039a-108">Use data slots when your actual requirements might be discovered only at run time.</span></span> <span data-ttu-id="2039a-109">資料位置較慢，多執行緒相關的靜態欄位，而造成不便，資料會儲存為類型<xref:System.Object>，因此您必須將它轉換成正確的型別再使用它。</span><span class="sxs-lookup"><span data-stu-id="2039a-109">Data slots are slower and more awkward to use than thread-relative static fields, and data is stored as type <xref:System.Object>, so you must cast it to the correct type before you use it.</span></span>  
  
 <span data-ttu-id="2039a-110">在 unmanaged c + + 中，您可以使用`TlsAlloc`動態配置位置和`__declspec(thread)`來宣告變數，應配置執行緒相關的儲存體中。</span><span class="sxs-lookup"><span data-stu-id="2039a-110">In unmanaged C++, you use `TlsAlloc` to allocate slots dynamically and `__declspec(thread)` to declare that a variable should be allocated in thread-relative storage.</span></span> <span data-ttu-id="2039a-111">相對執行緒的靜態欄位和資料位置提供的受管理的版本，此行為。</span><span class="sxs-lookup"><span data-stu-id="2039a-111">Thread-relative static fields and data slots provide the managed version of this behavior.</span></span>  
  
 <span data-ttu-id="2039a-112">在[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，您可以使用<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>類別以建立第一次取用物件時執行延遲初始化執行緒區域物件。</span><span class="sxs-lookup"><span data-stu-id="2039a-112">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> class to create thread-local objects that are initialized lazily when the object is first consumed.</span></span> <span data-ttu-id="2039a-113">如需詳細資訊，請參閱[延遲初始化](../../../docs/framework/performance/lazy-initialization.md)。</span><span class="sxs-lookup"><span data-stu-id="2039a-113">For more information, see [Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md).</span></span>  
  
## <a name="uniqueness-of-data-in-managed-tls"></a><span data-ttu-id="2039a-114">受管理的 TLS 中的資料的唯一性</span><span class="sxs-lookup"><span data-stu-id="2039a-114">Uniqueness of Data in Managed TLS</span></span>  
 <span data-ttu-id="2039a-115">無論您是使用執行緒相關的靜態欄位或資料的位置，受管理的 TLS 中的資料是唯一的執行緒和應用程式定義域的組合。</span><span class="sxs-lookup"><span data-stu-id="2039a-115">Whether you use thread-relative static fields or data slots, data in managed TLS is unique to the combination of thread and application domain.</span></span>  
  
-   <span data-ttu-id="2039a-116">應用程式定義域內兩個執行緒使用的同一個欄位或位置時，即使一個執行緒時，無法修改來自另一個執行緒，資料。</span><span class="sxs-lookup"><span data-stu-id="2039a-116">Within an application domain, one thread cannot modify data from another thread, even when both threads use the same field or slot.</span></span>  
  
-   <span data-ttu-id="2039a-117">當執行緒存取相同的欄位或位置，從多個應用程式定義域時，每個應用程式定義域中維護個別的值。</span><span class="sxs-lookup"><span data-stu-id="2039a-117">When a thread accesses the same field or slot from multiple application domains, a separate value is maintained in each application domain.</span></span>  
  
 <span data-ttu-id="2039a-118">例如，如果執行緒設定執行緒相關的靜態欄位的值會在進入另一個應用程式定義域，並接著會擷取欄位的值，擷取第二個應用程式定義域中的值不同於第一個應用程式定義域中的值。</span><span class="sxs-lookup"><span data-stu-id="2039a-118">For example, if a thread sets the value of a thread-relative static field, enters another application domain, and then retrieves the value of the field, the value retrieved in the second application domain differs from the value in the first application domain.</span></span> <span data-ttu-id="2039a-119">設定第二個應用程式定義域中的新值的欄位不會影響欄位的第一個應用程式定義域中的值。</span><span class="sxs-lookup"><span data-stu-id="2039a-119">Setting a new value for the field in the second application domain does not affect the field's value in the first application domain.</span></span>  
  
 <span data-ttu-id="2039a-120">同樣地，當執行緒會取得兩個不同的應用程式網域中相同的具名的資料位置，第一個應用程式網域中的資料會維持獨立於第二個應用程式網域中的資料。</span><span class="sxs-lookup"><span data-stu-id="2039a-120">Similarly, when a thread gets the same named data slot in two different application domains, the data in the first application domain remains independent of the data in the second application domain.</span></span>  
  
## <a name="thread-relative-static-fields"></a><span data-ttu-id="2039a-121">執行緒相關的靜態欄位</span><span class="sxs-lookup"><span data-stu-id="2039a-121">Thread-Relative Static Fields</span></span>  
 <span data-ttu-id="2039a-122">如果您知道某份資料一定是唯一的執行緒和應用程式定義域的組合，套用<xref:System.ThreadStaticAttribute>屬性到靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="2039a-122">If you know that a piece of data is always unique to a thread and application-domain combination, apply the <xref:System.ThreadStaticAttribute> attribute to the static field.</span></span> <span data-ttu-id="2039a-123">如同您使用任何其他靜態欄位，請使用欄位。</span><span class="sxs-lookup"><span data-stu-id="2039a-123">Use the field as you would use any other static field.</span></span> <span data-ttu-id="2039a-124">欄位中的資料是使用它的每個執行緒的唯一的。</span><span class="sxs-lookup"><span data-stu-id="2039a-124">The data in the field is unique to each thread that uses it.</span></span>  
  
 <span data-ttu-id="2039a-125">執行緒相關的靜態欄位提供較佳的效能比資料位置，並有編譯時間類型檢查的好處。</span><span class="sxs-lookup"><span data-stu-id="2039a-125">Thread-relative static fields provide better performance than data slots and have the benefit of compile-time type checking.</span></span>  
  
 <span data-ttu-id="2039a-126">請注意，任何類別建構函式程式碼會存取欄位的第一個內容中的第一個執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="2039a-126">Be aware that any class constructor code will run on the first thread in the first context that accesses the field.</span></span> <span data-ttu-id="2039a-127">在所有其他執行緒或內容相同的應用程式定義域中，欄位將初始化為`null`(`Nothing`在 Visual Basic 中) 如果它們都是參考類型，或設為預設值，如果它們是實值類型。</span><span class="sxs-lookup"><span data-stu-id="2039a-127">In all other threads or contexts in the same application domain, the fields will be initialized to `null` (`Nothing` in Visual Basic) if they are reference types, or to their default values if they are value types.</span></span> <span data-ttu-id="2039a-128">因此，您不應該依賴類別建構函式來初始化執行緒相關的靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="2039a-128">Therefore, you should not rely on class constructors to initialize thread-relative static fields.</span></span> <span data-ttu-id="2039a-129">相反地，請避免初始化執行緒相關的靜態欄位，並假設已初始化為`null`(`Nothing`) 或為其預設值。</span><span class="sxs-lookup"><span data-stu-id="2039a-129">Instead, avoid initializing thread-relative static fields and assume that they are initialized to `null` (`Nothing`) or to their default values.</span></span>  
  
## <a name="data-slots"></a><span data-ttu-id="2039a-130">資料位置</span><span class="sxs-lookup"><span data-stu-id="2039a-130">Data Slots</span></span>  
 <span data-ttu-id="2039a-131">.NET Framework 提供動態的資料位置對執行緒和應用程式定義域的組合都是唯一。</span><span class="sxs-lookup"><span data-stu-id="2039a-131">The .NET Framework provides dynamic data slots that are unique to a combination of thread and application-domain.</span></span> <span data-ttu-id="2039a-132">有兩種類型的資料位置： 具名位置和未命名的位置。</span><span class="sxs-lookup"><span data-stu-id="2039a-132">There are two types of data slots: named slots and unnamed slots.</span></span> <span data-ttu-id="2039a-133">兩者都透過使用實作<xref:System.LocalDataStoreSlot>結構。</span><span class="sxs-lookup"><span data-stu-id="2039a-133">Both are implemented by using the <xref:System.LocalDataStoreSlot> structure.</span></span>  
  
-   <span data-ttu-id="2039a-134">若要建立具名的資料位置，請使用<xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType>或<xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="2039a-134">To create a named data slot, use the <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> or <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2039a-135">若要取得現有的具名位置的參考，傳遞至其名稱<xref:System.Threading.Thread.GetNamedDataSlot%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2039a-135">To get a reference to an existing named slot, pass its name to the <xref:System.Threading.Thread.GetNamedDataSlot%2A> method.</span></span>  
  
-   <span data-ttu-id="2039a-136">若要建立未命名的資料位置，請使用<xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="2039a-136">To create an unnamed data slot, use the <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="2039a-137">針對名為和未命名的位置，使用<xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType>和<xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType>方法設定和擷取的位置中的資訊。</span><span class="sxs-lookup"><span data-stu-id="2039a-137">For both named and unnamed slots, use the <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> methods to set and retrieve the information in the slot.</span></span> <span data-ttu-id="2039a-138">這些是永遠作用於目前執行它們的執行緒資料的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="2039a-138">These are static methods that always act on the data for the thread that is currently executing them.</span></span>  
  
 <span data-ttu-id="2039a-139">具名的位置很方便，因為當您需要藉由傳遞至其名稱時，您可以擷取插槽<xref:System.Threading.Thread.GetNamedDataSlot%2A>方法，而不是維護的參考未命名的位置。</span><span class="sxs-lookup"><span data-stu-id="2039a-139">Named slots can be convenient, because you can retrieve the slot when you need it by passing its name to the <xref:System.Threading.Thread.GetNamedDataSlot%2A> method, instead of maintaining a reference to an unnamed slot.</span></span> <span data-ttu-id="2039a-140">不過，如果另一個元件使用相同的名稱，其執行緒相關的儲存體和執行緒執行程式碼從您的元件和其他元件，兩個元件可能會損毀彼此的資料。</span><span class="sxs-lookup"><span data-stu-id="2039a-140">However, if another component uses the same name for its thread-relative storage and a thread executes code from both your component and the other component, the two components might corrupt each other's data.</span></span> <span data-ttu-id="2039a-141">（此案例假設這兩個元件，相同的應用程式定義域中執行，而他們並非設計來共用相同的資料）。</span><span class="sxs-lookup"><span data-stu-id="2039a-141">(This scenario assumes that both components are running in the same application domain, and that they are not designed to share the same data.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2039a-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2039a-142">See Also</span></span>  
 <xref:System.ContextStaticAttribute>  
 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>  
 <xref:System.ThreadStaticAttribute>  
 <xref:System.Runtime.Remoting.Messaging.CallContext>  
 [<span data-ttu-id="2039a-143">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="2039a-143">Threading</span></span>](../../../docs/standard/threading/index.md)
