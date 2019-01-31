---
title: 執行緒區域儲存區：執行緒相關的靜態欄位和資料位置
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69107cd7f1f84fa402479bb8a76c4b9b8a825d69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718256"
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a><span data-ttu-id="7901f-102">執行緒區域儲存區：執行緒相關的靜態欄位和資料位置</span><span class="sxs-lookup"><span data-stu-id="7901f-102">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>
<span data-ttu-id="7901f-103">您可以使用受控執行緒區域儲存區 (TLS) 來儲存對執行緒和應用程式定義域而言是唯一的資料。</span><span class="sxs-lookup"><span data-stu-id="7901f-103">You can use managed thread local storage (TLS) to store data that is unique to a thread and application domain.</span></span> <span data-ttu-id="7901f-104">.NET Framework 提供兩種方式來使用受控 TLS：執行緒相關的靜態欄位和資料插槽。</span><span class="sxs-lookup"><span data-stu-id="7901f-104">The .NET Framework provides two ways to use managed TLS: thread-relative static fields and data slots.</span></span>  
  
-   <span data-ttu-id="7901f-105">如果您可以預期編譯時期的確切需求，請使用執行緒相關的靜態欄位 (在 Visual Basic 中為執行緒相關 `Shared` 欄位)。</span><span class="sxs-lookup"><span data-stu-id="7901f-105">Use thread-relative static fields (thread-relative `Shared` fields in Visual Basic) if you can anticipate your exact needs at compile time.</span></span> <span data-ttu-id="7901f-106">執行緒相關靜態欄位提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="7901f-106">Thread-relative static fields provide the best performance.</span></span> <span data-ttu-id="7901f-107">它們也提供編譯時期類型檢查的優點。</span><span class="sxs-lookup"><span data-stu-id="7901f-107">They also give you the benefits of compile-time type checking.</span></span>  
  
-   <span data-ttu-id="7901f-108">若您的實際需求只能在執行階段進行探索，請使用資料插槽。</span><span class="sxs-lookup"><span data-stu-id="7901f-108">Use data slots when your actual requirements might be discovered only at run time.</span></span> <span data-ttu-id="7901f-109">比起執行緒相關靜態欄位，資料插槽的速度更慢且更難使用，而且會將資料儲存為 <xref:System.Object> 型別，因此您必須將它轉換成正確的型別才能使用它。</span><span class="sxs-lookup"><span data-stu-id="7901f-109">Data slots are slower and more awkward to use than thread-relative static fields, and data is stored as type <xref:System.Object>, so you must cast it to the correct type before you use it.</span></span>  
  
 <span data-ttu-id="7901f-110">在非受控 C++ 中，您可以使用 `TlsAlloc` 動態配置插槽，並使用 `__declspec(thread)` 來宣告變數應配置於執行緒相關儲存區中。</span><span class="sxs-lookup"><span data-stu-id="7901f-110">In unmanaged C++, you use `TlsAlloc` to allocate slots dynamically and `__declspec(thread)` to declare that a variable should be allocated in thread-relative storage.</span></span> <span data-ttu-id="7901f-111">執行緒相關靜態欄位和資料插槽提供此行為的受控版本。</span><span class="sxs-lookup"><span data-stu-id="7901f-111">Thread-relative static fields and data slots provide the managed version of this behavior.</span></span>  
  
 <span data-ttu-id="7901f-112">在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，您可以使用 <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> 類別來建立第一次取用物件時進行延遲初始化的執行緒區域物件。</span><span class="sxs-lookup"><span data-stu-id="7901f-112">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> class to create thread-local objects that are initialized lazily when the object is first consumed.</span></span> <span data-ttu-id="7901f-113">如需詳細資訊，請參閱[延遲初始化](../../../docs/framework/performance/lazy-initialization.md)。</span><span class="sxs-lookup"><span data-stu-id="7901f-113">For more information, see [Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md).</span></span>  
  
## <a name="uniqueness-of-data-in-managed-tls"></a><span data-ttu-id="7901f-114">受控 TLS 中資料的唯一性</span><span class="sxs-lookup"><span data-stu-id="7901f-114">Uniqueness of Data in Managed TLS</span></span>  
 <span data-ttu-id="7901f-115">無論您使用的是執行緒相關靜態欄位或資料插槽，受控 TLS 中的資料對執行緒和應用程式定義域的組合都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="7901f-115">Whether you use thread-relative static fields or data slots, data in managed TLS is unique to the combination of thread and application domain.</span></span>  
  
-   <span data-ttu-id="7901f-116">在應用程式定義域內，一個執行緒無法修改另一個執行緒的資料，即使這兩個執行緒使用同一個欄位或插槽也一樣。</span><span class="sxs-lookup"><span data-stu-id="7901f-116">Within an application domain, one thread cannot modify data from another thread, even when both threads use the same field or slot.</span></span>  
  
-   <span data-ttu-id="7901f-117">當執行緒從多個應用程式定義域存取相同的欄位或插槽時，會在每個應用程式定義域中維護個別的值。</span><span class="sxs-lookup"><span data-stu-id="7901f-117">When a thread accesses the same field or slot from multiple application domains, a separate value is maintained in each application domain.</span></span>  
  
 <span data-ttu-id="7901f-118">例如，如果執行緒會設定執行緒相關靜態欄位的值，則進入另一個應用程式定義域，然後擷取該欄位的值，在第二個應用程式定義域中擷取的值與第一個應用程式定義域中的值不同。</span><span class="sxs-lookup"><span data-stu-id="7901f-118">For example, if a thread sets the value of a thread-relative static field, enters another application domain, and then retrieves the value of the field, the value retrieved in the second application domain differs from the value in the first application domain.</span></span> <span data-ttu-id="7901f-119">在第二個應用程式定義域中設定欄位的新值，不會影響欄位在第一個應用程式定義域中的值。</span><span class="sxs-lookup"><span data-stu-id="7901f-119">Setting a new value for the field in the second application domain does not affect the field's value in the first application domain.</span></span>  
  
 <span data-ttu-id="7901f-120">同樣地，當執行緒取得兩個不同應用程式定義域中相同的具名資料插槽時，第一個應用程式定義域中的資料會維持獨立，與第二個應用程式定義域中的資料無關。</span><span class="sxs-lookup"><span data-stu-id="7901f-120">Similarly, when a thread gets the same named data slot in two different application domains, the data in the first application domain remains independent of the data in the second application domain.</span></span>  
  
## <a name="thread-relative-static-fields"></a><span data-ttu-id="7901f-121">執行緒相關靜態欄位</span><span class="sxs-lookup"><span data-stu-id="7901f-121">Thread-Relative Static Fields</span></span>  
 <span data-ttu-id="7901f-122">如果您知道某份資料對執行緒和應用程式定義域組合而言一定是唯一的，請將 <xref:System.ThreadStaticAttribute> 屬性套用到靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="7901f-122">If you know that a piece of data is always unique to a thread and application-domain combination, apply the <xref:System.ThreadStaticAttribute> attribute to the static field.</span></span> <span data-ttu-id="7901f-123">像使用任何其他靜態欄位一樣使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="7901f-123">Use the field as you would use any other static field.</span></span> <span data-ttu-id="7901f-124">欄位中的資料對使用它的每個執行緒而言都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="7901f-124">The data in the field is unique to each thread that uses it.</span></span>  
  
 <span data-ttu-id="7901f-125">執行緒相關靜態欄位提供比資料插槽更好的效能，並具備編譯時期型別檢查的優點。</span><span class="sxs-lookup"><span data-stu-id="7901f-125">Thread-relative static fields provide better performance than data slots and have the benefit of compile-time type checking.</span></span>  
  
 <span data-ttu-id="7901f-126">請注意，任何類別建構函式程式碼都將在存取欄位之第一個內容的第一個執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="7901f-126">Be aware that any class constructor code will run on the first thread in the first context that accesses the field.</span></span> <span data-ttu-id="7901f-127">在相同應用程式定義域的所有其他執行緒或內容中，如果它們為參考型別，就會將欄位初始化為 `null` (在 Visual Basic 中為 `Nothing`)，或者如果它們是實值型別，則會設為預設值。</span><span class="sxs-lookup"><span data-stu-id="7901f-127">In all other threads or contexts in the same application domain, the fields will be initialized to `null` (`Nothing` in Visual Basic) if they are reference types, or to their default values if they are value types.</span></span> <span data-ttu-id="7901f-128">因此，您不應該依賴類別建構函式來將執行緒相關靜態欄位初始化。</span><span class="sxs-lookup"><span data-stu-id="7901f-128">Therefore, you should not rely on class constructors to initialize thread-relative static fields.</span></span> <span data-ttu-id="7901f-129">而是應避免將執行緒相關靜態欄位初始化，並假設已將它們初始化為 `null` (`Nothing`) 或其預設值。</span><span class="sxs-lookup"><span data-stu-id="7901f-129">Instead, avoid initializing thread-relative static fields and assume that they are initialized to `null` (`Nothing`) or to their default values.</span></span>  
  
## <a name="data-slots"></a><span data-ttu-id="7901f-130">資料插槽</span><span class="sxs-lookup"><span data-stu-id="7901f-130">Data Slots</span></span>  
 <span data-ttu-id="7901f-131">.NET Framework 提供動態資料插槽，這些插槽對執行緒和應用程式定義域的組合而言都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="7901f-131">The .NET Framework provides dynamic data slots that are unique to a combination of thread and application-domain.</span></span> <span data-ttu-id="7901f-132">有兩種類型的資料插槽：具名插槽和未命名的插槽。</span><span class="sxs-lookup"><span data-stu-id="7901f-132">There are two types of data slots: named slots and unnamed slots.</span></span> <span data-ttu-id="7901f-133">這兩者都使用 <xref:System.LocalDataStoreSlot> 結構來實作。</span><span class="sxs-lookup"><span data-stu-id="7901f-133">Both are implemented by using the <xref:System.LocalDataStoreSlot> structure.</span></span>  
  
-   <span data-ttu-id="7901f-134">若要建立具名資料插槽，使用 <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> 或 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="7901f-134">To create a named data slot, use the <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> or <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7901f-135">若要取得現有具名插槽的參考，將其名稱傳遞至 <xref:System.Threading.Thread.GetNamedDataSlot%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7901f-135">To get a reference to an existing named slot, pass its name to the <xref:System.Threading.Thread.GetNamedDataSlot%2A> method.</span></span>  
  
-   <span data-ttu-id="7901f-136">若要建立未命名的資料插槽，請使用 <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="7901f-136">To create an unnamed data slot, use the <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="7901f-137">針對具名和未命名的插槽，請使用 <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> 方法來設定和擷取插槽中的資訊。</span><span class="sxs-lookup"><span data-stu-id="7901f-137">For both named and unnamed slots, use the <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> methods to set and retrieve the information in the slot.</span></span> <span data-ttu-id="7901f-138">這些靜態方法一律會根據目前正在執行它們之執行緒的資料來動作。</span><span class="sxs-lookup"><span data-stu-id="7901f-138">These are static methods that always act on the data for the thread that is currently executing them.</span></span>  
  
 <span data-ttu-id="7901f-139">具名插槽很方便，因為當您需要擷取該插槽時，您可以透過將其名稱傳遞至 <xref:System.Threading.Thread.GetNamedDataSlot%2A> 方法來完成，而不需維護未命名插槽的參考。</span><span class="sxs-lookup"><span data-stu-id="7901f-139">Named slots can be convenient, because you can retrieve the slot when you need it by passing its name to the <xref:System.Threading.Thread.GetNamedDataSlot%2A> method, instead of maintaining a reference to an unnamed slot.</span></span> <span data-ttu-id="7901f-140">不過，如果另一個元件針對其執行緒相關儲存區使用相同名稱，而且執行緒會執行來自您的元件和另一個元件的程式碼，則這兩個元件可能會損毀彼此的資料</span><span class="sxs-lookup"><span data-stu-id="7901f-140">However, if another component uses the same name for its thread-relative storage and a thread executes code from both your component and the other component, the two components might corrupt each other's data.</span></span> <span data-ttu-id="7901f-141">(此案例假設這兩個元件正在相同的應用程式定義域中執行，而且它們並未設計來共用相同資料)。</span><span class="sxs-lookup"><span data-stu-id="7901f-141">(This scenario assumes that both components are running in the same application domain, and that they are not designed to share the same data.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7901f-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7901f-142">See also</span></span>

- <xref:System.ContextStaticAttribute>
- <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>
- <xref:System.ThreadStaticAttribute>
- <xref:System.Runtime.Remoting.Messaging.CallContext>
- [<span data-ttu-id="7901f-143">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="7901f-143">Threading</span></span>](../../../docs/standard/threading/index.md)
