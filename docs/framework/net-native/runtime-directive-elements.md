---
title: 執行階段指示詞項目
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: 96bce89c02ad17d1b30eda66237f69a15123dcd3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250797"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="139d4-102">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="139d4-102">Runtime Directive Elements</span></span>

<span data-ttu-id="139d4-103">執行階段指示詞 (rd.xml) 檔案格式支援下列執行階段指示詞元素。</span><span class="sxs-lookup"><span data-stu-id="139d4-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="139d4-104">如需階層表示法，請參閱[執行階段指示詞 (rd.xml) 組態檔參考](runtime-directives-rd-xml-configuration-file-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="139d4-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [\<Application>](application-element-net-native.md)  
 <span data-ttu-id="139d4-105">將執行階段反映原則套用至應用程式使用的所有類型，並做為整個應用程式的類型和類型成員的容器，這些類型和類型成員的中繼資料可在執行階段用於反映。</span><span class="sxs-lookup"><span data-stu-id="139d4-105">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="139d4-106">這是元素的子系 [\<Directives>](directives-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="139d4-106">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [\<Assembly>](assembly-element-net-native.md)  
 <span data-ttu-id="139d4-107">將執行階段原則套用至組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="139d4-107">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="139d4-108">這是和元素的子 [\<Application>](application-element-net-native.md) 系 [\<Library>](library-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="139d4-108">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="139d4-109">如果其包含 [\<Type>](type-element-net-native.md) 的指示詞是屬性，則會將執行時間原則套用至套用該屬性的程式碼專案。</span><span class="sxs-lookup"><span data-stu-id="139d4-109">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [\<Directives>](directives-element-net-native.md)  
 <span data-ttu-id="139d4-110">.NET Native 的每個執行時間指示詞檔案中的根項目。</span><span class="sxs-lookup"><span data-stu-id="139d4-110">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="139d4-111">其子項目為 [\<Application>](application-element-net-native.md) 和 [\<Library>](library-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="139d4-111">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [\<Event>](event-element-net-native.md)  
 <span data-ttu-id="139d4-112">將執行階段原則套用至事件。</span><span class="sxs-lookup"><span data-stu-id="139d4-112">Applies runtime policy to an event.</span></span> <span data-ttu-id="139d4-113">這是和元素的子 [\<Type>](type-element-net-native.md) 系 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="139d4-113">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Field>](field-element-net-native.md)  
 <span data-ttu-id="139d4-114">將執行階段原則套用至欄位。</span><span class="sxs-lookup"><span data-stu-id="139d4-114">Applies runtime policy to a field.</span></span> <span data-ttu-id="139d4-115">這是和元素的子 [\<Type>](type-element-net-native.md) 系 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="139d4-115">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 <span data-ttu-id="139d4-116">將執行階段原則套用至泛型類型或方法的參數類型。</span><span class="sxs-lookup"><span data-stu-id="139d4-116">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 <span data-ttu-id="139d4-117">如果執行階段原則已套用至包含類型或方法，則會將該原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="139d4-117">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [\<Library>](library-element-net-native.md)  
 <span data-ttu-id="139d4-118">將執行階段原則套用至組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="139d4-118">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="139d4-119">這是和元素的子 [\<Application>](application-element-net-native.md) 系 [\<Library>](library-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="139d4-119">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<Method>](method-element-net-native.md)  
 <span data-ttu-id="139d4-120">將執行階段原則套用至方法。</span><span class="sxs-lookup"><span data-stu-id="139d4-120">Applies runtime policy to a method.</span></span> <span data-ttu-id="139d4-121">這是和元素的子 [\<Type>](type-element-net-native.md) 系 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="139d4-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="139d4-122">將執行階段原則套用至建構的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="139d4-122">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="139d4-123">這是和元素的子 [\<Type>](type-element-net-native.md) 系 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="139d4-123">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Namespace>](namespace-element-net-native.md)  
 <span data-ttu-id="139d4-124">將執行階段原則套用至命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="139d4-124">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [\<Parameter>](parameter-element-net-native.md)  
 <span data-ttu-id="139d4-125">將執行階段原則套用至傳遞給方法的引數類型。</span><span class="sxs-lookup"><span data-stu-id="139d4-125">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [\<Property>](property-element-net-native.md)  
 <span data-ttu-id="139d4-126">將執行階段原則套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="139d4-126">Applies runtime policy to a property.</span></span> <span data-ttu-id="139d4-127">這是和元素的子 [\<Type>](type-element-net-native.md) 系 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="139d4-127">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 <span data-ttu-id="139d4-128">將執行階段原則套用至從包含類型繼承的所有類別。</span><span class="sxs-lookup"><span data-stu-id="139d4-128">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [\<Type>](type-element-net-native.md)  
 <span data-ttu-id="139d4-129">將執行階段原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="139d4-129">Applies runtime policy to a type.</span></span>  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="139d4-130">將執行階段原則套用至建構的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="139d4-130">Applies runtime policy to a constructed generic type.</span></span>  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 <span data-ttu-id="139d4-131">將執行階段原則套用至傳遞給方法之 <xref:System.Type> 引數所表示的類型。</span><span class="sxs-lookup"><span data-stu-id="139d4-131">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="139d4-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="139d4-132">See also</span></span>

- [<span data-ttu-id="139d4-133">rd.xml 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="139d4-133">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
