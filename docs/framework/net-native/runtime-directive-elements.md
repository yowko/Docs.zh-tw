---
title: 執行階段指示詞項目
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128176"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="fa5f9-102">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="fa5f9-102">Runtime Directive Elements</span></span>
<span data-ttu-id="fa5f9-103">執行階段指示詞 (rd.xml) 檔案格式支援下列執行階段指示詞元素。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="fa5f9-104">如需階層表示法，請參閱[執行階段指示詞 (rd.xml) 組態檔參考](runtime-directives-rd-xml-configuration-file-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="fa5f9-105">\<Application></span><span class="sxs-lookup"><span data-stu-id="fa5f9-105">\<Application></span></span>](application-element-net-native.md)  
 <span data-ttu-id="fa5f9-106">將執行階段反映原則套用至應用程式使用的所有類型，並做為整個應用程式的類型和類型成員的容器，這些類型和類型成員的中繼資料可在執行階段用於反映。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="fa5f9-107">這是 [\<Directives>](directives-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-107">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="fa5f9-108">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="fa5f9-108">\<Assembly></span></span>](assembly-element-net-native.md)  
 <span data-ttu-id="fa5f9-109">將執行階段原則套用至組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-109">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="fa5f9-110">這是 [\<Application>](application-element-net-native.md) 和 [\<Library>](library-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-110">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="fa5f9-111">\<AttributeImplies></span><span class="sxs-lookup"><span data-stu-id="fa5f9-111">\<AttributeImplies></span></span>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="fa5f9-112">如果其包含 [\<Type>](type-element-net-native.md) 指示詞是屬性，則會將執行階段原則套用至套用該屬性的程式碼項目。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-112">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="fa5f9-113">\<Directives></span><span class="sxs-lookup"><span data-stu-id="fa5f9-113">\<Directives></span></span>](directives-element-net-native.md)  
 <span data-ttu-id="fa5f9-114">.NET Native 的每個執行時間指示詞檔案中的根項目。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-114">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="fa5f9-115">其子項目是 [\<Application>](application-element-net-native.md) 和 [\<Library>](library-element-net-native.md)。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-115">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="fa5f9-116">\<Event></span><span class="sxs-lookup"><span data-stu-id="fa5f9-116">\<Event></span></span>](event-element-net-native.md)  
 <span data-ttu-id="fa5f9-117">將執行階段原則套用至事件。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="fa5f9-118">這是 [\<Type>](type-element-net-native.md) 和 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-118">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="fa5f9-119">\<Field></span><span class="sxs-lookup"><span data-stu-id="fa5f9-119">\<Field></span></span>](field-element-net-native.md)  
 <span data-ttu-id="fa5f9-120">將執行階段原則套用至欄位。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="fa5f9-121">這是 [\<Type>](type-element-net-native.md) 和 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="fa5f9-122">\<GenericParameter></span><span class="sxs-lookup"><span data-stu-id="fa5f9-122">\<GenericParameter></span></span>](genericparameter-element-net-native.md)  
 <span data-ttu-id="fa5f9-123">將執行階段原則套用至泛型類型或方法的參數類型。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="fa5f9-124">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="fa5f9-124">\<ImpliesType></span></span>](impliestype-element-net-native.md)  
 <span data-ttu-id="fa5f9-125">如果執行階段原則已套用至包含類型或方法，則會將該原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="fa5f9-126">\<Library></span><span class="sxs-lookup"><span data-stu-id="fa5f9-126">\<Library></span></span>](library-element-net-native.md)  
 <span data-ttu-id="fa5f9-127">將執行階段原則套用至組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="fa5f9-128">這是 [\<Application>](application-element-net-native.md) 和 [\<Library>](library-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-128">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="fa5f9-129">\<Method></span><span class="sxs-lookup"><span data-stu-id="fa5f9-129">\<Method></span></span>](method-element-net-native.md)  
 <span data-ttu-id="fa5f9-130">將執行階段原則套用至方法。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="fa5f9-131">這是 [\<Type>](type-element-net-native.md) 和 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-131">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="fa5f9-132">\<MethodInstantiation></span><span class="sxs-lookup"><span data-stu-id="fa5f9-132">\<MethodInstantiation></span></span>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="fa5f9-133">將執行階段原則套用至建構的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="fa5f9-134">這是 [\<Type>](type-element-net-native.md) 和 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-134">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="fa5f9-135">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="fa5f9-135">\<Namespace></span></span>](namespace-element-net-native.md)  
 <span data-ttu-id="fa5f9-136">將執行階段原則套用至命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="fa5f9-137">\<Parameter></span><span class="sxs-lookup"><span data-stu-id="fa5f9-137">\<Parameter></span></span>](parameter-element-net-native.md)  
 <span data-ttu-id="fa5f9-138">將執行階段原則套用至傳遞給方法的引數類型。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="fa5f9-139">\<Property></span><span class="sxs-lookup"><span data-stu-id="fa5f9-139">\<Property></span></span>](property-element-net-native.md)  
 <span data-ttu-id="fa5f9-140">將執行階段原則套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="fa5f9-141">這是 [\<Type>](type-element-net-native.md) 和 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 項目的子項。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-141">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="fa5f9-142">\<Subtypes></span><span class="sxs-lookup"><span data-stu-id="fa5f9-142">\<Subtypes></span></span>](subtypes-element-net-native.md)  
 <span data-ttu-id="fa5f9-143">將執行階段原則套用至從包含類型繼承的所有類別。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="fa5f9-144">\<Type></span><span class="sxs-lookup"><span data-stu-id="fa5f9-144">\<Type></span></span>](type-element-net-native.md)  
 <span data-ttu-id="fa5f9-145">將執行階段原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="fa5f9-146">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="fa5f9-146">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="fa5f9-147">將執行階段原則套用至建構的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="fa5f9-148">\<TypeParameter></span><span class="sxs-lookup"><span data-stu-id="fa5f9-148">\<TypeParameter></span></span>](typeparameter-element-net-native.md)  
 <span data-ttu-id="fa5f9-149">將執行階段原則套用至傳遞給方法之 <xref:System.Type> 引數所表示的類型。</span><span class="sxs-lookup"><span data-stu-id="fa5f9-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa5f9-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="fa5f9-150">See also</span></span>

- [<span data-ttu-id="fa5f9-151">rd.xml 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="fa5f9-151">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
