---
title: 泛型和反映 (C# 程式設計手冊)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3048cb6a9b333107f6ea37edf31ead96f9fe2057
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="generics-and-reflection-c-programming-guide"></a><span data-ttu-id="be209-102">泛型和反映 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="be209-102">Generics and Reflection (C# Programming Guide)</span></span>
<span data-ttu-id="be209-103">由於 Common Language Runtime (CLR) 可在執行階段存取泛型型別資訊，因此您可以使用反映取得泛型型別的相關資訊，方法和取得非泛型型別的資訊相同。</span><span class="sxs-lookup"><span data-stu-id="be209-103">Because the Common Language Runtime (CLR) has access to generic type information at run time, you can use reflection to obtain information about generic types in the same way as for non-generic types.</span></span> <span data-ttu-id="be209-104">如需詳細資訊，請參閱[執行階段中的泛型](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)。</span><span class="sxs-lookup"><span data-stu-id="be209-104">For more information, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="be209-105">在 [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] 中，<xref:System.Type> 類別已新增幾個新成員，以允許泛型型別的執行階段資訊。</span><span class="sxs-lookup"><span data-stu-id="be209-105">In the [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] several new members are added to the <xref:System.Type> class to enable run-time information for generic types.</span></span> <span data-ttu-id="be209-106">如需使用這些方法和屬性的詳細資訊，請參閱這些類別的文件。</span><span class="sxs-lookup"><span data-stu-id="be209-106">See the documentation on these classes for more information on how to use these methods and properties.</span></span> <span data-ttu-id="be209-107"><xref:System.Reflection.Emit> 命名空間也包含支援泛型的新成員。</span><span class="sxs-lookup"><span data-stu-id="be209-107">The <xref:System.Reflection.Emit> namespace also contains new members that support generics.</span></span> <span data-ttu-id="be209-108">請參閱[如何：使用反映發出定義泛型型別](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)。</span><span class="sxs-lookup"><span data-stu-id="be209-108">See [How to: Define a Generic Type with Reflection Emit](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).</span></span>  
  
 <span data-ttu-id="be209-109">如需泛型反映中所使用之規範的恆成立條件清單，請參閱 <xref:System.Type.IsGenericType%2A> 屬性備註。</span><span class="sxs-lookup"><span data-stu-id="be209-109">For a list of the invariant conditions for terms used in generic reflection, see the <xref:System.Type.IsGenericType%2A> property remarks.</span></span>  
  
|<span data-ttu-id="be209-110">System.Type 成員名稱</span><span class="sxs-lookup"><span data-stu-id="be209-110">System.Type Member Name</span></span>|<span data-ttu-id="be209-111">描述</span><span class="sxs-lookup"><span data-stu-id="be209-111">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|<span data-ttu-id="be209-112">如果類型是泛型，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="be209-112">Returns true if a type is generic.</span></span>|  
|<xref:System.Type.GetGenericArguments%2A>|<span data-ttu-id="be209-113">傳回 `Type` 物件的陣列，代表提供給建構類型的型別引數，或泛型型別定義的型別參數。</span><span class="sxs-lookup"><span data-stu-id="be209-113">Returns an array of `Type` objects that represent the type arguments supplied for a constructed type, or the type parameters of a generic type definition.</span></span>|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|<span data-ttu-id="be209-114">傳回目前建構類型的基礎泛型型別定義。</span><span class="sxs-lookup"><span data-stu-id="be209-114">Returns the underlying generic type definition for the current constructed type.</span></span>|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|<span data-ttu-id="be209-115">傳回由 `Type` 物件組成的陣列，這些物件代表對目前泛型類型參數所設下的條件約束。</span><span class="sxs-lookup"><span data-stu-id="be209-115">Returns an array of `Type` objects that represent the constraints on the current generic type parameter.</span></span>|  
|<xref:System.Type.ContainsGenericParameters%2A>|<span data-ttu-id="be209-116">如果類型或是其封入之任何類型或方法中，包含尚未提供其特定類型的型別參數，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="be209-116">Returns true if the type or any of its enclosing types or methods contain type parameters for which specific types have not been supplied.</span></span>|  
|<xref:System.Type.GenericParameterAttributes%2A>|<span data-ttu-id="be209-117">取得一組 `GenericParameterAttributes` 旗標，描述目前泛型型別參數的特殊條件約束。</span><span class="sxs-lookup"><span data-stu-id="be209-117">Gets a combination of `GenericParameterAttributes` flags that describe the special constraints of the current generic type parameter.</span></span>|  
|<xref:System.Type.GenericParameterPosition%2A>|<span data-ttu-id="be209-118">針對代表型別參數的 `Type` 物件，取得宣告型別參數之泛型型別定義或泛型方法定義中，型別參數清單內的型別參數位置。</span><span class="sxs-lookup"><span data-stu-id="be209-118">For a `Type` object that represents a type parameter, gets the position of the type parameter in the type parameter list of the generic type definition or generic method definition that declared the type parameter.</span></span>|  
|<xref:System.Type.IsGenericParameter%2A>|<span data-ttu-id="be209-119">取得值，指出目前的 `Type` 是否表示泛型型別或方法定義的型別參數。</span><span class="sxs-lookup"><span data-stu-id="be209-119">Gets a value that indicates whether the current `Type` represents a type parameter of a generic type or method definition.</span></span>|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|<span data-ttu-id="be209-120">取得值，指出目前的 <xref:System.Type> 是否代表可用於建構其他泛型型別的泛型型別定義。</span><span class="sxs-lookup"><span data-stu-id="be209-120">Gets a value that indicates whether the current <xref:System.Type> represents a generic type definition, from which other generic types can be constructed.</span></span> <span data-ttu-id="be209-121">如果類型表示泛型型別的定義，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="be209-121">Returns true if the type represents the definition of a generic type.</span></span>|  
|<xref:System.Type.DeclaringMethod%2A>|<span data-ttu-id="be209-122">傳回定義目前泛型型別參數的泛型方法；如果泛型方法未定義型別參數，則為 Null。</span><span class="sxs-lookup"><span data-stu-id="be209-122">Returns the generic method that defined the current generic type parameter, or null if the type parameter was not defined by a generic method.</span></span>|  
|<xref:System.Type.MakeGenericType%2A>|<span data-ttu-id="be209-123">以類型陣列的項目取代目前泛型型別定義的型別參數，並傳回代表所得結果建構類型的 <xref:System.Type> 物件。</span><span class="sxs-lookup"><span data-stu-id="be209-123">Substitutes the elements of an array of types for the type parameters of the current generic type definition, and returns a <xref:System.Type> object representing the resulting constructed type.</span></span>|  
  
 <span data-ttu-id="be209-124">此外，<xref:System.Reflection.MethodInfo> 類別的成員會啟用泛型方法的執行階段資訊。</span><span class="sxs-lookup"><span data-stu-id="be209-124">In addition, members of the <xref:System.Reflection.MethodInfo> class enable run-time information for generic methods.</span></span> <span data-ttu-id="be209-125">如需用來在泛型方法上反映之規範的恆成立條件清單，請參閱 <xref:System.Reflection.MethodBase.IsGenericMethod%2A> 屬性備註。</span><span class="sxs-lookup"><span data-stu-id="be209-125">See the <xref:System.Reflection.MethodBase.IsGenericMethod%2A> property remarks for a list of invariant conditions for terms used to reflect on generic methods.</span></span>  
  
|<span data-ttu-id="be209-126">System.Reflection.MemberInfo 成員名稱</span><span class="sxs-lookup"><span data-stu-id="be209-126">System.Reflection.MemberInfo Member Name</span></span>|<span data-ttu-id="be209-127">描述</span><span class="sxs-lookup"><span data-stu-id="be209-127">Description</span></span>|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodBase.IsGenericMethod%2A>|<span data-ttu-id="be209-128">如果方法是泛型，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="be209-128">Returns true if a method is generic.</span></span>|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|<span data-ttu-id="be209-129">傳回 Type 物件的陣列，這些物件代表所建構泛型方法的型別引數，或泛型方法定義的型別參數。</span><span class="sxs-lookup"><span data-stu-id="be209-129">Returns an array of Type objects that represent the type arguments of a constructed generic method or the type parameters of a generic method definition.</span></span>|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|<span data-ttu-id="be209-130">傳回目前建構方法的基礎泛型方法定義。</span><span class="sxs-lookup"><span data-stu-id="be209-130">Returns the underlying generic method definition for the current constructed method.</span></span>|  
|<xref:System.Reflection.MethodBase.ContainsGenericParameters%2A>|<span data-ttu-id="be209-131">如果方法或是其封入之任何類型中，包含尚未提供其特定類型的任何型別參數，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="be209-131">Returns true if the method or any of its enclosing types contain any type parameters for which specific types have not been supplied.</span></span>|  
|<xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>|<span data-ttu-id="be209-132">如果目前 <xref:System.Reflection.MethodInfo> 代表泛型方法的定義，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="be209-132">Returns true if the current <xref:System.Reflection.MethodInfo> represents the definition of a generic method.</span></span>|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|<span data-ttu-id="be209-133">使用類型陣列的項目取代目前泛型方法定義的類型參數，並傳回代表所產生之建構方法的 <xref:System.Reflection.MethodInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="be209-133">Substitutes the elements of an array of types for the type parameters of the current generic method definition, and returns a <xref:System.Reflection.MethodInfo> object representing the resulting constructed method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be209-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="be209-134">See Also</span></span>  
 [<span data-ttu-id="be209-135">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="be209-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="be209-136">泛型</span><span class="sxs-lookup"><span data-stu-id="be209-136">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="be209-137">反映和泛用類型</span><span class="sxs-lookup"><span data-stu-id="be209-137">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
 [<span data-ttu-id="be209-138">泛型</span><span class="sxs-lookup"><span data-stu-id="be209-138">Generics</span></span>](~/docs/standard/generics/index.md)
