---
title: "執行階段指示詞項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3143c6b78749f3339e7e7195b551b5a5c31fad12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="0a3a8-102">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="0a3a8-102">Runtime Directive Elements</span></span>
<span data-ttu-id="0a3a8-103">執行階段指示詞 (rd.xml) 檔案格式支援下列執行階段指示詞元素。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="0a3a8-104">如需階層表示法，請參閱[執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-104">See [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="0a3a8-105">\<Application></span><span class="sxs-lookup"><span data-stu-id="0a3a8-105">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)  
 <span data-ttu-id="0a3a8-106">將執行階段反映原則套用至應用程式使用的所有類型，並做為整個應用程式的類型和類型成員的容器，這些類型和類型成員的中繼資料可在執行階段用於反映。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="0a3a8-107">這是 [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-107">This is a child of the [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="0a3a8-108">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="0a3a8-108">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)  
 <span data-ttu-id="0a3a8-109">將執行階段原則套用至組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-109">Applies runnntime policy to all the types in an assembly.</span></span> <span data-ttu-id="0a3a8-110">這是 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 和 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-110">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="0a3a8-111">\<AttributeImplies></span><span class="sxs-lookup"><span data-stu-id="0a3a8-111">\<AttributeImplies></span></span>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 <span data-ttu-id="0a3a8-112">如果其包含 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 指示詞是屬性，則會將執行階段原則套用至套用該屬性的程式碼項目。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-112">If its containing [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="0a3a8-113">\<Directives></span><span class="sxs-lookup"><span data-stu-id="0a3a8-113">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)  
 <span data-ttu-id="0a3a8-114">[!INCLUDE[net_native](../../../includes/net-native-md.md)] 每個執行階段指示詞檔案中的根元素。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-114">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="0a3a8-115">其子項目是 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 和 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md)。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-115">Its child elements are [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="0a3a8-116">\<Event></span><span class="sxs-lookup"><span data-stu-id="0a3a8-116">\<Event></span></span>](../../../docs/framework/net-native/event-element-net-native.md)  
 <span data-ttu-id="0a3a8-117">將執行階段原則套用至事件。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="0a3a8-118">這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-118">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="0a3a8-119">\<Field></span><span class="sxs-lookup"><span data-stu-id="0a3a8-119">\<Field></span></span>](../../../docs/framework/net-native/field-element-net-native.md)  
 <span data-ttu-id="0a3a8-120">將執行階段原則套用至欄位。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="0a3a8-121">這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-121">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="0a3a8-122">\<GenericParameter></span><span class="sxs-lookup"><span data-stu-id="0a3a8-122">\<GenericParameter></span></span>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 <span data-ttu-id="0a3a8-123">將執行階段原則套用至泛型類型或方法的參數類型。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="0a3a8-124">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="0a3a8-124">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 <span data-ttu-id="0a3a8-125">如果執行階段原則已套用至包含類型或方法，則會將該原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="0a3a8-126">\<Library></span><span class="sxs-lookup"><span data-stu-id="0a3a8-126">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)  
 <span data-ttu-id="0a3a8-127">將執行階段原則套用至組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="0a3a8-128">這是 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 和 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-128">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="0a3a8-129">\<Method></span><span class="sxs-lookup"><span data-stu-id="0a3a8-129">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 <span data-ttu-id="0a3a8-130">將執行階段原則套用至方法。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="0a3a8-131">這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-131">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="0a3a8-132">\<MethodInstantiation></span><span class="sxs-lookup"><span data-stu-id="0a3a8-132">\<MethodInstantiation></span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 <span data-ttu-id="0a3a8-133">將執行階段原則套用至建構的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="0a3a8-134">這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-134">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="0a3a8-135">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="0a3a8-135">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 <span data-ttu-id="0a3a8-136">將執行階段原則套用至命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="0a3a8-137">\<Parameter></span><span class="sxs-lookup"><span data-stu-id="0a3a8-137">\<Parameter></span></span>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 <span data-ttu-id="0a3a8-138">將執行階段原則套用至傳遞給方法的引數類型。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="0a3a8-139">\<Property></span><span class="sxs-lookup"><span data-stu-id="0a3a8-139">\<Property></span></span>](../../../docs/framework/net-native/property-element-net-native.md)  
 <span data-ttu-id="0a3a8-140">將執行階段原則套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="0a3a8-141">這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-141">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="0a3a8-142">\<Subtypes></span><span class="sxs-lookup"><span data-stu-id="0a3a8-142">\<Subtypes></span></span>](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 <span data-ttu-id="0a3a8-143">將執行階段原則套用至從包含類型繼承的所有類別。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="0a3a8-144">\<Type></span><span class="sxs-lookup"><span data-stu-id="0a3a8-144">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 <span data-ttu-id="0a3a8-145">將執行階段原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="0a3a8-146">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="0a3a8-146">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 <span data-ttu-id="0a3a8-147">將執行階段原則套用至建構的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="0a3a8-148">\<TypeParameter></span><span class="sxs-lookup"><span data-stu-id="0a3a8-148">\<TypeParameter></span></span>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 <span data-ttu-id="0a3a8-149">將執行階段原則套用至傳遞給方法之 <xref:System.Type> 引數所表示的類型。</span><span class="sxs-lookup"><span data-stu-id="0a3a8-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a3a8-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a3a8-150">See Also</span></span>  
 [<span data-ttu-id="0a3a8-151">rd.xml 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="0a3a8-151">rd.xml Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
