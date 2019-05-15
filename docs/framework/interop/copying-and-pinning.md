---
title: 複製和 Pin
ms.date: 03/30/2017
helpviewer_keywords:
- pinning, interop marshaling
- copying, interop marshaling
- interop marshaling, copying
- interop marshaling, pinning
ms.assetid: 0059f576-e460-4e70-b257-668870e420b8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90ed12862c4cadc45777150deb1b9f91f111bf41
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750504"
---
# <a name="copying-and-pinning"></a><span data-ttu-id="e8638-102">複製和 Pin</span><span class="sxs-lookup"><span data-stu-id="e8638-102">Copying and Pinning</span></span>

<span data-ttu-id="e8638-103">封送處理資料時，Interop 封送處理器可以複製或釘選所封送處理的資料。</span><span class="sxs-lookup"><span data-stu-id="e8638-103">When marshaling data, the interop marshaler can copy or pin the data being marshaled.</span></span> <span data-ttu-id="e8638-104">複製資料時會將某個記憶體位置中的一份資料放入另一個記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="e8638-104">Copying the data places a copy of data from one memory location in another memory location.</span></span> <span data-ttu-id="e8638-105">下圖顯示複製實值型別與以傳址方式將類型從 Managed 複製至 Unmanaged 記憶體之間的差異。</span><span class="sxs-lookup"><span data-stu-id="e8638-105">The following illustration shows the differences between copying a value type and copying a type passed by reference from managed to unmanaged memory.</span></span>

![示範如何複製值和參考型別的圖表。](./media/copying-and-pinning/interop-marshal-copy.gif)

<span data-ttu-id="e8638-107">以傳值方式傳遞的方法引數會封送處理成 Unmanaged 程式碼，以作為堆疊上的值。</span><span class="sxs-lookup"><span data-stu-id="e8638-107">Method arguments passed by value are marshaled to unmanaged code as values on the stack.</span></span> <span data-ttu-id="e8638-108">複製程序是直接的。</span><span class="sxs-lookup"><span data-stu-id="e8638-108">The copying process is direct.</span></span> <span data-ttu-id="e8638-109">以傳址方式傳遞的引數會傳遞為堆疊上的指標。</span><span class="sxs-lookup"><span data-stu-id="e8638-109">Arguments passed by reference are passed as pointers on the stack.</span></span> <span data-ttu-id="e8638-110">同時以傳值和傳址方式傳遞參考型別。</span><span class="sxs-lookup"><span data-stu-id="e8638-110">Reference types are also passed by value and by reference.</span></span> <span data-ttu-id="e8638-111">如下圖所示，會複製或釘選以傳值方式傳遞的參考型別：</span><span class="sxs-lookup"><span data-stu-id="e8638-111">As the following illustration shows, reference types passed by value are either copied or pinned:</span></span>

![示範以傳值和傳址方式傳遞之參考型別的圖表。](./media/copying-and-pinning/interop-marshal-reference-pin.gif)

<span data-ttu-id="e8638-113">釘選會暫時鎖定其目前記憶體位置中的資料，因此 Common Language Runtime 的記憶體回收行程不會重新定位它。</span><span class="sxs-lookup"><span data-stu-id="e8638-113">Pinning temporarily locks the data in its current memory location, thus keeping it from being relocated by the common language runtime's garbage collector.</span></span> <span data-ttu-id="e8638-114">封送處理器會釘選資料，以減少複製和增強效能的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="e8638-114">The marshaler pins data to reduce the overhead of copying and enhance performance.</span></span> <span data-ttu-id="e8638-115">資料的類型決定在封送處理程序期間複製還是釘選資料。</span><span class="sxs-lookup"><span data-stu-id="e8638-115">The type of the data determines whether it is copied or pinned during the marshaling process.</span></span>  <span data-ttu-id="e8638-116">在封送處理期間，會針對 <xref:System.String> 這類物件自動執行釘選，不過，您也可以使用 <xref:System.Runtime.InteropServices.GCHandle> 類別來手動釘選記憶體。</span><span class="sxs-lookup"><span data-stu-id="e8638-116">Pinning is automatically performed during marshaling for objects such as <xref:System.String>, however you can also manually pin memory using the <xref:System.Runtime.InteropServices.GCHandle> class.</span></span>

## <a name="formatted-blittable-classes"></a><span data-ttu-id="e8638-117">格式化 Blittable 類別</span><span class="sxs-lookup"><span data-stu-id="e8638-117">Formatted Blittable Classes</span></span>

<span data-ttu-id="e8638-118">格式化 [Blittable](blittable-and-non-blittable-types.md) 類別具有固定配置 (格式化) 以及 Managed 和 Unmanaged 記憶體中的常見資料呈現。</span><span class="sxs-lookup"><span data-stu-id="e8638-118">Formatted [blittable](blittable-and-non-blittable-types.md) classes have fixed layout (formatted) and common data representation in both managed and unmanaged memory.</span></span> <span data-ttu-id="e8638-119">這些類型需要封送處理時，會將堆積中物件的指標直接傳遞給被呼叫者。</span><span class="sxs-lookup"><span data-stu-id="e8638-119">When these types require marshaling, a pointer to the object in the heap is passed to the callee directly.</span></span> <span data-ttu-id="e8638-120">被呼叫者可以變更指標所參考記憶體位置的內容。</span><span class="sxs-lookup"><span data-stu-id="e8638-120">The callee can change the contents of the memory location being referenced by the pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="e8638-121">如果參數標記 Out 或 In/Out，則被呼叫者可以變更記憶體內容。相反地，將參數設定為封送處理為 In (這是格式化 Blittable 類型的預設值) 時，被呼叫者應該避免變更內容。</span><span class="sxs-lookup"><span data-stu-id="e8638-121">The callee can change the memory contents if the parameter is marked Out or In/Out. In contrast, the callee should avoid changing the contents when the parameter is set to marshal as In, which is the default for formatted blittable types.</span></span> <span data-ttu-id="e8638-122">修改 In 物件時會在將相同類別匯出至型別程式庫時產生問題，並且用來進行跨 Apartment 呼叫。</span><span class="sxs-lookup"><span data-stu-id="e8638-122">Modifying an In object generates problems when the same class is exported to a type library and used to make cross-apartment calls.</span></span>

## <a name="formatted-non-blittable-classes"></a><span data-ttu-id="e8638-123">格式化非 Blittable 類別</span><span class="sxs-lookup"><span data-stu-id="e8638-123">Formatted Non-Blittable Classes</span></span>

<span data-ttu-id="e8638-124">格式化[非 Blittable](blittable-and-non-blittable-types.md) 類別具有固定配置 (格式化)，但 Managed 和 Unmanaged 記憶體中的資料呈現不同。</span><span class="sxs-lookup"><span data-stu-id="e8638-124">Formatted [non-blittable](blittable-and-non-blittable-types.md) classes have fixed layout (formatted) but the data representation is different in managed and unmanaged memory.</span></span> <span data-ttu-id="e8638-125">在下列情況下，資料可能需要轉換：</span><span class="sxs-lookup"><span data-stu-id="e8638-125">The data can require transformation under the following conditions:</span></span>

- <span data-ttu-id="e8638-126">如果以傳值方式封送處理非 Blittable 類別，被呼叫者會收到一份資料結構的指標。</span><span class="sxs-lookup"><span data-stu-id="e8638-126">If a non-blittable class is marshaled by value, the callee receives a pointer to a copy of the data structure.</span></span>

- <span data-ttu-id="e8638-127">如果以傳址方式封送處理非 Blittable 類別，被呼叫者會收到一份資料結構的指標。</span><span class="sxs-lookup"><span data-stu-id="e8638-127">If a non-blittable class is marshaled by reference, the callee receives a pointer to a pointer to a copy of the data structure.</span></span>

- <span data-ttu-id="e8638-128">如果設定 <xref:System.Runtime.InteropServices.InAttribute> 屬性，則一律會使用執行個體狀態來初始化此複本，並依需要封送處理。</span><span class="sxs-lookup"><span data-stu-id="e8638-128">If the <xref:System.Runtime.InteropServices.InAttribute> attribute is set, this copy is always initialized with the instance's state, marshaling as necessary.</span></span>

- <span data-ttu-id="e8638-129">如果設定 <xref:System.Runtime.InteropServices.OutAttribute> 屬性，則一律會在傳回時將狀態複製回執行個體，並依需要封送處理。</span><span class="sxs-lookup"><span data-stu-id="e8638-129">If the <xref:System.Runtime.InteropServices.OutAttribute> attribute is set, the state is always copied back to the instance on return, marshaling as necessary.</span></span>

- <span data-ttu-id="e8638-130">如果同時設定 **InAttribute** 和 **OutAttribute**，則需要兩個複本。</span><span class="sxs-lookup"><span data-stu-id="e8638-130">If both **InAttribute** and **OutAttribute** are set, both copies are required.</span></span> <span data-ttu-id="e8638-131">如果省略任一屬性，則封送處理器可以透過排除任一複本來進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="e8638-131">If either attribute is omitted, the marshaler can optimize by eliminating either copy.</span></span>

## <a name="reference-types"></a><span data-ttu-id="e8638-132">參考類型</span><span class="sxs-lookup"><span data-stu-id="e8638-132">Reference Types</span></span>

<span data-ttu-id="e8638-133">可以透過傳值或傳址方式傳遞參考型別。</span><span class="sxs-lookup"><span data-stu-id="e8638-133">Reference types can be passed by value or by reference.</span></span> <span data-ttu-id="e8638-134">以傳值方式傳遞它們時，會在堆疊上傳遞類型的指標。</span><span class="sxs-lookup"><span data-stu-id="e8638-134">When they are passed by value, a pointer to the type is passed on the stack.</span></span> <span data-ttu-id="e8638-135">以傳址方式傳遞時，會在堆疊上傳遞類型的指標。</span><span class="sxs-lookup"><span data-stu-id="e8638-135">When passed by reference, a pointer to a pointer to the type is passed on the stack.</span></span>

<span data-ttu-id="e8638-136">參考型別具有下列條件式行為：</span><span class="sxs-lookup"><span data-stu-id="e8638-136">Reference types have the following conditional behavior:</span></span>

- <span data-ttu-id="e8638-137">如果以傳值方式傳遞參考型別，而且它具有非 Blittable 類型的成員，則會將類型轉換兩次：</span><span class="sxs-lookup"><span data-stu-id="e8638-137">If a reference type is passed by value and it has members of non-blittable types, the types are converted twice:</span></span>

  - <span data-ttu-id="e8638-138">將引數傳遞給 Unmanaged 端時。</span><span class="sxs-lookup"><span data-stu-id="e8638-138">When an argument is passed to the unmanaged side.</span></span>

  - <span data-ttu-id="e8638-139">從呼叫傳回時。</span><span class="sxs-lookup"><span data-stu-id="e8638-139">On return from the call.</span></span>

  <span data-ttu-id="e8638-140">為了避免不必要的複製和轉換，這些類型會封送處理為 In 參數。</span><span class="sxs-lookup"><span data-stu-id="e8638-140">To avoid unnecessarily copying and conversion, these types are marshaled as In parameters.</span></span> <span data-ttu-id="e8638-141">您必須將 **InAttribute** 和 **OutAttribute** 屬性明確地套用至呼叫者的引數，以查看被呼叫者所進行的變更。</span><span class="sxs-lookup"><span data-stu-id="e8638-141">You must explicitly apply the **InAttribute** and **OutAttribute** attributes to an argument for the caller to see changes made by the callee.</span></span>

- <span data-ttu-id="e8638-142">如果以傳值方式傳遞參考型別，而且它只有 Blittable 類型的成員，則可以在封送處理期間釘選它，而且呼叫者會看到被呼叫者對類型成員所進行的任何變更。</span><span class="sxs-lookup"><span data-stu-id="e8638-142">If a reference type is passed by value and it has only members of blittable types, it can be pinned during marshaling and any changes made to the members of the type by the callee are seen by the caller.</span></span> <span data-ttu-id="e8638-143">如果您想要這個行為，請明確地套用 **InAttribute** 和 **OutAttribute**。</span><span class="sxs-lookup"><span data-stu-id="e8638-143">Apply **InAttribute** and **OutAttribute** explicitly if you want this behavior.</span></span> <span data-ttu-id="e8638-144">如果沒有這些方向屬性，Interop 封送處理器就不會將方向資訊匯出至型別程式庫 (它會匯出為 In，這是預設值)，而且這可能會導致 COM 跨 Apartment 封送處理問題。</span><span class="sxs-lookup"><span data-stu-id="e8638-144">Without these directional attributes, the interop marshaler does not export directional information to the type library (it exports as In, which is the default) and this can cause problems with COM cross-apartment marshaling.</span></span>

- <span data-ttu-id="e8638-145">如果以傳址方式傳遞參考型別，則預設會將它封送處理為 In/Out。</span><span class="sxs-lookup"><span data-stu-id="e8638-145">If a reference type is passed by reference, it will be marshaled as In/Out by default.</span></span>

## <a name="systemstring-and-systemtextstringbuilder"></a><span data-ttu-id="e8638-146">System.String 和 System.Text.StringBuilder</span><span class="sxs-lookup"><span data-stu-id="e8638-146">System.String and System.Text.StringBuilder</span></span>

<span data-ttu-id="e8638-147">以傳值方式或傳址方式將資料封送處理至 Unmanaged 程式碼時，封送處理器通常會將資料複製至次要緩衝區 (可能會在複製期間轉換字元集)，並將緩衝區的參考傳遞給被呼叫者。</span><span class="sxs-lookup"><span data-stu-id="e8638-147">When data is marshaled to unmanaged code by value or by reference, the marshaler typically copies the data to a secondary buffer (possibly converting character sets during the copy) and passes a reference to the buffer to the callee.</span></span> <span data-ttu-id="e8638-148">除非參考是與 **SysAllocString** 一起配置的 **BSTR**，否則參考一律是與 **CoTaskMemAlloc** 一起配置。</span><span class="sxs-lookup"><span data-stu-id="e8638-148">Unless the reference is a **BSTR** allocated with **SysAllocString**, the reference is always allocated with **CoTaskMemAlloc**.</span></span>

<span data-ttu-id="e8638-149">以傳值方式封送處理任一字串類型來進行最佳化時，(例如 Unicode 字元字串)，封送處理器會將內部 Unicode 緩衝區中 Managed 字串的直接指標傳遞給被呼叫者，而不是將它複製至新的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e8638-149">As an optimization when either string type is marshaled by value (such as a Unicode character string), the marshaler passes the callee a direct pointer to managed strings in the internal Unicode buffer instead of copying it to a new buffer.</span></span>

> [!CAUTION]
> <span data-ttu-id="e8638-150">以傳值方式傳遞字串時，被呼叫者必須永遠不得改變封送處理器所傳遞的參考。</span><span class="sxs-lookup"><span data-stu-id="e8638-150">When a string is passed by value, the callee must never alter the reference passed by the marshaler.</span></span> <span data-ttu-id="e8638-151">這樣做可能會損毀 Managed 堆積。</span><span class="sxs-lookup"><span data-stu-id="e8638-151">Doing so can corrupt the managed heap.</span></span>

<span data-ttu-id="e8638-152">以傳址方式傳遞 <xref:System.String?displayProperty=nameWithType> 時，封送處理器會先將字串的內容複製至次要緩衝區，再提出要求。</span><span class="sxs-lookup"><span data-stu-id="e8638-152">When a <xref:System.String?displayProperty=nameWithType> is passed by reference, the marshaler copies the contents the string to a secondary buffer before making the call.</span></span> <span data-ttu-id="e8638-153">它接著會透過呼叫，在傳回時將緩衝區的內容複製至新的字串。</span><span class="sxs-lookup"><span data-stu-id="e8638-153">It then copies the contents of the buffer into a new string on return from the call.</span></span> <span data-ttu-id="e8638-154">這項技術可確保不可變的 Managed 字串保持不變。</span><span class="sxs-lookup"><span data-stu-id="e8638-154">This technique ensures that the immutable managed string remains unaltered.</span></span>

<span data-ttu-id="e8638-155">以傳值方式傳遞 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 時，封送處理器會直接將 **StringBuilder** 的內部緩衝區參考傳遞給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="e8638-155">When a <xref:System.Text.StringBuilder?displayProperty=nameWithType> is passed by value, the marshaler passes a reference to the internal buffer of the **StringBuilder** directly to the caller.</span></span> <span data-ttu-id="e8638-156">呼叫者和被呼叫者必須同意緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="e8638-156">The caller and callee must agree on the size of the buffer.</span></span> <span data-ttu-id="e8638-157">呼叫者負責建立長度足夠的 **StringBuilder**。</span><span class="sxs-lookup"><span data-stu-id="e8638-157">The caller is responsible for creating a **StringBuilder** of adequate length.</span></span> <span data-ttu-id="e8638-158">被呼叫者必須採取必要的預防措施，確保緩衝區未溢位。</span><span class="sxs-lookup"><span data-stu-id="e8638-158">The callee must take the necessary precautions to ensure that the buffer is not overrun.</span></span> <span data-ttu-id="e8638-159">**StringBuilder** 是規則的例外狀況，而此規則預設會將以傳值方式傳遞的參考型別傳遞為 In 參數。</span><span class="sxs-lookup"><span data-stu-id="e8638-159">**StringBuilder** is an exception to the rule that reference types passed by value are passed as In parameters by default.</span></span> <span data-ttu-id="e8638-160">它一律會傳遞為 In/Out。</span><span class="sxs-lookup"><span data-stu-id="e8638-160">It is always passed as In/Out.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8638-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8638-161">See also</span></span>

- [<span data-ttu-id="e8638-162">預設的封送處理行為</span><span class="sxs-lookup"><span data-stu-id="e8638-162">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- <span data-ttu-id="e8638-163">[方向屬性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e8638-163">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="e8638-164">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="e8638-164">Interop Marshaling</span></span>](interop-marshaling.md)
