---
title: 執行階段指示詞項目
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf692ff93a575858d1d1a89346611cb9c5957b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61867039"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="1dc7b-102">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="1dc7b-102">Runtime Directive Elements</span></span>
<span data-ttu-id="1dc7b-103">執行階段指示詞 (rd.xml) 檔案格式支援下列執行階段指示詞元素。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="1dc7b-104">如需階層表示法，請參閱[執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-104">See [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="1dc7b-105">\<Application></span><span class="sxs-lookup"><span data-stu-id="1dc7b-105">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)  
 <span data-ttu-id="1dc7b-106">將執行階段反映原則套用至應用程式使用的所有類型，並做為整個應用程式的類型和類型成員的容器，這些類型和類型成員的中繼資料可在執行階段用於反映。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="1dc7b-107">這是 [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-107">This is a child of the [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="1dc7b-108">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="1dc7b-108">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)  
 <span data-ttu-id="1dc7b-109">將執行階段原則套用至組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-109">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="1dc7b-110">這是 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 和 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-110">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1dc7b-111">\<AttributeImplies></span><span class="sxs-lookup"><span data-stu-id="1dc7b-111">\<AttributeImplies></span></span>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 <span data-ttu-id="1dc7b-112">如果其包含 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 指示詞是屬性，則會將執行階段原則套用至套用該屬性的程式碼項目。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-112">If its containing [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="1dc7b-113">\<Directives></span><span class="sxs-lookup"><span data-stu-id="1dc7b-113">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)  
 <span data-ttu-id="1dc7b-114">[!INCLUDE[net_native](../../../includes/net-native-md.md)] 每個執行階段指示詞檔案中的根元素。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-114">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="1dc7b-115">其子項目是 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 和 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md)。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-115">Its child elements are [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="1dc7b-116">\<Event></span><span class="sxs-lookup"><span data-stu-id="1dc7b-116">\<Event></span></span>](../../../docs/framework/net-native/event-element-net-native.md)  
 <span data-ttu-id="1dc7b-117">將執行階段原則套用至事件。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="1dc7b-118">這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-118">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1dc7b-119">\<Field></span><span class="sxs-lookup"><span data-stu-id="1dc7b-119">\<Field></span></span>](../../../docs/framework/net-native/field-element-net-native.md)  
 <span data-ttu-id="1dc7b-120">將執行階段原則套用至欄位。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="1dc7b-121">這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-121">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1dc7b-122">\<GenericParameter></span><span class="sxs-lookup"><span data-stu-id="1dc7b-122">\<GenericParameter></span></span>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 <span data-ttu-id="1dc7b-123">將執行階段原則套用至泛型類型或方法的參數類型。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="1dc7b-124">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="1dc7b-124">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 <span data-ttu-id="1dc7b-125">如果執行階段原則已套用至包含類型或方法，則會將該原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="1dc7b-126">\<程式庫></span><span class="sxs-lookup"><span data-stu-id="1dc7b-126">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)  
 <span data-ttu-id="1dc7b-127">將執行階段原則套用至組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="1dc7b-128">這是 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 和 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-128">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1dc7b-129">\<Method></span><span class="sxs-lookup"><span data-stu-id="1dc7b-129">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 <span data-ttu-id="1dc7b-130">將執行階段原則套用至方法。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="1dc7b-131">這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-131">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1dc7b-132">\<MethodInstantiation></span><span class="sxs-lookup"><span data-stu-id="1dc7b-132">\<MethodInstantiation></span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 <span data-ttu-id="1dc7b-133">將執行階段原則套用至建構的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="1dc7b-134">這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-134">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1dc7b-135">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="1dc7b-135">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 <span data-ttu-id="1dc7b-136">將執行階段原則套用至命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="1dc7b-137">\<Parameter></span><span class="sxs-lookup"><span data-stu-id="1dc7b-137">\<Parameter></span></span>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 <span data-ttu-id="1dc7b-138">將執行階段原則套用至傳遞給方法的引數類型。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="1dc7b-139">\<Property></span><span class="sxs-lookup"><span data-stu-id="1dc7b-139">\<Property></span></span>](../../../docs/framework/net-native/property-element-net-native.md)  
 <span data-ttu-id="1dc7b-140">將執行階段原則套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="1dc7b-141">這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-141">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="1dc7b-142">\<Subtypes></span><span class="sxs-lookup"><span data-stu-id="1dc7b-142">\<Subtypes></span></span>](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 <span data-ttu-id="1dc7b-143">將執行階段原則套用至從包含類型繼承的所有類別。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="1dc7b-144">\<Type></span><span class="sxs-lookup"><span data-stu-id="1dc7b-144">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 <span data-ttu-id="1dc7b-145">將執行階段原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="1dc7b-146">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="1dc7b-146">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 <span data-ttu-id="1dc7b-147">將執行階段原則套用至建構的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="1dc7b-148">\<TypeParameter></span><span class="sxs-lookup"><span data-stu-id="1dc7b-148">\<TypeParameter></span></span>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 <span data-ttu-id="1dc7b-149">將執行階段原則套用至傳遞給方法之 <xref:System.Type> 引數所表示的類型。</span><span class="sxs-lookup"><span data-stu-id="1dc7b-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc7b-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dc7b-150">See also</span></span>

- [<span data-ttu-id="1dc7b-151">rd.xml 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="1dc7b-151">rd.xml Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
