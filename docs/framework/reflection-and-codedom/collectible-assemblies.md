---
title: 動態類型產生的可回收組件
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b26da264b2da40e19db4bc5e3b3575505f5c979c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637738"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a><span data-ttu-id="4c4f3-102">動態類型產生的可回收組件</span><span class="sxs-lookup"><span data-stu-id="4c4f3-102">Collectible assemblies for dynamic type generation</span></span>

<span data-ttu-id="4c4f3-103">「可回收組件」是動態組件，不需要卸載其建立所在的應用程式定義域即可予以卸載。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-103">*Collectible assemblies* are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span> <span data-ttu-id="4c4f3-104">可以回收可回收組件所使用的所有受控和非受控記憶體與其包含的類型。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-104">All managed and unmanaged memory used by a collectible assembly and the types it contains can be reclaimed.</span></span> <span data-ttu-id="4c4f3-105">組件名稱這類資訊會從內部資料表中予以移除。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-105">Information such as the assembly name is removed from internal tables.</span></span>

<span data-ttu-id="4c4f3-106">若要啟用卸載，請在建立動態組件時使用 <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> 旗標。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-106">To enable unloading, use the <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> flag when you create a dynamic assembly.</span></span> <span data-ttu-id="4c4f3-107">組件是暫時性 (也就是無法儲存它) 並受限於[可回收組件的限制](#restrictions-on-collectible-assemblies)一節中所述的限制。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-107">The assembly is transient (that is, it cannot be saved) and is subject to limitations described in the [Restrictions on Collectible Assemblies](#restrictions-on-collectible-assemblies) section.</span></span> <span data-ttu-id="4c4f3-108">通用語言執行平台 (CLR) 會在您發行所有與組件建立關聯的物件時自動卸載可回收組件。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-108">The common language runtime (CLR) unloads a collectible assembly automatically when you release all objects associated with the assembly.</span></span> <span data-ttu-id="4c4f3-109">在所有其他方面，可回收組件的建立和使用方式都會與其他動態組件相同。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-109">In all other respects, collectible assemblies are created and used in the same way as other dynamic assemblies.</span></span>

## <a name="lifetime-of-collectible-assemblies"></a><span data-ttu-id="4c4f3-110">可回收組件的存留期</span><span class="sxs-lookup"><span data-stu-id="4c4f3-110">Lifetime of collectible assemblies</span></span>

<span data-ttu-id="4c4f3-111">可回收組件的存留期受控於是否有其所含類型以及從這些型別所建立之物件的參考。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-111">The lifetime of a collectible assembly is controlled by the existence of references to the types it contains and the objects that are created from those types.</span></span> <span data-ttu-id="4c4f3-112">只要有下列其中一或多個項目，通用語言執行平台就不會卸載組件 (`T` 是組件中定義的任何類型)：</span><span class="sxs-lookup"><span data-stu-id="4c4f3-112">The common language runtime does not unload an assembly as long as one or more of the following exist (`T` is any type that is defined in the assembly):</span></span> 

- <span data-ttu-id="4c4f3-113">`T` 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-113">An instance of `T`.</span></span>

- <span data-ttu-id="4c4f3-114">`T` 陣列的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-114">An instance of an array of `T`.</span></span>
 
- <span data-ttu-id="4c4f3-115">將 `T` 作為它的其中一個型別引數的泛型型別執行個體。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-115">An instance of a generic type that has `T` as one of its type arguments.</span></span> <span data-ttu-id="4c4f3-116">這包含 `T` 的泛型集合，即使該集合是空的也是一樣。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-116">This includes generic collections of `T`, even if that collection is empty.</span></span>

- <span data-ttu-id="4c4f3-117">表示 `T` 的 <xref:System.Type> 或 <xref:System.Reflection.Emit.TypeBuilder> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-117">An instance of <xref:System.Type> or <xref:System.Reflection.Emit.TypeBuilder> that represents `T`.</span></span> 

   > [!IMPORTANT]
   > <span data-ttu-id="4c4f3-118">您必須發行所有代表組件各部分的物件。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-118">You must release all objects that represent parts of the assembly.</span></span> <span data-ttu-id="4c4f3-119">定義 `T` 的 <xref:System.Reflection.Emit.ModuleBuilder> 會保留 <xref:System.Reflection.Emit.TypeBuilder> 的參考，而 <xref:System.Reflection.Emit.AssemblyBuilder> 物件會保留 <xref:System.Reflection.Emit.ModuleBuilder> 的參考，因此必須發行這些物件的參考。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-119">The <xref:System.Reflection.Emit.ModuleBuilder> that defines `T` keeps a reference to the <xref:System.Reflection.Emit.TypeBuilder>, and the <xref:System.Reflection.Emit.AssemblyBuilder> object keeps a reference to the <xref:System.Reflection.Emit.ModuleBuilder>, so references to these objects must be released.</span></span> <span data-ttu-id="4c4f3-120">即使建構 `T` 時已使用 <xref:System.Reflection.Emit.LocalBuilder> 或 <xref:System.Reflection.Emit.ILGenerator> 還是會防止卸載。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-120">Even the existence of a <xref:System.Reflection.Emit.LocalBuilder> or an <xref:System.Reflection.Emit.ILGenerator> used in the construction of `T` prevents unloading.</span></span>

- <span data-ttu-id="4c4f3-121">依另一個動態定義型別 `T1` 之 `T` 的靜態參考，而此動態定義型別仍然可以透過執行程式碼來取得。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-121">A static reference to `T` by another dynamically defined type `T1` that is still reachable by executing code.</span></span> <span data-ttu-id="4c4f3-122">例如，`T1` 可能衍生自 `T`，或 `T` 可能是 `T1` 的方法中的參數類型。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-122">For example, `T1` might derive from `T`, or `T` might be the type of a parameter in a method of `T1`.</span></span>
 
- <span data-ttu-id="4c4f3-123">屬於 `T` 之靜態欄位的 **ByRef**。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-123">A **ByRef** to a static field that belongs to `T`.</span></span>

- <span data-ttu-id="4c4f3-124"><xref:System.RuntimeTypeHandle>、<xref:System.RuntimeFieldHandle> 或 <xref:System.RuntimeMethodHandle>，可以參考 `T` 或 `T` 的元件。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-124">A <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>, or <xref:System.RuntimeMethodHandle> that refers to `T` or to a component of `T`.</span></span>

- <span data-ttu-id="4c4f3-125">任何反映物件執行個體，可以間接或直接用來存取代表 `T` 的 <xref:System.Type> 物件。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-125">An instance of any reflection object that could be used indirectly or directly to access the <xref:System.Type> object that represents `T`.</span></span> <span data-ttu-id="4c4f3-126">例如，`T` 的 <xref:System.Type> 物件可以從其項目類型為 `T` 的陣列類型取得，或從具有 `T` 作為型別引數的泛型型別取得。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-126">For example, the <xref:System.Type> object for `T` can be obtained from an array type whose element type is `T`, or from a generic type that has `T` as a type argument.</span></span> 

- <span data-ttu-id="4c4f3-127">任何執行緒呼叫堆疊上的方法 `M`，其中 `M` 是 `T` 的方法或是組件中所定義的模型層級方法。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-127">A method `M` on the call stack of any thread, where `M` is a method of `T` or a module-level method that is defined in the assembly.</span></span>

- <span data-ttu-id="4c4f3-128">定義於組件模組中之靜態方法的委派。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-128">A delegate to a static method that is defined in a module of the assembly.</span></span>

<span data-ttu-id="4c4f3-129">如果組件中的一個類型或一個方法在此清單中只有一個項目，則執行階段無法卸載組件。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-129">If only one item from this list exists for only one type or one method in the assembly, the runtime cannot unload the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="4c4f3-130">除非已針對清單中的所有項目執行完成項，否則執行階段不會實際卸載組件。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-130">The runtime does not actually unload the assembly until finalizers have run for all items in the list.</span></span>

<span data-ttu-id="4c4f3-131">基於追蹤存留期的目的，會將產生可回收組件時所建立和使用的建構化泛型型別 (例如，C# 中的 `List<int>` 或 Visual Basic 中的 `List(Of Integer)`) 視為已定義在包含泛型型別定義的組件中，或包含它的其中一個型別引號定義的組件中。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-131">For purposes of tracking lifetime, a constructed generic type such as `List<int>` (in C#) or `List(Of Integer)` (in Visual Basic) that is created and used in the generation of a collectible assembly is considered to have been defined either in the assembly that contains the generic type definition or in an assembly that contains the definition of one of its type arguments.</span></span> <span data-ttu-id="4c4f3-132">使用的確切組件是實作詳細資料，而且可能會變更。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-132">The exact assembly that is used is an implementation detail and subject to change.</span></span>
 
## <a name="restrictions-on-collectible-assemblies"></a><span data-ttu-id="4c4f3-133">可回收組件的限制</span><span class="sxs-lookup"><span data-stu-id="4c4f3-133">Restrictions on collectible assemblies</span></span>

<span data-ttu-id="4c4f3-134">下列限制適用於可回收組件：</span><span class="sxs-lookup"><span data-stu-id="4c4f3-134">The following restrictions apply to collectible assemblies:</span></span> 

- <span data-ttu-id="4c4f3-135">**靜態參考** </span><span class="sxs-lookup"><span data-stu-id="4c4f3-135">**Static references** </span></span>  
  <span data-ttu-id="4c4f3-136">一般動態組件中的類型不能有可回收組件中所定義型別的靜態參考。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-136">Types in an ordinary dynamic assembly cannot have static references to types that are defined in a collectible assembly.</span></span> <span data-ttu-id="4c4f3-137">例如，如果您定義繼承自可回收組件中類型的一般類型，則會擲回 <xref:System.NotSupportedException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-137">For example, if you define an ordinary type that inherits from a type in a collectible assembly, a <xref:System.NotSupportedException> exception is thrown.</span></span> <span data-ttu-id="4c4f3-138">可回收組件中的類型可以有另一個可回收組件中類型的靜態參考，但這會將已參考組件的存留期擴充為參考中組件的存留期。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-138">A type in a collectible assembly can have static references to a type in another collectible assembly, but this extends the lifetime of the referenced assembly to the lifetime of the referencing assembly.</span></span>

- <span data-ttu-id="4c4f3-139">**COM Interop** </span><span class="sxs-lookup"><span data-stu-id="4c4f3-139">**COM interop** </span></span>  
   <span data-ttu-id="4c4f3-140">在可回收組件內無法定義 COM 介面，而且可回收組件內的型別執行個體無法轉換為 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-140">No COM interfaces can be defined within a collectible assembly, and no instances of types within a collectible assembly can be converted into COM objects.</span></span> <span data-ttu-id="4c4f3-141">可回收組件中的類型不能作為 COM 可呼叫包裝函式 (CCW) 或執行階段可呼叫包裝函式 (RCW)。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-141">A type in a collectible assembly cannot serve as a COM callable wrapper (CCW) or runtime callable wrapper (RCW).</span></span> <span data-ttu-id="4c4f3-142">不過，可回收組件中的類型可以使用可實作 COM 介面的物件。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-142">However, types in collectible assemblies can use objects that implement COM interfaces.</span></span>

- <span data-ttu-id="4c4f3-143">**平台叫用** </span><span class="sxs-lookup"><span data-stu-id="4c4f3-143">**Platform invoke** </span></span>  
   <span data-ttu-id="4c4f3-144">具有 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性的方法在可回收組件中進行宣告時就不會進行編譯。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-144">Methods that have the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute will not compile when they are declared in a collectible assembly.</span></span> <span data-ttu-id="4c4f3-145"><xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> 指令不能用於可回收組件中的類型實作，而且無法將此等類型封送處理至非受控碼。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-145">The <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> instruction cannot be used in the implementation of a type in a collectible assembly, and such types cannot be marshaled to unmanaged code.</span></span> <span data-ttu-id="4c4f3-146">不過，您可以使用非可回收組件中所宣告的進入點來呼叫原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-146">However, you can call into native code by using an entry point that is declared in a non-collectible assembly.</span></span>
 
- <span data-ttu-id="4c4f3-147">**封送處理** </span><span class="sxs-lookup"><span data-stu-id="4c4f3-147">**Marshaling** </span></span>  
   <span data-ttu-id="4c4f3-148">無法封送處理可回收組件中所定義的物件 (特別是委派)。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-148">Objects (in particular, delegates) that are defined in collectible assemblies cannot be marshaled.</span></span> <span data-ttu-id="4c4f3-149">這是所有暫時發出型別的限制。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-149">This is a restriction on all transient emitted types.</span></span>

- <span data-ttu-id="4c4f3-150">**組件載入** </span><span class="sxs-lookup"><span data-stu-id="4c4f3-150">**Assembly loading** </span></span>  
   <span data-ttu-id="4c4f3-151">反映發出是唯一支援載入可回收組件的機制。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-151">Reflection emit is the only mechanism that is supported for loading collectible assemblies.</span></span> <span data-ttu-id="4c4f3-152">無法卸載使用其他任何形式的組件載入所載入的組件。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-152">Assemblies that are loaded by using any other form of assembly loading cannot be unloaded.</span></span>
 
- <span data-ttu-id="4c4f3-153">**內容繫結物件**  </span><span class="sxs-lookup"><span data-stu-id="4c4f3-153">**Context-bound objects**  </span></span>  
   <span data-ttu-id="4c4f3-154">不支援內容靜態變數。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-154">Context-static variables are not supported.</span></span> <span data-ttu-id="4c4f3-155">可回收組件中的類型無法擴充 <xref:System.ContextBoundObject>。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-155">Types in a collectible assembly cannot extend <xref:System.ContextBoundObject>.</span></span> <span data-ttu-id="4c4f3-156">不過，可回收組件中的程式碼可以使用在其他位置定義的內容繫結物件。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-156">However, code in collectible assemblies can use context-bound objects that are defined elsewhere.</span></span>

- <span data-ttu-id="4c4f3-157">**執行緒靜態資料**     </span><span class="sxs-lookup"><span data-stu-id="4c4f3-157">**Thread-static data**     </span></span>  
   <span data-ttu-id="4c4f3-158">不支援執行緒靜態變數。</span><span class="sxs-lookup"><span data-stu-id="4c4f3-158">Thread-static variables are not supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c4f3-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c4f3-159">See also</span></span>

- [<span data-ttu-id="4c4f3-160">發出動態方法和組件</span><span class="sxs-lookup"><span data-stu-id="4c4f3-160">Emitting Dynamic Methods and Assemblies</span></span>](emitting-dynamic-methods-and-assemblies.md)
