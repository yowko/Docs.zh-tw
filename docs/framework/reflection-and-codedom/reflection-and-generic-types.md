---
title: 反映和泛用類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic types
- reflection, generic types
- type arguments
- generics [.NET Framework], reflection
- viewing type information
- type information, viewing
- types, generic
- type parameters
ms.assetid: f7180fc5-dd41-42d4-8a8e-1b34288e06de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05b1d80887186466044acdb088d7f45a386b37f7
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364040"
---
# <a name="reflection-and-generic-types"></a><span data-ttu-id="a793e-102">反映和泛用類型</span><span class="sxs-lookup"><span data-stu-id="a793e-102">Reflection and Generic Types</span></span>
<a name="top"></a> <span data-ttu-id="a793e-103">從反映的的觀點來看，泛型類型與一般類型間的差異在於泛型類型具有與其相關聯的一組類型參數 (若其定義為泛型類型) 或類型引數 (若其為建構類型)。</span><span class="sxs-lookup"><span data-stu-id="a793e-103">From the point of view of reflection, the difference between a generic type and an ordinary type is that a generic type has associated with it a set of type parameters (if it is a generic type definition) or type arguments (if it is a constructed type).</span></span> <span data-ttu-id="a793e-104">泛型方法與一般方法的差異也如同上述。</span><span class="sxs-lookup"><span data-stu-id="a793e-104">A generic method differs from an ordinary method in the same way.</span></span>  
  
 <span data-ttu-id="a793e-105">了解反映如何處理泛型類型和方法有兩種方式：</span><span class="sxs-lookup"><span data-stu-id="a793e-105">There are two keys to understanding how reflection handles generic types and methods:</span></span>  
  
- <span data-ttu-id="a793e-106"><xref:System.Type> 類別的執行個體，代表泛型類型定義與泛型方法定義的類型參數。</span><span class="sxs-lookup"><span data-stu-id="a793e-106">The type parameters of generic type definitions and generic method definitions are represented by instances of the <xref:System.Type> class.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a793e-107"><xref:System.Type> 物件代表泛型類型參數時，許多 <xref:System.Type> 的屬性與方法會有不同的行為。</span><span class="sxs-lookup"><span data-stu-id="a793e-107">Many properties and methods of <xref:System.Type> have different behavior when a <xref:System.Type> object represents a generic type parameter.</span></span> <span data-ttu-id="a793e-108">這些差異皆記錄在屬性與方法主題中。</span><span class="sxs-lookup"><span data-stu-id="a793e-108">These differences are documented in the property and method topics.</span></span> <span data-ttu-id="a793e-109">如需範例，請參閱 <xref:System.Type.IsAutoClass%2A> 與 <xref:System.Type.DeclaringType%2A>。</span><span class="sxs-lookup"><span data-stu-id="a793e-109">For example, see <xref:System.Type.IsAutoClass%2A> and <xref:System.Type.DeclaringType%2A>.</span></span> <span data-ttu-id="a793e-110">此外，部分成員僅限於 <xref:System.Type> 物件代表泛型類型參數時才有效。</span><span class="sxs-lookup"><span data-stu-id="a793e-110">In addition, some members are valid only when a <xref:System.Type> object represents a generic type parameter.</span></span> <span data-ttu-id="a793e-111">如需範例，請參閱 <xref:System.Type.GetGenericTypeDefinition%2A>。</span><span class="sxs-lookup"><span data-stu-id="a793e-111">For example, see <xref:System.Type.GetGenericTypeDefinition%2A>.</span></span>  
  
- <span data-ttu-id="a793e-112">如果 <xref:System.Type> 的執行個體代表泛型類型，則其包含一個代表類型參數 (若是泛型類型定義) 或代表類型引數 (若是建構類型) 的類型陣列。</span><span class="sxs-lookup"><span data-stu-id="a793e-112">If an instance of <xref:System.Type> represents a generic type, then it includes an array of types that represent the type parameters (for generic type definitions) or the type arguments (for constructed types).</span></span> <span data-ttu-id="a793e-113">上述同樣適用於代表泛型方法之 <xref:System.Reflection.MethodInfo> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a793e-113">The same is true of an instance of the <xref:System.Reflection.MethodInfo> class that represents a generic method.</span></span>  
  
 <span data-ttu-id="a793e-114">反映提供允許您存取類型參數陣列之 <xref:System.Type> 和 <xref:System.Reflection.MethodInfo> 的方法，並決定 <xref:System.Type> 的執行個體是否代表類型參數或實際的類型。</span><span class="sxs-lookup"><span data-stu-id="a793e-114">Reflection provides methods of <xref:System.Type> and <xref:System.Reflection.MethodInfo> that allow you to access the array of type parameters, and to determine whether an instance of <xref:System.Type> represents a type parameter or an actual type.</span></span>  
  
 <span data-ttu-id="a793e-115">如需示範此處討論之方法的範例程式碼，請參閱[如何：使用反映檢查和具現化泛型型別](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="a793e-115">For example code demonstrating the methods discussed here, see [How to: Examine and Instantiate Generic Types with Reflection](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="a793e-116">下列討論假設您熟悉泛型術語，例如類型參數與引數之間的差異，以及引數與開放式或封閉式的建構類型。</span><span class="sxs-lookup"><span data-stu-id="a793e-116">The following discussion assumes familiarity with the terminology of generics, such as the difference between type parameters and arguments and open or closed constructed types.</span></span> <span data-ttu-id="a793e-117">如需詳細資訊，請參閱[泛型](../../../docs/standard/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a793e-117">For more information, see [Generics](../../../docs/standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="a793e-118">本概觀包含下列各節：</span><span class="sxs-lookup"><span data-stu-id="a793e-118">This overview consists of the following sections:</span></span>  
  
- [<span data-ttu-id="a793e-119">這是泛型類型或泛型方法？</span><span class="sxs-lookup"><span data-stu-id="a793e-119">Is This a Generic Type or Method?</span></span>](#is_this_a_generic_type_or_method)  
  
- [<span data-ttu-id="a793e-120">產生封閉式泛型類型</span><span class="sxs-lookup"><span data-stu-id="a793e-120">Generating Closed Generic Types</span></span>](#generating_closed_generic_types)  
  
- [<span data-ttu-id="a793e-121">檢查類型引數與類型參數</span><span class="sxs-lookup"><span data-stu-id="a793e-121">Examining Type Arguments and Type Parameters</span></span>](#examining_type_arguments)  
  
- [<span data-ttu-id="a793e-122">非變異值</span><span class="sxs-lookup"><span data-stu-id="a793e-122">Invariants</span></span>](#invariants)  
  
- [<span data-ttu-id="a793e-123">相關主題</span><span class="sxs-lookup"><span data-stu-id="a793e-123">Related Topics</span></span>](#related_topics)  
  
<a name="is_this_a_generic_type_or_method"></a>   
## <a name="is-this-a-generic-type-or-method"></a><span data-ttu-id="a793e-124">這是泛型類型或泛型方法？</span><span class="sxs-lookup"><span data-stu-id="a793e-124">Is This a Generic Type or Method?</span></span>  
 <span data-ttu-id="a793e-125">當您使用反映來查看未知的類型 (以 <xref:System.Type>的執行個體表示) 時，請使用 <xref:System.Type.IsGenericType%2A> 屬性來決定未知類型是否為泛型。</span><span class="sxs-lookup"><span data-stu-id="a793e-125">When you use reflection to examine an unknown type, represented by an instance of <xref:System.Type>, use the <xref:System.Type.IsGenericType%2A> property to determine whether the unknown type is generic.</span></span> <span data-ttu-id="a793e-126">如果類型為泛型，其將傳回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="a793e-126">It returns `true` if the type is generic.</span></span> <span data-ttu-id="a793e-127">同樣地，查看未知的方法 (以 <xref:System.Reflection.MethodInfo> 類別的執行個體表示) 時，請使用 <xref:System.Reflection.MethodBase.IsGenericMethod%2A> 屬性來決定方法是否為泛型。</span><span class="sxs-lookup"><span data-stu-id="a793e-127">Similarly, when you examine an unknown method, represented by an instance of the <xref:System.Reflection.MethodInfo> class, use the <xref:System.Reflection.MethodBase.IsGenericMethod%2A> property to determine whether the method is generic.</span></span>  
  
### <a name="is-this-a-generic-type-or-method-definition"></a><span data-ttu-id="a793e-128">這是泛型類型或方法定義？</span><span class="sxs-lookup"><span data-stu-id="a793e-128">Is This a Generic Type or Method Definition?</span></span>  
 <span data-ttu-id="a793e-129">使用 <xref:System.Type.IsGenericTypeDefinition%2A> 屬性來決定 <xref:System.Type> 物件是否代表泛型類型定義，並使用 <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> 方法來決定 <xref:System.Reflection.MethodInfo> 是否代表泛型方法定義。</span><span class="sxs-lookup"><span data-stu-id="a793e-129">Use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether a <xref:System.Type> object represents a generic type definition, and use the <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> method to determine whether a <xref:System.Reflection.MethodInfo> represents a generic method definition.</span></span>  
  
 <span data-ttu-id="a793e-130">泛型類型與方法定義為建立執行個體類型的範本。</span><span class="sxs-lookup"><span data-stu-id="a793e-130">Generic type and method definitions are the templates from which instantiable types are created.</span></span> <span data-ttu-id="a793e-131">.NET Framwork 類別庫中的泛型類型 (例如 <xref:System.Collections.Generic.Dictionary%602>) 是泛型類型定義。</span><span class="sxs-lookup"><span data-stu-id="a793e-131">Generic types in the .NET Framework class library, such as <xref:System.Collections.Generic.Dictionary%602>, are generic type definitions.</span></span>  
  
### <a name="is-the-type-or-method-open-or-closed"></a><span data-ttu-id="a793e-132">類型 (或方法) 為開放式或是封閉式？</span><span class="sxs-lookup"><span data-stu-id="a793e-132">Is the Type or Method Open or Closed?</span></span>  
 <span data-ttu-id="a793e-133">如果可具現化類型已取代其所有類型參數 (包括所有封入類型的類型參數)，則泛型類型或方法為封閉式。</span><span class="sxs-lookup"><span data-stu-id="a793e-133">A generic type or method is closed if instantiable types have been substituted for all its type parameters, including all the type parameters of all enclosing types.</span></span> <span data-ttu-id="a793e-134">如果類型為封閉式，則您僅能建立泛型類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a793e-134">You can only create an instance of a generic type if it is closed.</span></span> <span data-ttu-id="a793e-135">如果類型為開放式，則 <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> 屬性會傳回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="a793e-135">The <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> property returns `true` if a type is open.</span></span> <span data-ttu-id="a793e-136">若是方法，則 <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> 方法會執行相同的函式。</span><span class="sxs-lookup"><span data-stu-id="a793e-136">For methods, the <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> method performs the same function.</span></span>  
  
 [<span data-ttu-id="a793e-137">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a793e-137">Back to top</span></span>](#top)  
  
<a name="generating_closed_generic_types"></a>   
## <a name="generating-closed-generic-types"></a><span data-ttu-id="a793e-138">產生封閉式泛型類型</span><span class="sxs-lookup"><span data-stu-id="a793e-138">Generating Closed Generic Types</span></span>  
 <span data-ttu-id="a793e-139">若您有泛型類型或方法定義，使用 <xref:System.Type.MakeGenericType%2A> 方法可建立封閉式泛型類型，而使用 <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> 方法則會為封閉式泛型方法建立 <xref:System.Reflection.MethodInfo> 。</span><span class="sxs-lookup"><span data-stu-id="a793e-139">Once you have a generic type or method definition, use the <xref:System.Type.MakeGenericType%2A> method to create a closed generic type or the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> method to create a <xref:System.Reflection.MethodInfo> for a closed generic method.</span></span>  
  
### <a name="getting-the-generic-type-or-method-definition"></a><span data-ttu-id="a793e-140">取得泛型類型或方法定義</span><span class="sxs-lookup"><span data-stu-id="a793e-140">Getting the Generic Type or Method Definition</span></span>  
 <span data-ttu-id="a793e-141">開放式類型或方法若不是泛型類型或方法定義，則無法建立該類型或方法的執行個體，且無法提供遺失的類型參數。</span><span class="sxs-lookup"><span data-stu-id="a793e-141">If you have an open generic type or method that is not a generic type or method definition, you cannot create instances of it and you cannot supply the type parameters that are missing.</span></span> <span data-ttu-id="a793e-142">您必須具有泛型類型或泛型定義。</span><span class="sxs-lookup"><span data-stu-id="a793e-142">You must have a generic type or method definition.</span></span> <span data-ttu-id="a793e-143">使用 <xref:System.Type.GetGenericTypeDefinition%2A> 方法可取得泛型類型定義，而使用 <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> 方法則可取得泛型方法定義。</span><span class="sxs-lookup"><span data-stu-id="a793e-143">Use the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition or the <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> method to obtain the generic method definition.</span></span>  
  
 <span data-ttu-id="a793e-144">例如，如果您有代表 <xref:System.Type> (在 Visual Basic 中為 `Dictionary<int, string>` ) 的`Dictionary(Of Integer, String)` 物件，而想要建立類型 `Dictionary<string, MyClass>`，可以使用 <xref:System.Type.GetGenericTypeDefinition%2A> 方法來取得代表 <xref:System.Type> 的 `Dictionary<TKey, TValue>` ，然後使用 <xref:System.Type.MakeGenericType%2A> 方法以產生代表 <xref:System.Type> 的 `Dictionary<int, MyClass>`。</span><span class="sxs-lookup"><span data-stu-id="a793e-144">For example, if you have a <xref:System.Type> object representing `Dictionary<int, string>` (`Dictionary(Of Integer, String)` in Visual Basic) and you want to create the type `Dictionary<string, MyClass>`, you can use the <xref:System.Type.GetGenericTypeDefinition%2A> method to get a <xref:System.Type> representing `Dictionary<TKey, TValue>` and then use the <xref:System.Type.MakeGenericType%2A> method to produce a <xref:System.Type> representing `Dictionary<int, MyClass>`.</span></span>  
  
 <span data-ttu-id="a793e-145">以不是泛型類型的開放式泛型類型為例，請參閱本主題稍後的＜類型參數或類型引數＞。</span><span class="sxs-lookup"><span data-stu-id="a793e-145">For an example of an open generic type that is not a generic type, see "Type Parameter or Type Argument" later in this topic.</span></span>  
  
 [<span data-ttu-id="a793e-146">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a793e-146">Back to top</span></span>](#top)  
  
<a name="examining_type_arguments"></a>   
## <a name="examining-type-arguments-and-type-parameters"></a><span data-ttu-id="a793e-147">檢查類型引數與類型參數</span><span class="sxs-lookup"><span data-stu-id="a793e-147">Examining Type Arguments and Type Parameters</span></span>  
 <span data-ttu-id="a793e-148">使用 <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> 方法可取得代表泛型類型之類型參數或類型引數之 <xref:System.Type> 物件的陣列，若是泛型方法則請使用 <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> 方法以相同的方式取得陣列。</span><span class="sxs-lookup"><span data-stu-id="a793e-148">Use the <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> method to obtain an array of <xref:System.Type> objects that represent the type parameters or type arguments of a generic type, and use the <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> method to do the same for a generic method.</span></span>  
  
 <span data-ttu-id="a793e-149">如果您已了解代表類型參數的 <xref:System.Type> 物件，則反映能夠回答許多額外的問題。</span><span class="sxs-lookup"><span data-stu-id="a793e-149">Once you know that a <xref:System.Type> object represents a type parameter, there are many additional questions reflection can answer.</span></span> <span data-ttu-id="a793e-150">您可以決定類型參數的來源、其位置，及其條件約束。</span><span class="sxs-lookup"><span data-stu-id="a793e-150">You can determine the type parameter's source, its position, and its constraints.</span></span>  
  
### <a name="type-parameter-or-type-argument"></a><span data-ttu-id="a793e-151">類型參數或類型引數</span><span class="sxs-lookup"><span data-stu-id="a793e-151">Type Parameter or Type Argument</span></span>  
 <span data-ttu-id="a793e-152">若要判斷陣列的特定元素是類型參數或類型引數，請使用 <xref:System.Type.IsGenericParameter%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a793e-152">To determine whether a particular element of the array is a type parameter or a type argument, use the <xref:System.Type.IsGenericParameter%2A> property.</span></span> <span data-ttu-id="a793e-153">如果元素是類型參數，則 <xref:System.Type.IsGenericParameter%2A> 屬性為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="a793e-153">The <xref:System.Type.IsGenericParameter%2A> property is `true` if the element is a type parameter.</span></span>  
  
 <span data-ttu-id="a793e-154">泛型類型可以在不是泛型類型定義的情況下開啟，此時其具有類型引數和類型參數的混合。</span><span class="sxs-lookup"><span data-stu-id="a793e-154">A generic type can be open without being a generic type definition, in which case it has a mixture of type arguments and type parameters.</span></span> <span data-ttu-id="a793e-155">以下列程式碼為例，類別 `D` 衍生自類型，該類型的第一個類型參數由 `D` 所取代，第二個類型參數則由 `B`取代。</span><span class="sxs-lookup"><span data-stu-id="a793e-155">For example, in the following code, class `D` derives from a type created by substituting the first type parameter of `D` for the second type parameter of `B`.</span></span>  
  
```csharp  
class B<T, U> {}  
class D<V, W> : B<int, V> {}  
```  
  
```vb  
Class B(Of T, U)  
End Class  
Class D(Of V, W)  
    Inherits B(Of Integer, V)  
End Class  
```  
  
```cpp  
generic<typename T, typename U> ref class B {};  
generic<typename V, typename W> ref class D : B<int, V> {};  
```  
  
 <span data-ttu-id="a793e-156">如果您取得代表 <xref:System.Type> 的 `D<V, W>` 物件，並使用 <xref:System.Type.BaseType%2A> 屬性以取得其基底類型，所產生的 `type B<int, V>` 就會是開放式，但其不是泛型類型定義。</span><span class="sxs-lookup"><span data-stu-id="a793e-156">If you obtain a <xref:System.Type> object representing `D<V, W>` and use the <xref:System.Type.BaseType%2A> property to obtain its base type, the resulting `type B<int, V>` is open, but it is not a generic type definition.</span></span>  
  
### <a name="source-of-a-generic-parameter"></a><span data-ttu-id="a793e-157">泛型參數的來源</span><span class="sxs-lookup"><span data-stu-id="a793e-157">Source of a Generic Parameter</span></span>  
 <span data-ttu-id="a793e-158">泛型類型參數可能來自於目前正在檢查的類型、封入類型，或是來自泛型方法。</span><span class="sxs-lookup"><span data-stu-id="a793e-158">A generic type parameter might come from the type you are examining, from an enclosing type, or from a generic method.</span></span> <span data-ttu-id="a793e-159">您可以透過下列方式來判斷泛型類型參數的來源：</span><span class="sxs-lookup"><span data-stu-id="a793e-159">You can determine the source of the generic type parameter as follows:</span></span>  
  
- <span data-ttu-id="a793e-160">首先，使用 <xref:System.Type.DeclaringMethod%2A> 屬性來判斷類型參數是否來自泛型方法。</span><span class="sxs-lookup"><span data-stu-id="a793e-160">First, use the <xref:System.Type.DeclaringMethod%2A> property to determine whether the type parameter comes from a generic method.</span></span> <span data-ttu-id="a793e-161">如果屬性值不是 null 參考 (在 Visual Basic 中為`Nothing` )，則來源為泛型方法。</span><span class="sxs-lookup"><span data-stu-id="a793e-161">If the property value is not a null reference (`Nothing` in Visual Basic), then the source is a generic method.</span></span>  
  
- <span data-ttu-id="a793e-162">如果來源不是泛型方法，請使用 <xref:System.Type.DeclaringType%2A> 屬性來判斷泛型類型參數所屬的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="a793e-162">If the source is not a generic method, use the <xref:System.Type.DeclaringType%2A> property to determine the generic type the generic type parameter belongs to.</span></span>  
  
 <span data-ttu-id="a793e-163">如果類型參數屬於泛型的方法， <xref:System.Type.DeclaringType%2A> 屬性會傳回原先宣告泛型方法但不相關的類型。</span><span class="sxs-lookup"><span data-stu-id="a793e-163">If the type parameter belongs to a generic method, the <xref:System.Type.DeclaringType%2A> property returns the type that declared the generic method, which is irrelevant.</span></span>  
  
### <a name="position-of-a-generic-parameter"></a><span data-ttu-id="a793e-164">泛型參數的位置</span><span class="sxs-lookup"><span data-stu-id="a793e-164">Position of a Generic Parameter</span></span>  
 <span data-ttu-id="a793e-165">在很罕見的情況下，您必須判斷類型參數在類型參數清單中的宣告類別位置。</span><span class="sxs-lookup"><span data-stu-id="a793e-165">In rare situations, it is necessary to determine the position of a type parameter in the type parameter list of its declaring class.</span></span> <span data-ttu-id="a793e-166">例如，假設您有前述範例中代表 <xref:System.Type> 類型的 `B<int, V>` 物件。</span><span class="sxs-lookup"><span data-stu-id="a793e-166">For example, suppose you have a <xref:System.Type> object representing the `B<int, V>` type from the preceding example.</span></span> <span data-ttu-id="a793e-167"><xref:System.Type.GetGenericArguments%2A> 方法提供有類型引數的清單，且在查看 `V` 時，您可以使用 <xref:System.Type.DeclaringMethod%2A> 和 <xref:System.Type.DeclaringType%2A> 屬性以探索其來自何處。</span><span class="sxs-lookup"><span data-stu-id="a793e-167">The <xref:System.Type.GetGenericArguments%2A> method gives you a list of type arguments, and when you examine `V` you can use the <xref:System.Type.DeclaringMethod%2A> and <xref:System.Type.DeclaringType%2A> properties to discover where it comes from.</span></span> <span data-ttu-id="a793e-168">您可以使用 <xref:System.Type.GenericParameterPosition%2A> 屬性來判斷其定義所在之類型參數清單中的位置。</span><span class="sxs-lookup"><span data-stu-id="a793e-168">You can then use the <xref:System.Type.GenericParameterPosition%2A> property to determine its position in the type parameter list where it was defined.</span></span> <span data-ttu-id="a793e-169">在此範例中， `V` 位於其定義所在之類型參數清單中的位置 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="a793e-169">In this example, `V` is at position 0 (zero) in the type parameter list where it was defined.</span></span>  
  
### <a name="base-type-and-interface-constraints"></a><span data-ttu-id="a793e-170">基底類型與介面條件約束</span><span class="sxs-lookup"><span data-stu-id="a793e-170">Base Type and Interface Constraints</span></span>  
 <span data-ttu-id="a793e-171">使用 <xref:System.Type.GetGenericParameterConstraints%2A> 方法，以取得基底類型條件約束與類型參數的介面條件約束。</span><span class="sxs-lookup"><span data-stu-id="a793e-171">Use the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain the base type constraint and interface constraints of a type parameter.</span></span> <span data-ttu-id="a793e-172">陣列元素的順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="a793e-172">The order of the elements of the array is not significant.</span></span> <span data-ttu-id="a793e-173">如果元素是介面類型，則該元素代表介面約束條件。</span><span class="sxs-lookup"><span data-stu-id="a793e-173">An element represents an interface constraint if it is an interface type.</span></span>  
  
### <a name="generic-parameter-attributes"></a><span data-ttu-id="a793e-174">泛型參數屬性</span><span class="sxs-lookup"><span data-stu-id="a793e-174">Generic Parameter Attributes</span></span>  
 <span data-ttu-id="a793e-175"><xref:System.Type.GenericParameterAttributes%2A> 屬性會取得表示變異數 (共變數或反變數) 及類型參數特殊條件約束的 <xref:System.Reflection.GenericParameterAttributes> 值。</span><span class="sxs-lookup"><span data-stu-id="a793e-175">The <xref:System.Type.GenericParameterAttributes%2A> property gets a <xref:System.Reflection.GenericParameterAttributes> value that indicates the variance (covariance or contravariance) and the special constraints of a type parameter.</span></span>  
  
#### <a name="covariance-and-contravariance"></a><span data-ttu-id="a793e-176">共變數和反變數</span><span class="sxs-lookup"><span data-stu-id="a793e-176">Covariance and Contravariance</span></span>  
 <span data-ttu-id="a793e-177">若要判斷類型參數是共變數或是反變數，請套用 <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> 遮罩至由 <xref:System.Reflection.GenericParameterAttributes> 屬性所傳回的 <xref:System.Type.GenericParameterAttributes%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="a793e-177">To determine whether a type parameter is covariant or contravariant, apply the <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> mask to the <xref:System.Reflection.GenericParameterAttributes> value that is returned by the <xref:System.Type.GenericParameterAttributes%2A> property.</span></span> <span data-ttu-id="a793e-178">如果結果為 <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>，則類型參數為非變異值。</span><span class="sxs-lookup"><span data-stu-id="a793e-178">If the result is <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, the type parameter is invariant.</span></span> <span data-ttu-id="a793e-179">請參閱 [共變數和反變數](../../../docs/standard/generics/covariance-and-contravariance.md)。</span><span class="sxs-lookup"><span data-stu-id="a793e-179">See [Covariance and Contravariance](../../../docs/standard/generics/covariance-and-contravariance.md).</span></span>  
  
#### <a name="special-constraints"></a><span data-ttu-id="a793e-180">特殊條件約束</span><span class="sxs-lookup"><span data-stu-id="a793e-180">Special Constraints</span></span>  
 <span data-ttu-id="a793e-181">若要判斷類型參數的特殊條件約束，請套用 <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> 遮罩至 <xref:System.Reflection.GenericParameterAttributes> 屬性所傳回的 <xref:System.Type.GenericParameterAttributes%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="a793e-181">To determine the special constraints of a type parameter, apply the <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> mask to the <xref:System.Reflection.GenericParameterAttributes> value that is returned by the <xref:System.Type.GenericParameterAttributes%2A> property.</span></span> <span data-ttu-id="a793e-182">如果結果是 <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>，則沒有特殊條件約束。</span><span class="sxs-lookup"><span data-stu-id="a793e-182">If the result is <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, there are no special constraints.</span></span> <span data-ttu-id="a793e-183">型別參數可以限制為參考型別、非 Null 實值型別，以及具有無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="a793e-183">A type parameter can be constrained to be a reference type, to be a non-nullable value type, and to have a parameterless constructor.</span></span>  
  
 [<span data-ttu-id="a793e-184">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a793e-184">Back to top</span></span>](#top)  
  
<a name="invariants"></a>   
## <a name="invariants"></a><span data-ttu-id="a793e-185">非變異值</span><span class="sxs-lookup"><span data-stu-id="a793e-185">Invariants</span></span>  
 <span data-ttu-id="a793e-186">若要了解反映中泛型類型非變異條件hapi 一般條款表，請參閱 <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a793e-186">For a table of the invariant conditions for common terms in reflection for generic types, see <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a793e-187">與泛型方法相關的其他條款，請參閱 <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a793e-187">For additional terms relating to generic methods, see <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="a793e-188">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a793e-188">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="a793e-189">相關主題</span><span class="sxs-lookup"><span data-stu-id="a793e-189">Related Topics</span></span>  
  
|<span data-ttu-id="a793e-190">標題</span><span class="sxs-lookup"><span data-stu-id="a793e-190">Title</span></span>|<span data-ttu-id="a793e-191">說明</span><span class="sxs-lookup"><span data-stu-id="a793e-191">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a793e-192">如何：使用反映檢視並具現化泛型型別</span><span class="sxs-lookup"><span data-stu-id="a793e-192">How to: Examine and Instantiate Generic Types with Reflection</span></span>](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)|<span data-ttu-id="a793e-193">示範如何使用 <xref:System.Type> 和 <xref:System.Reflection.MethodInfo> 的屬性及方法，來檢查泛型類型。</span><span class="sxs-lookup"><span data-stu-id="a793e-193">Shows how to use the properties and methods of <xref:System.Type> and <xref:System.Reflection.MethodInfo> to examine generic types.</span></span>|  
|[<span data-ttu-id="a793e-194">泛型</span><span class="sxs-lookup"><span data-stu-id="a793e-194">Generics</span></span>](../../../docs/standard/generics/index.md)|<span data-ttu-id="a793e-195">說明泛型功能，及在 .NET Framework 下如何加以支援。</span><span class="sxs-lookup"><span data-stu-id="a793e-195">Describes the generics feature and how it is supported in the .NET Framework.</span></span>|  
|[<span data-ttu-id="a793e-196">如何：使用反映發出定義泛型型別</span><span class="sxs-lookup"><span data-stu-id="a793e-196">How to: Define a Generic Type with Reflection Emit</span></span>](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|<span data-ttu-id="a793e-197">示範如何在動態組件中使用反映發出以產生泛型類型。</span><span class="sxs-lookup"><span data-stu-id="a793e-197">Shows how to use reflection emit to generate generic types in dynamic assemblies.</span></span>|  
|[<span data-ttu-id="a793e-198">檢視類型資訊</span><span class="sxs-lookup"><span data-stu-id="a793e-198">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|<span data-ttu-id="a793e-199">描述 <xref:System.Type> 類別，並提供程式碼範例以說明如何搭配不同的反映類別來使用 <xref:System.Type>，以取得建構函式、方法、欄位、屬性與事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a793e-199">Describes the <xref:System.Type> class and provides code examples that illustrate how to use <xref:System.Type> with various reflection classes to obtain information about constructors, methods, fields, properties, and events.</span></span>|
