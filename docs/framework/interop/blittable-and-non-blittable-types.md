---
title: "Blittable 和非 Blittable 類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10e9f4be3d02ac24c70c4a370ed96ff0dada130a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="b0533-102">Blittable 和非 Blittable 類型</span><span class="sxs-lookup"><span data-stu-id="b0533-102">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="b0533-103">大部分的資料類型是 Managed 和 Unmanaged 記憶體中的常見呈現，而且 Interop 封送處理器不需要特殊處理。</span><span class="sxs-lookup"><span data-stu-id="b0533-103">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="b0533-104">這些類型稱為「Blittable 類型」，因為它們在 Managed 與 Unmanaged 程式碼之間傳遞時不需要進行轉換。</span><span class="sxs-lookup"><span data-stu-id="b0533-104">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="b0533-105">從平台叫用呼叫傳回的結構必須是 Blittable 類型。</span><span class="sxs-lookup"><span data-stu-id="b0533-105">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="b0533-106">平台叫用不支援非 Blittable 結構作為傳回類型。</span><span class="sxs-lookup"><span data-stu-id="b0533-106">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="b0533-107"><xref:System> 命名空間中的下列類型是 Blittable 類型：</span><span class="sxs-lookup"><span data-stu-id="b0533-107">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
-   <xref:System.Byte?displayProperty=nameWithType>  
  
-   <xref:System.SByte?displayProperty=nameWithType>  
  
-   <xref:System.Int16?displayProperty=nameWithType>  
  
-   <xref:System.UInt16?displayProperty=nameWithType>  
  
-   <xref:System.Int32?displayProperty=nameWithType>  
  
-   <xref:System.UInt32?displayProperty=nameWithType>  
  
-   <xref:System.Int64?displayProperty=nameWithType>  
  
-   <xref:System.UInt64?displayProperty=nameWithType>  
  
-   <xref:System.IntPtr?displayProperty=nameWithType>  
  
-   <xref:System.UIntPtr?displayProperty=nameWithType>  
  
-   <xref:System.Single?displayProperty=nameWithType>  
  
-   <xref:System.Double?displayProperty=nameWithType>  
  
 <span data-ttu-id="b0533-108">下列複雜類型也是 Blittable 類型：</span><span class="sxs-lookup"><span data-stu-id="b0533-108">The following complex types are also blittable types:</span></span>  
  
-   <span data-ttu-id="b0533-109">Blittable 類型的一維陣列 (例如整數陣列)。</span><span class="sxs-lookup"><span data-stu-id="b0533-109">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="b0533-110">不過，包含 Blittable 類型之可變陣列的類型本身不是 Blittable。</span><span class="sxs-lookup"><span data-stu-id="b0533-110">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
-   <span data-ttu-id="b0533-111">只包含 Blittable 類型 (將它們封送處理為格式化類型時也包含類別) 的格式化實值型別。</span><span class="sxs-lookup"><span data-stu-id="b0533-111">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="b0533-112">如需格式化實值型別的詳細資訊，請參閱[實值型別的預設封送處理](http://msdn.microsoft.com/library/4d9a876c-e05a-40ba-bd85-bd22877f984a)。</span><span class="sxs-lookup"><span data-stu-id="b0533-112">For more information about formatted value types, see [Default Marshaling for Value Types](http://msdn.microsoft.com/library/4d9a876c-e05a-40ba-bd85-bd22877f984a).</span></span>  
  
 <span data-ttu-id="b0533-113">物件參考不是 Blittable。</span><span class="sxs-lookup"><span data-stu-id="b0533-113">Object references are not blittable.</span></span> <span data-ttu-id="b0533-114">這包含自行 Blittable 之物件參考的陣列。</span><span class="sxs-lookup"><span data-stu-id="b0533-114">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="b0533-115">例如，您可以定義 Blittable 結構，但無法定義包含這些結構參考之陣列的 Blittable 類型。</span><span class="sxs-lookup"><span data-stu-id="b0533-115">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="b0533-116">進行最佳化時，在封送處理期間，會[釘選](../../../docs/framework/interop/copying-and-pinning.md) Blittable 類型以及只包含 Blittable 成員之類別的陣列，而不是複製。</span><span class="sxs-lookup"><span data-stu-id="b0533-116">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](../../../docs/framework/interop/copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="b0533-117">呼叫者和被呼叫者位於相同的 Apartment 時，可以將這些類型封送處理為 In/Out 參數。</span><span class="sxs-lookup"><span data-stu-id="b0533-117">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="b0533-118">不過，會將這些類型實際封送處理為 In 參數；而且，如果您想要將引數封送處理為 In/Out 參數，則您必須套用 <xref:System.Runtime.InteropServices.InAttribute> 和 <xref:System.Runtime.InteropServices.OutAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b0533-118">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="b0533-119">部分 Managed 資料類型需要 Unmanaged 環境中有不同的呈現。</span><span class="sxs-lookup"><span data-stu-id="b0533-119">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="b0533-120">這些非 Blittable 資料類型必須轉換成可封送處理的形式。</span><span class="sxs-lookup"><span data-stu-id="b0533-120">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="b0533-121">例如，Managed 字串是非 Blittable 類型，因為它們必須先轉換成字串物件，才能進行封送處理。</span><span class="sxs-lookup"><span data-stu-id="b0533-121">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="b0533-122">下表列出 <xref:System> 命名空間中的非 Blittable 類型。</span><span class="sxs-lookup"><span data-stu-id="b0533-122">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="b0533-123">[委派](http://msdn.microsoft.com/library/d176ee76-f982-494b-b03d-92e4118896e2) (這是參照靜態方法或類別執行個體的資料結構) 也是非 Blittable。</span><span class="sxs-lookup"><span data-stu-id="b0533-123">[Delegates](http://msdn.microsoft.com/library/d176ee76-f982-494b-b03d-92e4118896e2), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="b0533-124">非 Blittable 類型</span><span class="sxs-lookup"><span data-stu-id="b0533-124">Non-blittable type</span></span>|<span data-ttu-id="b0533-125">描述</span><span class="sxs-lookup"><span data-stu-id="b0533-125">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="b0533-126">System.Array</span><span class="sxs-lookup"><span data-stu-id="b0533-126">System.Array</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="b0533-127">轉換成 C 樣式陣列或 `SAFEARRAY`。</span><span class="sxs-lookup"><span data-stu-id="b0533-127">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="b0533-128">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="b0533-128">System.Boolean</span></span>](http://msdn.microsoft.com/library/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)|<span data-ttu-id="b0533-129">轉換成 `true` 為 1 或 -1 的 1、2 或 4 位元組值。</span><span class="sxs-lookup"><span data-stu-id="b0533-129">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|[<span data-ttu-id="b0533-130">System.Char</span><span class="sxs-lookup"><span data-stu-id="b0533-130">System.Char</span></span>](http://msdn.microsoft.com/library/cecc87c1-075e-4cde-aa56-33d189f66feb)|<span data-ttu-id="b0533-131">轉換成 Unicode 或 ANSI 字元。</span><span class="sxs-lookup"><span data-stu-id="b0533-131">Converts to a Unicode or ANSI character.</span></span>|  
|[<span data-ttu-id="b0533-132">System.Class</span><span class="sxs-lookup"><span data-stu-id="b0533-132">System.Class</span></span>](http://msdn.microsoft.com/library/fe334af5-0123-43d8-be84-26f6f023ddb6)|<span data-ttu-id="b0533-133">轉換成類別介面。</span><span class="sxs-lookup"><span data-stu-id="b0533-133">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="b0533-134">System.Object</span><span class="sxs-lookup"><span data-stu-id="b0533-134">System.Object</span></span>](../../../docs/framework/interop/default-marshaling-for-objects.md)|<span data-ttu-id="b0533-135">轉換成變異值或介面。</span><span class="sxs-lookup"><span data-stu-id="b0533-135">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="b0533-136">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="b0533-136">System.Mdarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="b0533-137">轉換成 C 樣式陣列或 `SAFEARRAY`。</span><span class="sxs-lookup"><span data-stu-id="b0533-137">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="b0533-138">System.String</span><span class="sxs-lookup"><span data-stu-id="b0533-138">System.String</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)|<span data-ttu-id="b0533-139">轉換成 Null 參考中的字串終止，或轉換成 BSTR。</span><span class="sxs-lookup"><span data-stu-id="b0533-139">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|[<span data-ttu-id="b0533-140">System.Valuetype</span><span class="sxs-lookup"><span data-stu-id="b0533-140">System.Valuetype</span></span>](http://msdn.microsoft.com/library/4d9a876c-e05a-40ba-bd85-bd22877f984a)|<span data-ttu-id="b0533-141">轉換成具有固定記憶體配置的結構。</span><span class="sxs-lookup"><span data-stu-id="b0533-141">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="b0533-142">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="b0533-142">System.Szarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="b0533-143">轉換成 C 樣式陣列或 `SAFEARRAY`。</span><span class="sxs-lookup"><span data-stu-id="b0533-143">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="b0533-144">COM Interop 只能支援類別和物件類型。</span><span class="sxs-lookup"><span data-stu-id="b0533-144">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="b0533-145">如需 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、C# 和 C++ 中的對應類型，請參閱[類別庫概觀](../../../docs/standard/class-library-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b0533-145">For corresponding types in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++, see the [Class Library Overview](../../../docs/standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0533-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="b0533-146">See Also</span></span>  
 [<span data-ttu-id="b0533-147">預設的封送處理行為</span><span class="sxs-lookup"><span data-stu-id="b0533-147">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)
