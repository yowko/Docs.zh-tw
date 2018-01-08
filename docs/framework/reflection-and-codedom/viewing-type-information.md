---
title: "檢視類型資訊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- types, viewing type information
- Type object
- viewing type information
- reflection, viewing type information
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2b31c029eb18943c926dfd5ed5b0576e866067d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="viewing-type-information"></a><span data-ttu-id="615c5-102">檢視類型資訊</span><span class="sxs-lookup"><span data-stu-id="615c5-102">Viewing Type Information</span></span>
<span data-ttu-id="615c5-103"><xref:System.Type?displayProperty=nameWithType> 類別是反映的核心。</span><span class="sxs-lookup"><span data-stu-id="615c5-103">The <xref:System.Type?displayProperty=nameWithType> class is central to reflection.</span></span> <span data-ttu-id="615c5-104">Common Language Runtime 會在反映提出要求時，建立載入類型的**類型**。</span><span class="sxs-lookup"><span data-stu-id="615c5-104">The common language runtime creates the **Type** for a loaded type when reflection requests it.</span></span> <span data-ttu-id="615c5-105">您可以使用**類型**物件的方法、欄位、屬性和巢狀類別，找出有關該類型的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="615c5-105">You can use a **Type** object's methods, fields, properties, and nested classes to find out everything about that type.</span></span>  
  
 <span data-ttu-id="615c5-106">使用 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> 或 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>，從尚未載入、但以類型名稱或您想要的類型名稱傳遞的組件中，取得**類型**物件。</span><span class="sxs-lookup"><span data-stu-id="615c5-106">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> to obtain **Type** objects from assemblies that have not been loaded, passing in the name of the type or types you want.</span></span> <span data-ttu-id="615c5-107">使用<xref:System.Type.GetType%2A?displayProperty=nameWithType>取得**類型**已載入的組件的物件。</span><span class="sxs-lookup"><span data-stu-id="615c5-107">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> to get the **Type** objects from an assembly that is already loaded.</span></span> <span data-ttu-id="615c5-108">使用 <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> 和 <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> 取得模組**類型**物件。</span><span class="sxs-lookup"><span data-stu-id="615c5-108">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> and <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> to obtain module **Type** objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="615c5-109">如果您想要檢查和操作泛型型別和方法，請參閱[反映和泛用型別](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)提供的其他資訊，以及[如何：使用反映檢查和具現化泛型型別](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="615c5-109">If you want to examine and manipulate generic types and methods, please see the additional information provided in [Reflection and Generic Types](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) and [How to: Examine and Instantiate Generic Types with Reflection](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="615c5-110">下例示範為組件取得 <xref:System.Reflection.Assembly> 物件和模組的必要語法。</span><span class="sxs-lookup"><span data-stu-id="615c5-110">The following example shows the syntax necessary to get the <xref:System.Reflection.Assembly> object and module for an assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 <span data-ttu-id="615c5-111">下例示範從載入的組件中取得**類型**物件。</span><span class="sxs-lookup"><span data-stu-id="615c5-111">The following example demonstrates getting **Type** objects from a loaded assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 <span data-ttu-id="615c5-112">一旦取得**類型**，就有許多方式可以探索該類型成員的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="615c5-112">Once you obtain a **Type**, there are many ways you can discover information about the members of that type.</span></span> <span data-ttu-id="615c5-113">例如，您可以呼叫 <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> 方法找出類型的所有成員，它會取得 <xref:System.Reflection.MemberInfo> 物件的陣列，描述目前類型的每一個成員。</span><span class="sxs-lookup"><span data-stu-id="615c5-113">For example, you can find out about all the type's members by calling the <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> method, which obtains an array of <xref:System.Reflection.MemberInfo> objects describing each of the members of the current type.</span></span>  
  
 <span data-ttu-id="615c5-114">您也可以對**類型**類別使用方法，擷取按名稱指定的一或多個建構函式、方法、事件、欄位或屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="615c5-114">You can also use methods on the **Type** class to retrieve information about one or more constructors, methods, events, fields, or properties that you specify by name.</span></span> <span data-ttu-id="615c5-115">例如，<xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> 會封裝目前類別的特定建構函式。</span><span class="sxs-lookup"><span data-stu-id="615c5-115">For example, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsulates a specific constructor of the current class.</span></span>  
  
 <span data-ttu-id="615c5-116">如果您有**類型**，您可以使用 <xref:System.Type.Module%2A?displayProperty=nameWithType> 屬性，取得封裝模組的物件，而此模組包含該類型。</span><span class="sxs-lookup"><span data-stu-id="615c5-116">If you have a **Type**, you can use the <xref:System.Type.Module%2A?displayProperty=nameWithType> property to obtain an object that encapsulates the module containing that type.</span></span> <span data-ttu-id="615c5-117">使用 <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> 屬性找出封裝組件的物件，而此組件包含模組。</span><span class="sxs-lookup"><span data-stu-id="615c5-117">Use the <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> property to locate an object that encapsulates the assembly containing the module.</span></span> <span data-ttu-id="615c5-118">您可以使用 <xref:System.Type.Assembly%2A?displayProperty=nameWithType> 屬性直接取得封裝類型的組件。</span><span class="sxs-lookup"><span data-stu-id="615c5-118">You can obtain the assembly that encapsulates the type directly by using the <xref:System.Type.Assembly%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="systemtype-and-constructorinfo"></a><span data-ttu-id="615c5-119">System.Type 和 ConstructorInfo</span><span class="sxs-lookup"><span data-stu-id="615c5-119">System.Type and ConstructorInfo</span></span>  
 <span data-ttu-id="615c5-120">下例示範如何列出類別的建構函式，本例中為 <xref:System.String> 類別。</span><span class="sxs-lookup"><span data-stu-id="615c5-120">The following example shows how to list the constructors for a class, in this case, the <xref:System.String> class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a><span data-ttu-id="615c5-121">MemberInfo、MethodInfo、FieldInfo 和 PropertyInfo</span><span class="sxs-lookup"><span data-stu-id="615c5-121">MemberInfo, MethodInfo, FieldInfo, and PropertyInfo</span></span>  
 <span data-ttu-id="615c5-122">使用 <xref:System.Reflection.MemberInfo>、<xref:System.Reflection.MethodInfo>、<xref:System.Reflection.FieldInfo> 或 <xref:System.Reflection.PropertyInfo> 物件，取得類型方法、屬性、事件和欄位的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="615c5-122">Obtain information about the type's methods, properties, events, and fields using <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, or <xref:System.Reflection.PropertyInfo> objects.</span></span>  
  
 <span data-ttu-id="615c5-123">下例使用 **MemberInfo** 列出 **System.IO.File** 類別中的成員數目，並使用 <xref:System.Type.IsPublic%2A> 屬性判斷類別的可見度。</span><span class="sxs-lookup"><span data-stu-id="615c5-123">The following example uses **MemberInfo** to list the number of members in the **System.IO.File** class and uses the <xref:System.Type.IsPublic%2A> property to determine the visibility of the class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 <span data-ttu-id="615c5-124">下例會檢查指定的成員類型。</span><span class="sxs-lookup"><span data-stu-id="615c5-124">The following example investigates the type of the specified member.</span></span> <span data-ttu-id="615c5-125">它會對 **MemberInfo** 類別的成員執行反映，列出其類型。</span><span class="sxs-lookup"><span data-stu-id="615c5-125">It performs reflection on a member of the **MemberInfo** class, and lists its type.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 <span data-ttu-id="615c5-126">下例使用所有反映 **\*Info** 類別與 <xref:System.Reflection.BindingFlags> 列出指定類別的所有成員 (建構函式、欄位、屬性、事件和方法)，將成員區分為靜態和執行個體類別。</span><span class="sxs-lookup"><span data-stu-id="615c5-126">The following example uses all the Reflection **\*Info** classes along with <xref:System.Reflection.BindingFlags> to list all the members (constructors, fields, properties, events, and methods) of the specified class, dividing the members into static and instance categories.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="615c5-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="615c5-127">See Also</span></span>  
 <xref:System.Reflection.BindingFlags>  
 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetFields%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.MemberInfo>  
 <xref:System.Reflection.ConstructorInfo>  
 <xref:System.Reflection.MethodInfo>  
 <xref:System.Reflection.FieldInfo>  
 <xref:System.Reflection.EventInfo>  
 <xref:System.Reflection.ParameterInfo>  
 [<span data-ttu-id="615c5-128">反映和泛用類型</span><span class="sxs-lookup"><span data-stu-id="615c5-128">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
