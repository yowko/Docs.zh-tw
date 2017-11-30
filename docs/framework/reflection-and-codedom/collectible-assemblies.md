---
title: "動態類型產生可回收組件"
description: 
ms.date: 08/29/2017
ms.prod: .net
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c9a613f4cc13c3e4189a59ace2e05d01d1bcb4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a><span data-ttu-id="fab65-102">動態類型產生可回收組件</span><span class="sxs-lookup"><span data-stu-id="fab65-102">Collectible assemblies for dynamic type generation</span></span>

<span data-ttu-id="fab65-103">*可回收組件*是動態組件，而不卸載它們建立所在的應用程式定義域可以卸載。</span><span class="sxs-lookup"><span data-stu-id="fab65-103">*Collectible assemblies* are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span> <span data-ttu-id="fab65-104">可回收組件和它所包含的型別所使用的所有 managed 和 unmanaged 記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="fab65-104">All managed and unmanaged memory used by a collectible assembly and the types it contains can be reclaimed.</span></span> <span data-ttu-id="fab65-105">組件名稱等資訊是從內部資料表中移除。</span><span class="sxs-lookup"><span data-stu-id="fab65-105">Information such as the assembly name is removed from internal tables.</span></span>

<span data-ttu-id="fab65-106">若要啟用卸載，請使用<xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType>旗標，當您建立動態組件。</span><span class="sxs-lookup"><span data-stu-id="fab65-106">To enable unloading, use the <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> flag when you create a dynamic assembly.</span></span> <span data-ttu-id="fab65-107">組件是暫時性 （也就是它不能儲存） 而且受限於中所述限制[可回收組件的限制](#restrictions-on-collectible-assemblies)> 一節。</span><span class="sxs-lookup"><span data-stu-id="fab65-107">The assembly is transient (that is, it cannot be saved) and is subject to limitations described in the [Restrictions on Collectible Assemblies](#restrictions-on-collectible-assemblies) section.</span></span> <span data-ttu-id="fab65-108">Common language runtime (CLR) 會自動卸載可回收組件，當您發行組件相關聯的所有物件。</span><span class="sxs-lookup"><span data-stu-id="fab65-108">The common language runtime (CLR) unloads a collectible assembly automatically when you release all objects associated with the assembly.</span></span> <span data-ttu-id="fab65-109">在其他方面，可回收組件會建立和使用方式與其他動態組件相同。</span><span class="sxs-lookup"><span data-stu-id="fab65-109">In all other respects, collectible assemblies are created and used in the same way as other dynamic assemblies.</span></span>

## <a name="lifetime-of-collectible-assemblies"></a><span data-ttu-id="fab65-110">可回收組件的存留期</span><span class="sxs-lookup"><span data-stu-id="fab65-110">Lifetime of collectible assemblies</span></span>

<span data-ttu-id="fab65-111">可回收組件的存留期會控制所包含的類型以及從這些型別所建立的物件參考存在。</span><span class="sxs-lookup"><span data-stu-id="fab65-111">The lifetime of a collectible assembly is controlled by the existence of references to the types it contains and the objects that are created from those types.</span></span> <span data-ttu-id="fab65-112">Common language runtime 不會卸載組件，只要有一個或多個項目存在 (`T`組件中定義的所有類型):</span><span class="sxs-lookup"><span data-stu-id="fab65-112">The common language runtime does not unload an assembly as long as one or more of the following exist (`T` is any type that is defined in the assembly):</span></span> 

- <span data-ttu-id="fab65-113">`T` 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fab65-113">An instance of `T`.</span></span>

- <span data-ttu-id="fab65-114">陣列的執行個體`T`。</span><span class="sxs-lookup"><span data-stu-id="fab65-114">An instance of an array of `T`.</span></span>
 
- <span data-ttu-id="fab65-115">具有泛型類型的執行個體`T`做為其中一個型別引數。</span><span class="sxs-lookup"><span data-stu-id="fab65-115">An instance of a generic type that has `T` as one of its type arguments.</span></span> <span data-ttu-id="fab65-116">這包括的泛型集合`T`，即使該集合是空的。</span><span class="sxs-lookup"><span data-stu-id="fab65-116">This includes generic collections of `T`, even if that collection is empty.</span></span>

- <span data-ttu-id="fab65-117">執行個體<xref:System.Type>或<xref:System.Reflection.Emit.TypeBuilder>表示`T`。</span><span class="sxs-lookup"><span data-stu-id="fab65-117">An instance of <xref:System.Type> or <xref:System.Reflection.Emit.TypeBuilder> that represents `T`.</span></span> 

   > [!IMPORTANT]
   > <span data-ttu-id="fab65-118">您必須釋放所有物件，代表組件的部分。</span><span class="sxs-lookup"><span data-stu-id="fab65-118">You must release all objects that represent parts of the assembly.</span></span> <span data-ttu-id="fab65-119"><xref:System.Reflection.Emit.ModuleBuilder>定義`T`會保留參考<xref:System.Reflection.Emit.TypeBuilder>，而<xref:System.Reflection.Emit.AssemblyBuilder>物件會保留參考<xref:System.Reflection.Emit.ModuleBuilder>，因此必須釋放這些物件的參考。</span><span class="sxs-lookup"><span data-stu-id="fab65-119">The <xref:System.Reflection.Emit.ModuleBuilder> that defines `T` keeps a reference to the <xref:System.Reflection.Emit.TypeBuilder>, and the <xref:System.Reflection.Emit.AssemblyBuilder> object keeps a reference to the <xref:System.Reflection.Emit.ModuleBuilder>, so references to these objects must be released.</span></span> <span data-ttu-id="fab65-120">即使有<xref:System.Reflection.Emit.LocalBuilder>或<xref:System.Reflection.Emit.ILGenerator>之建構中使用`T`可避免卸載。</span><span class="sxs-lookup"><span data-stu-id="fab65-120">Even the existence of a <xref:System.Reflection.Emit.LocalBuilder> or an <xref:System.Reflection.Emit.ILGenerator> used in the construction of `T` prevents unloading.</span></span>

- <span data-ttu-id="fab65-121">靜態參考`T`其他動態定義的型別來`T1`這仍可執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="fab65-121">A static reference to `T` by another dynamically defined type `T1` that is still reachable by executing code.</span></span> <span data-ttu-id="fab65-122">例如，`T1`可能會衍生自`T`，或`T`可能是在方法中參數的型別`T1`。</span><span class="sxs-lookup"><span data-stu-id="fab65-122">For example, `T1` might derive from `T`, or `T` might be the type of a parameter in a method of `T1`.</span></span>
 
- <span data-ttu-id="fab65-123">A **ByRef**至靜態欄位所屬`T`。</span><span class="sxs-lookup"><span data-stu-id="fab65-123">A **ByRef** to a static field that belongs to `T`.</span></span>

- <span data-ttu-id="fab65-124">A <xref:System.RuntimeTypeHandle>， <xref:System.RuntimeFieldHandle>，或<xref:System.RuntimeMethodHandle>參考`T`或元件的`T`。</span><span class="sxs-lookup"><span data-stu-id="fab65-124">A <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>, or <xref:System.RuntimeMethodHandle> that refers to `T` or to a component of `T`.</span></span>

- <span data-ttu-id="fab65-125">執行任何的個體無法間接使用的反映物件或直接存取<xref:System.Type>物件，代表`T`。</span><span class="sxs-lookup"><span data-stu-id="fab65-125">An instance of any reflection object that could be used indirectly or directly to access the <xref:System.Type> object that represents `T`.</span></span> <span data-ttu-id="fab65-126">例如，<xref:System.Type>物件`T`可以從其項目類型是陣列型別取得`T`，或從具有泛型型別`T`作為類型引數。</span><span class="sxs-lookup"><span data-stu-id="fab65-126">For example, the <xref:System.Type> object for `T` can be obtained from an array type whose element type is `T`, or from a generic type that has `T` as a type argument.</span></span> 

- <span data-ttu-id="fab65-127">方法`M`任何執行緒的呼叫堆疊上其中`M`是一種方法的`T`或組件中定義的模組層級方法。</span><span class="sxs-lookup"><span data-stu-id="fab65-127">A method `M` on the call stack of any thread, where `M` is a method of `T` or a module-level method that is defined in the assembly.</span></span>

- <span data-ttu-id="fab65-128">定義組件的模組中的靜態方法的委派。</span><span class="sxs-lookup"><span data-stu-id="fab65-128">A delegate to a static method that is defined in a module of the assembly.</span></span>

<span data-ttu-id="fab65-129">如果只有一個項目從這個清單有只有一個型別或組件中的一個方法，執行階段無法卸載組件。</span><span class="sxs-lookup"><span data-stu-id="fab65-129">If only one item from this list exists for only one type or one method in the assembly, the runtime cannot unload the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="fab65-130">執行階段不會實際卸載組件清單中的所有項目執行完成項之前。</span><span class="sxs-lookup"><span data-stu-id="fab65-130">The runtime does not actually unload the assembly until finalizers have run for all items in the list.</span></span>

<span data-ttu-id="fab65-131">基於追蹤存留期的詳細資訊，建構的泛型類型例如`List<int>`（C# 中） 或`List(Of Integer)`（在 Visual Basic)，是建立，而且用於產生可回收組件會被視為已定義組件中，包含泛型類型定義，或是在組件包含的其中一個型別引數的定義。</span><span class="sxs-lookup"><span data-stu-id="fab65-131">For purposes of tracking lifetime, a constructed generic type such as `List<int>` (in C#) or `List(Of Integer)` (in Visual Basic) that is created and used in the generation of a collectible assembly is considered to have been defined either in the assembly that contains the generic type definition or in an assembly that contains the definition of one of its type arguments.</span></span> <span data-ttu-id="fab65-132">使用的確切組件是實作詳細資料和可能有所變更。</span><span class="sxs-lookup"><span data-stu-id="fab65-132">The exact assembly that is used is an implementation detail and subject to change.</span></span>
 
## <a name="restrictions-on-collectible-assemblies"></a><span data-ttu-id="fab65-133">可回收組件的限制</span><span class="sxs-lookup"><span data-stu-id="fab65-133">Restrictions on collectible assemblies</span></span>

<span data-ttu-id="fab65-134">下列限制適用於可回收組件：</span><span class="sxs-lookup"><span data-stu-id="fab65-134">The following restrictions apply to collectible assemblies:</span></span> 

- <span data-ttu-id="fab65-135">**靜態參考** </span><span class="sxs-lookup"><span data-stu-id="fab65-135">**Static references** </span></span>  
  <span data-ttu-id="fab65-136">一般的動態組件中的類型不能有靜態參考可回收組件中定義的類型。</span><span class="sxs-lookup"><span data-stu-id="fab65-136">Types in an ordinary dynamic assembly cannot have static references to types that are defined in a collectible assembly.</span></span> <span data-ttu-id="fab65-137">例如，如果您定義一般型別繼承自可回收組件中的型別<xref:System.NotSupportedException>擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fab65-137">For example, if you define an ordinary type that inherits from a type in a collectible assembly, a <xref:System.NotSupportedException> exception is thrown.</span></span> <span data-ttu-id="fab65-138">可回收組件中的型別可以有類型的靜態參考另一個可回收組件，但這會擴充參考的組件參考的組件的存留期的存留期。</span><span class="sxs-lookup"><span data-stu-id="fab65-138">A type in a collectible assembly can have static references to a type in another collectible assembly, but this extends the lifetime of the referenced assembly to the lifetime of the referencing assembly.</span></span>

- <span data-ttu-id="fab65-139">**COM interop** </span><span class="sxs-lookup"><span data-stu-id="fab65-139">**COM interop** </span></span>  
   <span data-ttu-id="fab65-140">COM 介面都不可以定義內可回收組件，並為可回收組件中類型的任何執行個體都可以轉換為 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="fab65-140">No COM interfaces can be defined within a collectible assembly, and no instances of types within a collectible assembly can be converted into COM objects.</span></span> <span data-ttu-id="fab65-141">可回收組件中的類型不能做為 COM 可呼叫包裝函式 (CCW) 或執行階段可呼叫包裝函式 (RCW)。</span><span class="sxs-lookup"><span data-stu-id="fab65-141">A type in a collectible assembly cannot serve as a COM callable wrapper (CCW) or runtime callable wrapper (RCW).</span></span> <span data-ttu-id="fab65-142">不過，可回收組件中的型別可以使用實作 COM 介面的物件。</span><span class="sxs-lookup"><span data-stu-id="fab65-142">However, types in collectible assemblies can use objects that implement COM interfaces.</span></span>

- <span data-ttu-id="fab65-143">**平台叫用** </span><span class="sxs-lookup"><span data-stu-id="fab65-143">**Platform invoke** </span></span>  
   <span data-ttu-id="fab65-144">具有方法<xref:System.Runtime.InteropServices.DllImportAttribute>可回收組件中宣告時，不會編譯屬性。</span><span class="sxs-lookup"><span data-stu-id="fab65-144">Methods that have the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute will not compile when they are declared in a collectible assembly.</span></span> <span data-ttu-id="fab65-145"><xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType>指令不能用於在可回收組件，類型的實作，這類類型無法封送處理至 unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="fab65-145">The <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> instruction cannot be used in the implementation of a type in a collectible assembly, and such types cannot be marshaled to unmanaged code.</span></span> <span data-ttu-id="fab65-146">不過，您可以呼叫原生程式碼使用宣告非可回收組件中的進入點。</span><span class="sxs-lookup"><span data-stu-id="fab65-146">However, you can call into native code by using an entry point that is declared in a non-collectible assembly.</span></span>
 
- <span data-ttu-id="fab65-147">**封送處理** </span><span class="sxs-lookup"><span data-stu-id="fab65-147">**Marshaling** </span></span>  
   <span data-ttu-id="fab65-148">無法封送處理 （特別是在委派） 中可回收組件中定義的物件。</span><span class="sxs-lookup"><span data-stu-id="fab65-148">Objects (in particular, delegates) that are defined in collectible assemblies cannot be marshaled.</span></span> <span data-ttu-id="fab65-149">這是所有的暫時性發出型別上的限制。</span><span class="sxs-lookup"><span data-stu-id="fab65-149">This is a restriction on all transient emitted types.</span></span>

- <span data-ttu-id="fab65-150">**載入的組件** </span><span class="sxs-lookup"><span data-stu-id="fab65-150">**Assembly loading** </span></span>  
   <span data-ttu-id="fab65-151">反映發出時，才支援載入可回收組件的唯一機制。</span><span class="sxs-lookup"><span data-stu-id="fab65-151">Reflection emit is the only mechanism that is supported for loading collectible assemblies.</span></span> <span data-ttu-id="fab65-152">載入使用其他任何形式的組件載入的組件無法卸載。</span><span class="sxs-lookup"><span data-stu-id="fab65-152">Assemblies that are loaded by using any other form of assembly loading cannot be unloaded.</span></span>
 
- <span data-ttu-id="fab65-153">**內容繫結物件**  </span><span class="sxs-lookup"><span data-stu-id="fab65-153">**Context-bound objects**  </span></span>  
   <span data-ttu-id="fab65-154">不支援 context 靜態變數。</span><span class="sxs-lookup"><span data-stu-id="fab65-154">Context-static variables are not supported.</span></span> <span data-ttu-id="fab65-155">可回收組件中的類型無法擴充<xref:System.ContextBoundObject>。</span><span class="sxs-lookup"><span data-stu-id="fab65-155">Types in a collectible assembly cannot extend <xref:System.ContextBoundObject>.</span></span> <span data-ttu-id="fab65-156">不過，可回收組件中的程式碼可以其他地方使用內容繫結所定義的物件。</span><span class="sxs-lookup"><span data-stu-id="fab65-156">However, code in collectible assemblies can use context-bound objects that are defined elsewhere.</span></span>

- <span data-ttu-id="fab65-157">**執行緒靜態資料**     </span><span class="sxs-lookup"><span data-stu-id="fab65-157">**Thread-static data**     </span></span>  
   <span data-ttu-id="fab65-158">不支援執行緒靜態變數。</span><span class="sxs-lookup"><span data-stu-id="fab65-158">Thread-static variables are not supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="fab65-159">請參閱</span><span class="sxs-lookup"><span data-stu-id="fab65-159">See also</span></span>

[<span data-ttu-id="fab65-160">發出動態方法和組件</span><span class="sxs-lookup"><span data-stu-id="fab65-160">Emitting Dynamic Methods and Assemblies</span></span>](emitting-dynamic-methods-and-assemblies.md)
