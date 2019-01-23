---
title: 執行階段指示詞 (rd.xml) 組態檔參考
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fed8097c472be487256840f289c1d8252d978a93
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637098"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="ee683-102">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="ee683-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>
<span data-ttu-id="ee683-103">執行階段指示詞 (.rd.xml) 檔案是 XML 組態檔，指定所委任的程式元素是否適用於反映。</span><span class="sxs-lookup"><span data-stu-id="ee683-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="ee683-104">以下是執行階段指示詞檔案的範例：</span><span class="sxs-lookup"><span data-stu-id="ee683-104">Here’s an example of a runtime directives file:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
<Application>  
  <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />  
  <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />  
  
  <Namespace Name="System.Collections.ObjectModel" >  
    <TypeInstantiation Name="ObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />  
    <TypeInstantiation Name="ReadOnlyObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />  
  </Namespace>  
</Application>  
</Directives>  
```  
  
## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="ee683-105">執行階段指示詞檔案的結構</span><span class="sxs-lookup"><span data-stu-id="ee683-105">The structure of a runtime directives file</span></span>  
 <span data-ttu-id="ee683-106">執行階段指示詞檔案使用 `http://schemas.microsoft.com/netfx/2013/01/metadata` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ee683-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>  
  
 <span data-ttu-id="ee683-107">根項目是 [Directives](../../../docs/framework/net-native/directives-element-net-native.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="ee683-107">The root element is the [Directives](../../../docs/framework/net-native/directives-element-net-native.md) element.</span></span> <span data-ttu-id="ee683-108">它可以包含零 (含) 個以上的 [Library](../../../docs/framework/net-native/library-element-net-native.md) 項目，以及零或一個的 [Application](../../../docs/framework/net-native/application-element-net-native.md) 項目，如下列結構所示。</span><span class="sxs-lookup"><span data-stu-id="ee683-108">It can contain zero or more [Library](../../../docs/framework/net-native/library-element-net-native.md) elements, and zero or one [Application](../../../docs/framework/net-native/application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="ee683-109">[Application](../../../docs/framework/net-native/application-element-net-native.md) 項目的屬性可以定義整個應用程式的執行階段反映原則，或是作為子項目的容器。</span><span class="sxs-lookup"><span data-stu-id="ee683-109">The attributes of the [Application](../../../docs/framework/net-native/application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="ee683-110">另一方面，[Library](../../../docs/framework/net-native/library-element-net-native.md) 項目只是容器。</span><span class="sxs-lookup"><span data-stu-id="ee683-110">The [Library](../../../docs/framework/net-native/library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="ee683-111">[Application](../../../docs/framework/net-native/application-element-net-native.md) 和 [Library](../../../docs/framework/net-native/library-element-net-native.md) 項目的子項可定義適用於反映的類型、方法、欄位、屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="ee683-111">The children of the [Application](../../../docs/framework/net-native/application-element-net-native.md) and [Library](../../../docs/framework/net-native/library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>  
  
 <span data-ttu-id="ee683-112">如需參考資訊，請從下列結構中選擇項目，或參閱[執行階段指示詞項目](../../../docs/framework/net-native/runtime-directive-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee683-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](../../../docs/framework/net-native/runtime-directive-elements.md).</span></span> <span data-ttu-id="ee683-113">在下列階層中，省略符號標記了遞迴結構。</span><span class="sxs-lookup"><span data-stu-id="ee683-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="ee683-114">方括號中的資訊指出該元素是選用或必要元素，以及如果使用該元素，可允許多少執行個體 (一個或多個)。</span><span class="sxs-lookup"><span data-stu-id="ee683-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>  
  
 <span data-ttu-id="ee683-115">[Directives](../../../docs/framework/net-native/directives-element-net-native.md) [1:1]</span><span class="sxs-lookup"><span data-stu-id="ee683-115">[Directives](../../../docs/framework/net-native/directives-element-net-native.md) [1:1]</span></span>  
 <span data-ttu-id="ee683-116">[Application](../../../docs/framework/net-native/application-element-net-native.md) [0:1]</span><span class="sxs-lookup"><span data-stu-id="ee683-116">[Application](../../../docs/framework/net-native/application-element-net-native.md) [0:1]</span></span>  
 <span data-ttu-id="ee683-117">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-117">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-118">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-118">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-119">。</span><span class="sxs-lookup"><span data-stu-id="ee683-119">.</span></span> <span data-ttu-id="ee683-120">。</span><span class="sxs-lookup"><span data-stu-id="ee683-120">.</span></span> <span data-ttu-id="ee683-121">。</span><span class="sxs-lookup"><span data-stu-id="ee683-121">.</span></span>  
 <span data-ttu-id="ee683-122">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-122">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-123">。</span><span class="sxs-lookup"><span data-stu-id="ee683-123">.</span></span> <span data-ttu-id="ee683-124">。</span><span class="sxs-lookup"><span data-stu-id="ee683-124">.</span></span> <span data-ttu-id="ee683-125">。</span><span class="sxs-lookup"><span data-stu-id="ee683-125">.</span></span>  
 <span data-ttu-id="ee683-126">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (建構的泛型型別) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-126">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="ee683-127">。</span><span class="sxs-lookup"><span data-stu-id="ee683-127">.</span></span> <span data-ttu-id="ee683-128">。</span><span class="sxs-lookup"><span data-stu-id="ee683-128">.</span></span> <span data-ttu-id="ee683-129">。</span><span class="sxs-lookup"><span data-stu-id="ee683-129">.</span></span>  
 <span data-ttu-id="ee683-130">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-130">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-131">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-131">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-132">。</span><span class="sxs-lookup"><span data-stu-id="ee683-132">.</span></span> <span data-ttu-id="ee683-133">。</span><span class="sxs-lookup"><span data-stu-id="ee683-133">.</span></span> <span data-ttu-id="ee683-134">。</span><span class="sxs-lookup"><span data-stu-id="ee683-134">.</span></span>  
 <span data-ttu-id="ee683-135">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-135">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-136">。</span><span class="sxs-lookup"><span data-stu-id="ee683-136">.</span></span> <span data-ttu-id="ee683-137">。</span><span class="sxs-lookup"><span data-stu-id="ee683-137">.</span></span> <span data-ttu-id="ee683-138">。</span><span class="sxs-lookup"><span data-stu-id="ee683-138">.</span></span>  
 <span data-ttu-id="ee683-139">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (建構的泛型型別) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-139">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="ee683-140">。</span><span class="sxs-lookup"><span data-stu-id="ee683-140">.</span></span> <span data-ttu-id="ee683-141">。</span><span class="sxs-lookup"><span data-stu-id="ee683-141">.</span></span> <span data-ttu-id="ee683-142">。</span><span class="sxs-lookup"><span data-stu-id="ee683-142">.</span></span>  
 <span data-ttu-id="ee683-143">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-143">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-144">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (包含類型的子類別) [O:1]</span><span class="sxs-lookup"><span data-stu-id="ee683-144">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>  
 <span data-ttu-id="ee683-145">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-145">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-146">。</span><span class="sxs-lookup"><span data-stu-id="ee683-146">.</span></span> <span data-ttu-id="ee683-147">。</span><span class="sxs-lookup"><span data-stu-id="ee683-147">.</span></span> <span data-ttu-id="ee683-148">。</span><span class="sxs-lookup"><span data-stu-id="ee683-148">.</span></span>  
 <span data-ttu-id="ee683-149">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (建構的泛型型別) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-149">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="ee683-150">。</span><span class="sxs-lookup"><span data-stu-id="ee683-150">.</span></span> <span data-ttu-id="ee683-151">。</span><span class="sxs-lookup"><span data-stu-id="ee683-151">.</span></span> <span data-ttu-id="ee683-152">。</span><span class="sxs-lookup"><span data-stu-id="ee683-152">.</span></span>  
 <span data-ttu-id="ee683-153">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (包含類型是屬性) [O:1]</span><span class="sxs-lookup"><span data-stu-id="ee683-153">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>  
 <span data-ttu-id="ee683-154">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-154">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-155">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-155">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-156">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-156">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-157">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-157">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-158">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-158">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-159">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (建構的泛型方法) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-159">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="ee683-160">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-160">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-161">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-161">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-162">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-162">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-163">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (建構的泛型型別) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-163">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="ee683-164">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-164">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-165">。</span><span class="sxs-lookup"><span data-stu-id="ee683-165">.</span></span> <span data-ttu-id="ee683-166">。</span><span class="sxs-lookup"><span data-stu-id="ee683-166">.</span></span> <span data-ttu-id="ee683-167">。</span><span class="sxs-lookup"><span data-stu-id="ee683-167">.</span></span>  
 <span data-ttu-id="ee683-168">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (建構的泛型型別) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-168">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="ee683-169">。</span><span class="sxs-lookup"><span data-stu-id="ee683-169">.</span></span> <span data-ttu-id="ee683-170">。</span><span class="sxs-lookup"><span data-stu-id="ee683-170">.</span></span> <span data-ttu-id="ee683-171">。</span><span class="sxs-lookup"><span data-stu-id="ee683-171">.</span></span>  
 <span data-ttu-id="ee683-172">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-172">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-173">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-173">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-174">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-174">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-175">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-175">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-176">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (建構的泛型方法) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-176">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="ee683-177">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-177">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-178">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-178">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-179">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-179">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-180">[Library](../../../docs/framework/net-native/library-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-180">[Library](../../../docs/framework/net-native/library-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-181">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-181">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-182">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-182">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-183">。</span><span class="sxs-lookup"><span data-stu-id="ee683-183">.</span></span> <span data-ttu-id="ee683-184">。</span><span class="sxs-lookup"><span data-stu-id="ee683-184">.</span></span> <span data-ttu-id="ee683-185">。</span><span class="sxs-lookup"><span data-stu-id="ee683-185">.</span></span>  
 <span data-ttu-id="ee683-186">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-186">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-187">。</span><span class="sxs-lookup"><span data-stu-id="ee683-187">.</span></span> <span data-ttu-id="ee683-188">。</span><span class="sxs-lookup"><span data-stu-id="ee683-188">.</span></span> <span data-ttu-id="ee683-189">。</span><span class="sxs-lookup"><span data-stu-id="ee683-189">.</span></span>  
 <span data-ttu-id="ee683-190">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (建構的泛型型別) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-190">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="ee683-191">。</span><span class="sxs-lookup"><span data-stu-id="ee683-191">.</span></span> <span data-ttu-id="ee683-192">。</span><span class="sxs-lookup"><span data-stu-id="ee683-192">.</span></span> <span data-ttu-id="ee683-193">。</span><span class="sxs-lookup"><span data-stu-id="ee683-193">.</span></span>  
 <span data-ttu-id="ee683-194">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-194">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-195">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-195">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-196">。</span><span class="sxs-lookup"><span data-stu-id="ee683-196">.</span></span> <span data-ttu-id="ee683-197">。</span><span class="sxs-lookup"><span data-stu-id="ee683-197">.</span></span> <span data-ttu-id="ee683-198">。</span><span class="sxs-lookup"><span data-stu-id="ee683-198">.</span></span>  
 <span data-ttu-id="ee683-199">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-199">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-200">。</span><span class="sxs-lookup"><span data-stu-id="ee683-200">.</span></span> <span data-ttu-id="ee683-201">。</span><span class="sxs-lookup"><span data-stu-id="ee683-201">.</span></span> <span data-ttu-id="ee683-202">。</span><span class="sxs-lookup"><span data-stu-id="ee683-202">.</span></span>  
 <span data-ttu-id="ee683-203">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (建構的泛型型別) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-203">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="ee683-204">。</span><span class="sxs-lookup"><span data-stu-id="ee683-204">.</span></span> <span data-ttu-id="ee683-205">。</span><span class="sxs-lookup"><span data-stu-id="ee683-205">.</span></span> <span data-ttu-id="ee683-206">。</span><span class="sxs-lookup"><span data-stu-id="ee683-206">.</span></span>  
 <span data-ttu-id="ee683-207">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-207">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-208">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (包含類型的子類別) [O:1]</span><span class="sxs-lookup"><span data-stu-id="ee683-208">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>  
 <span data-ttu-id="ee683-209">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-209">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-210">。</span><span class="sxs-lookup"><span data-stu-id="ee683-210">.</span></span> <span data-ttu-id="ee683-211">。</span><span class="sxs-lookup"><span data-stu-id="ee683-211">.</span></span> <span data-ttu-id="ee683-212">。</span><span class="sxs-lookup"><span data-stu-id="ee683-212">.</span></span>  
 <span data-ttu-id="ee683-213">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (建構的泛型型別) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-213">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="ee683-214">。</span><span class="sxs-lookup"><span data-stu-id="ee683-214">.</span></span> <span data-ttu-id="ee683-215">。</span><span class="sxs-lookup"><span data-stu-id="ee683-215">.</span></span> <span data-ttu-id="ee683-216">。</span><span class="sxs-lookup"><span data-stu-id="ee683-216">.</span></span>  
 <span data-ttu-id="ee683-217">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (包含類型是屬性) [O:1]</span><span class="sxs-lookup"><span data-stu-id="ee683-217">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>  
 <span data-ttu-id="ee683-218">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-218">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-219">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-219">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-220">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (建構的泛型方法) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-220">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="ee683-221">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-221">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-222">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-222">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-223">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-223">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-224">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (建構的泛型型別) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-224">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="ee683-225">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-225">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-226">。</span><span class="sxs-lookup"><span data-stu-id="ee683-226">.</span></span> <span data-ttu-id="ee683-227">。</span><span class="sxs-lookup"><span data-stu-id="ee683-227">.</span></span> <span data-ttu-id="ee683-228">。</span><span class="sxs-lookup"><span data-stu-id="ee683-228">.</span></span>  
 <span data-ttu-id="ee683-229">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (建構的泛型型別) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-229">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="ee683-230">。</span><span class="sxs-lookup"><span data-stu-id="ee683-230">.</span></span> <span data-ttu-id="ee683-231">。</span><span class="sxs-lookup"><span data-stu-id="ee683-231">.</span></span> <span data-ttu-id="ee683-232">。</span><span class="sxs-lookup"><span data-stu-id="ee683-232">.</span></span>  
 <span data-ttu-id="ee683-233">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-233">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-234">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (建構的泛型方法) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-234">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="ee683-235">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-235">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-236">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-236">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="ee683-237">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="ee683-237">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
  
 <span data-ttu-id="ee683-238">[Application](../../../docs/framework/net-native/application-element-net-native.md) 項目可以沒有任何屬性，或者可以有[執行階段指示詞和原則](#Directives)一節中所描述的原則屬性。</span><span class="sxs-lookup"><span data-stu-id="ee683-238">The [Application](../../../docs/framework/net-native/application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>  
  
 <span data-ttu-id="ee683-239">[Library](../../../docs/framework/net-native/library-element-net-native.md) 項目具有單一屬性 `Name`，可指定程式庫或組件的名稱，但不含副檔名。</span><span class="sxs-lookup"><span data-stu-id="ee683-239">A [Library](../../../docs/framework/net-native/library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="ee683-240">例如，下列 [Library](../../../docs/framework/net-native/library-element-net-native.md) 項目套用於名為 Extensions.dll 的組件。</span><span class="sxs-lookup"><span data-stu-id="ee683-240">For example, the following [Library](../../../docs/framework/net-native/library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <!-- Child elements go here -->    
  </Application>  
  <Library Name="Extensions">  
     <!-- Child elements go here -->    
  </Library>  
</Directives>  
```  
  
<a name="Directives"></a>   
## <a name="runtime-directives-and-policy"></a><span data-ttu-id="ee683-241">執行階段指示詞和原則</span><span class="sxs-lookup"><span data-stu-id="ee683-241">Runtime directives and policy</span></span>  
 <span data-ttu-id="ee683-242">[Application](../../../docs/framework/net-native/application-element-net-native.md) 項目本身以及 [Library](../../../docs/framework/net-native/library-element-net-native.md) 和 [Application](../../../docs/framework/net-native/application-element-net-native.md) 項目的子項目表示原則；也就是說，其定義應用程式可以將反映套用於程式項目的方式。</span><span class="sxs-lookup"><span data-stu-id="ee683-242">The [Application](../../../docs/framework/net-native/application-element-net-native.md) element itself and the child elements of the [Library](../../../docs/framework/net-native/library-element-net-native.md) and [Application](../../../docs/framework/net-native/application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="ee683-243">原則類型是由元素的屬性 (例如 `Serialize`) 來定義。</span><span class="sxs-lookup"><span data-stu-id="ee683-243">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="ee683-244">原則值是由屬性的值 (例如 `Serialize="Required"`) 來定義。</span><span class="sxs-lookup"><span data-stu-id="ee683-244">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>  
  
 <span data-ttu-id="ee683-245">元素屬性所指定的任何原則，都會套用至沒有為該原則指定值的所有子元素。</span><span class="sxs-lookup"><span data-stu-id="ee683-245">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="ee683-246">例如，如果以 [Type](../../../docs/framework/net-native/type-element-net-native.md) 項目來指定原則，則該原則會套用至未明確指定原則的所有內含類型和成員。</span><span class="sxs-lookup"><span data-stu-id="ee683-246">For example, if a policy is specified by a [Type](../../../docs/framework/net-native/type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>  
  
 <span data-ttu-id="ee683-247">可以使用 [Application](../../../docs/framework/net-native/application-element-net-native.md)、[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md)、[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md)、[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md)、[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) 和 [Type](../../../docs/framework/net-native/type-element-net-native.md) 項目表示的原則，不同於可以為個別成員表示的原則 (使用 [Method](../../../docs/framework/net-native/method-element-net-native.md)、[Property](../../../docs/framework/net-native/property-element-net-native.md)、[Field](../../../docs/framework/net-native/field-element-net-native.md) 和 [Event](../../../docs/framework/net-native/event-element-net-native.md) 項目)。</span><span class="sxs-lookup"><span data-stu-id="ee683-247">The policy that can be expressed by the [Application](../../../docs/framework/net-native/application-element-net-native.md), [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md), and [Type](../../../docs/framework/net-native/type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](../../../docs/framework/net-native/method-element-net-native.md), [Property](../../../docs/framework/net-native/property-element-net-native.md), [Field](../../../docs/framework/net-native/field-element-net-native.md), and [Event](../../../docs/framework/net-native/event-element-net-native.md) elements).</span></span>  
  
### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="ee683-248">為組件、命名空間和類型指定原則</span><span class="sxs-lookup"><span data-stu-id="ee683-248">Specifying policy for assemblies, namespaces, and types</span></span>  
 <span data-ttu-id="ee683-249">[Application](../../../docs/framework/net-native/application-element-net-native.md)、[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md)、[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md)、[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md)、[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) 和 [Type](../../../docs/framework/net-native/type-element-net-native.md) 項目支援下列原則類型：</span><span class="sxs-lookup"><span data-stu-id="ee683-249">The [Application](../../../docs/framework/net-native/application-element-net-native.md), [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md), and [Type](../../../docs/framework/net-native/type-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="ee683-250">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="ee683-250">`Activate`.</span></span> <span data-ttu-id="ee683-251">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="ee683-251">Controls runtime access to constructors, to enable activation of instances.</span></span>  
  
-   <span data-ttu-id="ee683-252">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="ee683-252">`Browse`.</span></span> <span data-ttu-id="ee683-253">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="ee683-253">Controls querying for information about program elements but does not enable any runtime access.</span></span>  
  
-   <span data-ttu-id="ee683-254">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="ee683-254">`Dynamic`.</span></span> <span data-ttu-id="ee683-255">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="ee683-255">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>  
  
-   <span data-ttu-id="ee683-256">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="ee683-256">`Serialize`.</span></span> <span data-ttu-id="ee683-257">控制對建構函式、欄位和屬性的執行階段存取，讓類型執行個體能夠以 Newtonsoft JSON 序列化程式之類的協力廠商程式庫來序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="ee683-257">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>  
  
-   <span data-ttu-id="ee683-258">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="ee683-258">`DataContractSerializer`.</span></span> <span data-ttu-id="ee683-259">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-259">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="ee683-260">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="ee683-260">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="ee683-261">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-261">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="ee683-262">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="ee683-262">`XmlSerializer`.</span></span> <span data-ttu-id="ee683-263">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-263">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="ee683-264">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="ee683-264">`MarshalObject`.</span></span> <span data-ttu-id="ee683-265">控制將參考類型封送處理至 WinRT 及 COM 的原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-265">Controls policy for marshaling reference types to WinRT and COM.</span></span>  
  
-   <span data-ttu-id="ee683-266">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="ee683-266">`MarshalDelegate`.</span></span> <span data-ttu-id="ee683-267">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-267">Controls policy for marshaling delegate types as function pointers to native code.</span></span>  
  
-   <span data-ttu-id="ee683-268">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="ee683-268">`MarshalStructure` .</span></span> <span data-ttu-id="ee683-269">控制將結構封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-269">Controls policy for marshaling structures to native code.</span></span>  
  
 <span data-ttu-id="ee683-270">與這些原則類型相關聯的設定如下：</span><span class="sxs-lookup"><span data-stu-id="ee683-270">The settings associated with these policy types are:</span></span>  
  
-   <span data-ttu-id="ee683-271">`All`.</span><span class="sxs-lookup"><span data-stu-id="ee683-271">`All`.</span></span> <span data-ttu-id="ee683-272">針對工具鏈未移除的所有類型和成員，啟用原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-272">Enable the policy for all types and members that the tool chain does not remove.</span></span>  
  
-   <span data-ttu-id="ee683-273">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="ee683-273">`Auto`.</span></span> <span data-ttu-id="ee683-274">使用預設行為。</span><span class="sxs-lookup"><span data-stu-id="ee683-274">Use the default behavior.</span></span> <span data-ttu-id="ee683-275">(除非原則被 (例如父元素) 覆寫，否則，不指定原則相當於將該原則設定為 `Auto`。)</span><span class="sxs-lookup"><span data-stu-id="ee683-275">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>  
  
-   <span data-ttu-id="ee683-276">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="ee683-276">`Excluded`.</span></span> <span data-ttu-id="ee683-277">為程式元素停用原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-277">Disable the policy for the program element.</span></span>  
  
-   <span data-ttu-id="ee683-278">`Public`.</span><span class="sxs-lookup"><span data-stu-id="ee683-278">`Public`.</span></span> <span data-ttu-id="ee683-279">為公用類型或成員啟用原則，除非工具鏈判斷該成員是不必要的，並因此將它移除。</span><span class="sxs-lookup"><span data-stu-id="ee683-279">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="ee683-280">(在後者的情況下，您必須使用 `Required Public` 以確保該成員會保留，而且具有反映功能。)</span><span class="sxs-lookup"><span data-stu-id="ee683-280">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>  
  
-   <span data-ttu-id="ee683-281">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="ee683-281">`PublicAndInternal`.</span></span> <span data-ttu-id="ee683-282">如果公用和內部類型或成員沒有被工具鏈移除，則為其啟用原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-282">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>  
  
-   <span data-ttu-id="ee683-283">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="ee683-283">`Required Public`.</span></span> <span data-ttu-id="ee683-284">需要工具鏈保留公用類型和成員 (無論是否使用)，並為其啟用原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-284">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>  
  
-   <span data-ttu-id="ee683-285">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="ee683-285">`Required PublicAndInternal`.</span></span> <span data-ttu-id="ee683-286">需要工具鏈同時保留公用和內部類型和成員 (無論是否使用)，並為其啟用原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-286">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>  
  
-   <span data-ttu-id="ee683-287">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="ee683-287">`Required All`.</span></span> <span data-ttu-id="ee683-288">需要工具鏈保留所有類型和成員 (無論是否使用)，並為其啟用原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-288">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>  
  
 <span data-ttu-id="ee683-289">例如，下列執行階段指示詞檔案會為組件 DataClasses.dll 中的所有類型和成員定義原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-289">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="ee683-290">它會為所有公用屬性 (property) 的序列化啟用反映功能，為所有類型和類型成員啟用瀏覽功能，為所有類型啟用啟動功能 (因為 `Dynamic` 屬性 (attribute))，並為所有公用類型和成員啟用反映功能。</span><span class="sxs-lookup"><span data-stu-id="ee683-290">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"   
                Browse="All" Activate="PublicAndInternal"   
                Dynamic="Public"  />  
   </Application>  
   <Library Name="UtilityLibrary">  
     <!-- Child elements go here -->    
   </Library>  
</Directives>  
```  
  
### <a name="specifying-policy-for-members"></a><span data-ttu-id="ee683-291">為成員指定原則</span><span class="sxs-lookup"><span data-stu-id="ee683-291">Specifying policy for members</span></span>  
 <span data-ttu-id="ee683-292">[Property](../../../docs/framework/net-native/property-element-net-native.md) 和 [Field](../../../docs/framework/net-native/field-element-net-native.md) 項目支援下列原則類型：</span><span class="sxs-lookup"><span data-stu-id="ee683-292">The [Property](../../../docs/framework/net-native/property-element-net-native.md) and [Field](../../../docs/framework/net-native/field-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="ee683-293">`Browse` - 控制對此成員相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="ee683-293">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>  
  
-   <span data-ttu-id="ee683-294">`Dynamic` - 控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="ee683-294">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="ee683-295">另外也會控制對包含類型相關資訊的查詢。</span><span class="sxs-lookup"><span data-stu-id="ee683-295">Also controls querying for information about the containing type.</span></span>  
  
-   <span data-ttu-id="ee683-296">`Serialize` - 控制對成員的執行階段存取，讓類型執行個體能夠以 Newtonsoft JSON 序列化程式之類的程式庫來序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="ee683-296">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="ee683-297">這個原則可以套用至建構函式、欄位和屬性。</span><span class="sxs-lookup"><span data-stu-id="ee683-297">This policy can be applied to constructors, fields, and properties.</span></span>  
  
 <span data-ttu-id="ee683-298">[Method](../../../docs/framework/net-native/method-element-net-native.md) 和 [Event](../../../docs/framework/net-native/event-element-net-native.md) 項目支援下列原則類型：</span><span class="sxs-lookup"><span data-stu-id="ee683-298">The [Method](../../../docs/framework/net-native/method-element-net-native.md) and [Event](../../../docs/framework/net-native/event-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="ee683-299">`Browse` - 控制對此成員相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="ee683-299">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>  
  
-   <span data-ttu-id="ee683-300">`Dynamic` - 控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="ee683-300">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="ee683-301">另外也會控制對包含類型相關資訊的查詢。</span><span class="sxs-lookup"><span data-stu-id="ee683-301">Also controls querying for information about the containing type.</span></span>  
  
 <span data-ttu-id="ee683-302">與這些原則類型相關聯的設定如下：</span><span class="sxs-lookup"><span data-stu-id="ee683-302">The settings associated with these policy types are:</span></span>  
  
-   <span data-ttu-id="ee683-303">`Auto` - 使用預設行為。</span><span class="sxs-lookup"><span data-stu-id="ee683-303">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="ee683-304">(除非原則被覆寫，否則，不指定原則相當於將該原則設定為 `Auto`。）</span><span class="sxs-lookup"><span data-stu-id="ee683-304">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>  
  
-   <span data-ttu-id="ee683-305">`Excluded` - 永不包含成員的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ee683-305">`Excluded` - Never include metadata for the member.</span></span>  
  
-   <span data-ttu-id="ee683-306">`Included` - 如果父類型出現在輸出中，則啟用原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-306">`Included` - Enable the policy if the parent type is present in the output.</span></span>  
  
-   <span data-ttu-id="ee683-307">`Required` - 需要工具鏈保留此成員 (即使看似未使用)，並為其啟用原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-307">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>  
  
## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="ee683-308">執行階段指示詞檔案語意</span><span class="sxs-lookup"><span data-stu-id="ee683-308">Runtime directives file semantics</span></span>  
 <span data-ttu-id="ee683-309">可以將原則同時定義給較高層級和較低層級的元素。</span><span class="sxs-lookup"><span data-stu-id="ee683-309">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="ee683-310">例如，可以將原則定義給組件，以及該組件內含的一些類型。</span><span class="sxs-lookup"><span data-stu-id="ee683-310">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="ee683-311">如果未表示特定較低層級的元素，它會繼承其父元素的原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-311">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="ee683-312">例如，如果 `Assembly` 元素存在，但 `Type` 元素不存在，則 `Assembly` 元素中指定的原則會套用至組件中的每個類型。</span><span class="sxs-lookup"><span data-stu-id="ee683-312">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="ee683-313">多個元素也可以將原則套用至相同的程式元素。</span><span class="sxs-lookup"><span data-stu-id="ee683-313">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="ee683-314">例如，個別的 [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) 項目可能會以不同的方式，為相同的組件定義相同的原則項目。</span><span class="sxs-lookup"><span data-stu-id="ee683-314">For example, separate [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="ee683-315">以下章節將說明在這些情況下，如何解析特定類型的原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-315">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>  
  
 <span data-ttu-id="ee683-316">泛型型別或方法的 [Type](../../../docs/framework/net-native/type-element-net-native.md) 或 [Method](../../../docs/framework/net-native/method-element-net-native.md) 項目，會將其原則套用至沒有自己原則的所有具現化。</span><span class="sxs-lookup"><span data-stu-id="ee683-316">A [Type](../../../docs/framework/net-native/type-element-net-native.md) or [Method](../../../docs/framework/net-native/method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="ee683-317">例如，為 `Type` 指定原則的 <xref:System.Collections.Generic.List%601> 元素，會套用至該泛型類型的所有建構執行個體，除非已針對特定的建構泛型類型 (例如 `List<Int32>`)，以 `TypeInstantiation` 元素將它覆寫，</span><span class="sxs-lookup"><span data-stu-id="ee683-317">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="ee683-318">否則，元素會為所指名的程式元素定義原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-318">Otherwise, elements define policy for the program element named.</span></span>  
  
 <span data-ttu-id="ee683-319">當元素模稜兩可時，引擎會尋找相符項目，如果找到完全相符的項目，就會使用它。</span><span class="sxs-lookup"><span data-stu-id="ee683-319">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="ee683-320">如果找到多個相符項目，則會產生警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="ee683-320">If it finds multiple matches, there will be a warning or error.</span></span>  
  
### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="ee683-321">如果有兩個指示詞將原則套用至相同的程式元素</span><span class="sxs-lookup"><span data-stu-id="ee683-321">If two directives apply policy to the same program element</span></span>  
 <span data-ttu-id="ee683-322">如果不同執行階段指示詞檔案中的兩個元素，嘗試將相同程式元素 (例如組件或類型) 的相同原則類型設定為不同的值，則會以下列方式解決衝突：</span><span class="sxs-lookup"><span data-stu-id="ee683-322">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>  
  
1.  <span data-ttu-id="ee683-323">如果 `Excluded` 元素存在，則以它為優先。</span><span class="sxs-lookup"><span data-stu-id="ee683-323">If the `Excluded` element is present, it has precedence.</span></span>  
  
2.  <span data-ttu-id="ee683-324">`Required` 的優先順序高於非 `Required`。</span><span class="sxs-lookup"><span data-stu-id="ee683-324">`Required` has precedence over not `Required`.</span></span>  
  
3.  <span data-ttu-id="ee683-325">`All` 的優先順序高於 `PublicAndInternal`，而後者的優先順序高於 `Public`。</span><span class="sxs-lookup"><span data-stu-id="ee683-325">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>  
  
4.  <span data-ttu-id="ee683-326">任何明確的設定皆優先於 `Auto`。</span><span class="sxs-lookup"><span data-stu-id="ee683-326">Any explicit setting has precedence over `Auto`.</span></span>  
  
 <span data-ttu-id="ee683-327">例如，如果單一專案包含下列兩個執行階段指示詞檔案，則 DataClasses.dll 的序列化原則會同時設為 `Required Public` 和 `All`。</span><span class="sxs-lookup"><span data-stu-id="ee683-327">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="ee683-328">在此情況下，序列化原則會被解析成 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="ee683-328">In this case, the serialization policy would be resolved as `Required All`.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"/>  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="All" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
 <span data-ttu-id="ee683-329">不過，如果單一執行階段指示詞檔案中的兩個指示詞嘗試為相同的程式元素設定相同的原則類型，則 XML 配置定義工具會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="ee683-329">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>  
  
### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="ee683-330">如果子元素和父元素套用相同的原則類型</span><span class="sxs-lookup"><span data-stu-id="ee683-330">If child and parent elements apply the same policy type</span></span>  
 <span data-ttu-id="ee683-331">子元素會覆寫其父元素，包括 `Excluded` 設定。</span><span class="sxs-lookup"><span data-stu-id="ee683-331">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="ee683-332">覆寫是您會想要指定 `Auto` 的主要原因。</span><span class="sxs-lookup"><span data-stu-id="ee683-332">Overriding is the main reason you would want to specify `Auto`.</span></span>  
  
 <span data-ttu-id="ee683-333">在下列範例中，針對 `DataClasses` 中不在 `DataClasses.ViewModels` 內的所有項目，序列化原則設定為 `Required Public`，而針對不在 `DataClasses` 和 `DataClasses.ViewModels` 內的所有項目，則為 `All`。</span><span class="sxs-lookup"><span data-stu-id="ee683-333">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
   </Appliction>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="ee683-334">如果開放式泛型和具現化的元素套用相同的原則類型</span><span class="sxs-lookup"><span data-stu-id="ee683-334">If open generics and instantiated elements apply the same policy type</span></span>  
 <span data-ttu-id="ee683-335">在下列範例中，當引擎有必須為 `Dictionary<int,int>` 指定 `Browse` 原則的其他理由時，才會為其指派 `Browse` 原則 (否則為預設行為)；<xref:System.Collections.Generic.Dictionary%602> 的每個其他具現化都會使其所有成員可供瀏覽。</span><span class="sxs-lookup"><span data-stu-id="ee683-335">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
      <Namespace Name="DataClasses.Generics" />  
      <Type Name="Dictionary" Browse="All" />  
      <TypeInstantiation Name="Dictionary"   
                         Arguments="System.Int32,System.Int32" Browse="Auto" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="how-policy-is-inferred"></a><span data-ttu-id="ee683-336">推斷原則的方式</span><span class="sxs-lookup"><span data-stu-id="ee683-336">How policy is inferred</span></span>  
 <span data-ttu-id="ee683-337">每個原則類型都有一組不同的規則，用以判斷該原則類型的存在對其他建構有何影響。</span><span class="sxs-lookup"><span data-stu-id="ee683-337">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>  
  
#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="ee683-338">瀏覽原則的效果</span><span class="sxs-lookup"><span data-stu-id="ee683-338">The effect of Browse policy</span></span>  
 <span data-ttu-id="ee683-339">將 `Browse` 原則套用至類型牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="ee683-339">Applying the `Browse` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="ee683-340">類型的基底類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-340">The base type of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-341">如果類型是具現化泛型，則該類型的未具現化版本會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-341">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-342">如果類型是委派，則該類型上的 `Invoke` 方法會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-342">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="ee683-343">類型的每個介面都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-343">Each interface of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-344">套用至類型的每個屬性類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-344">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-345">如果類型是泛型，則每個條件約束類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-345">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-346">如果類型是泛型，則具現化類型之下的類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-346">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="ee683-347">將 `Browse` 原則套用至方法牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="ee683-347">Applying the `Browse` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="ee683-348">方法的每個參數類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-348">Each parameter type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-349">方法的傳回類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-349">The return type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-350">方法的包含類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-350">The containing type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-351">如果方法是具現化泛型方法，則未具現化的泛型方法會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-351">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-352">套用至方法的每個屬性類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-352">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-353">如果方法是泛型，則每個條件約束類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-353">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-354">如果方法是泛型，則具現化方法之下的類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-354">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="ee683-355">將 `Browse` 原則套用至欄位牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="ee683-355">Applying the `Browse` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="ee683-356">套用至欄位的每個屬性類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-356">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-357">欄位的類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-357">The type of the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-358">欄位所屬的類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-358">The type to which the field belongs is marked with the `Browse` policy.</span></span>  
  
#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="ee683-359">動態原則的效果</span><span class="sxs-lookup"><span data-stu-id="ee683-359">The effect of Dynamic policy</span></span>  
 <span data-ttu-id="ee683-360">將 `Dynamic` 原則套用至類型牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="ee683-360">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="ee683-361">類型的基底類型會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-361">The base type of the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="ee683-362">如果類型是具現化泛型，則該類型的未具現化版本會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-362">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="ee683-363">如果類型是委派類型，則該類型上的 `Invoke` 方法會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-363">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="ee683-364">類型的每個介面都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-364">Each interface of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-365">套用至類型的每個屬性類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-365">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-366">如果類型是泛型，則每個條件約束類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-366">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-367">如果類型是泛型，則具現化類型之下的類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-367">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="ee683-368">將 `Dynamic` 原則套用至方法牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="ee683-368">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="ee683-369">方法的每個參數類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-369">Each parameter type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-370">方法的傳回類型會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-370">The return type of the method is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="ee683-371">方法的包含類型會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-371">The containing type of the method is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="ee683-372">如果方法是具現化泛型方法，則未具現化的泛型方法會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-372">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-373">套用至方法的每個屬性類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-373">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-374">如果方法是泛型，則每個條件約束類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-374">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-375">如果方法是泛型，則具現化方法之下的類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-375">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-376">可以藉由 `MethodInfo.Invoke` 來叫用方法，而藉由 <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType> 就能夠進行委派建立。</span><span class="sxs-lookup"><span data-stu-id="ee683-376">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="ee683-377">將 `Dynamic` 原則套用至欄位牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="ee683-377">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="ee683-378">套用至欄位的每個屬性類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-378">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-379">欄位的類型會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-379">The type of the field is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="ee683-380">欄位所屬的類型會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-380">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>  
  
#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="ee683-381">啟動原則的效果</span><span class="sxs-lookup"><span data-stu-id="ee683-381">The effect of Activation policy</span></span>  
 <span data-ttu-id="ee683-382">將啟動原則套用至類型牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="ee683-382">Applying the Activation policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="ee683-383">如果類型是具現化泛型，則該類型的未具現化版本會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-383">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-384">如果類型是委派類型，則該類型上的 `Invoke` 方法會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-384">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="ee683-385">類型的建構函式會標示 `Activation` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-385">Constructors of the type are marked with the `Activation` policy.</span></span>  
  
 <span data-ttu-id="ee683-386">將 `Activation` 原則套用至方法牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="ee683-386">Applying the `Activation` policy to a method involves the following policy change:</span></span>  
  
-   <span data-ttu-id="ee683-387">可以藉由 <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> 和 <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 方法來叫用建構函式。</span><span class="sxs-lookup"><span data-stu-id="ee683-387">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="ee683-388">對於方法，`Activation` 原則只會影響建構函式。</span><span class="sxs-lookup"><span data-stu-id="ee683-388">For methods, the `Activation` policy affects constructors only.</span></span>  
  
 <span data-ttu-id="ee683-389">將 `Activation` 原則套用至欄位並沒有效果。</span><span class="sxs-lookup"><span data-stu-id="ee683-389">Applying the `Activation` policy to a field has no effect.</span></span>  
  
#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="ee683-390">序列化原則的效果</span><span class="sxs-lookup"><span data-stu-id="ee683-390">The effect of Serialize policy</span></span>  
 <span data-ttu-id="ee683-391">`Serialize` 原則可以啟用一般反映型序列化程式。</span><span class="sxs-lookup"><span data-stu-id="ee683-391">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="ee683-392">不過，由於 Microsoft 並不清楚非 Microsoft 序列化程式的確切反映存取模式，所以此原則可能不是全面有效。</span><span class="sxs-lookup"><span data-stu-id="ee683-392">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>  
  
 <span data-ttu-id="ee683-393">將 `Serialize` 原則套用至類型牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="ee683-393">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="ee683-394">類型的基底類型會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-394">The base type of the type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="ee683-395">如果類型是具現化泛型，則該類型的未具現化版本會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-395">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="ee683-396">如果類型是委派類型，則該類型上的 `Invoke` 方法會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-396">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="ee683-397">如果類型是列舉，則類型的陣列會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-397">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="ee683-398">如果類型實作 <xref:System.Collections.Generic.IEnumerable%601>，則 `T` 會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-398">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="ee683-399">如果類型是 <xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.Generic.IList%601>、<xref:System.Collections.Generic.ICollection%601>、<xref:System.Collections.Generic.IReadOnlyCollection%601> 或 <xref:System.Collections.Generic.IReadOnlyList%601>，則 `T[]` 和 <xref:System.Collections.Generic.List%601> 會標示 `Serialize` 原則，但介面類型沒有任何成員會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-399">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="ee683-400">如果類型是 <xref:System.Collections.Generic.List%601>，則沒有任何類型成員會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-400">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="ee683-401">如果類型是 <xref:System.Collections.Generic.IDictionary%602>，則 <xref:System.Collections.Generic.Dictionary%602> 會標示 `Serialize` 原則，</span><span class="sxs-lookup"><span data-stu-id="ee683-401">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="ee683-402">但沒有任何類型成員會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-402">but no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="ee683-403">如果類型是 <xref:System.Collections.Generic.Dictionary%602>，則沒有任何類型成員會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-403">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="ee683-404">如果類型實作 <xref:System.Collections.Generic.IDictionary%602>，則 `TKey` 和 `TValue` 會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-404">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="ee683-405">每個建構函式、每個屬性存取子和每個欄位都會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-405">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>  
  
 <span data-ttu-id="ee683-406">將 `Serialize` 原則套用至方法牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="ee683-406">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="ee683-407">包含類型會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-407">The containing type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="ee683-408">方法的傳回類型會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-408">The return type of the method is marked with the `Serialize` policy.</span></span>  
  
 <span data-ttu-id="ee683-409">將 `Serialize` 原則套用至欄位牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="ee683-409">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="ee683-410">包含類型會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-410">The containing type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="ee683-411">欄位的類型會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="ee683-411">The type of the field is marked with the `Serialize` policy.</span></span>  
  
#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserialier-policies"></a><span data-ttu-id="ee683-412">XmlSerializer、DataContractSerializer 和 DataContractJsonSerialier 原則的效果</span><span class="sxs-lookup"><span data-stu-id="ee683-412">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerialier policies</span></span>  
 <span data-ttu-id="ee683-413">不像 `Serialize` 原則是主要用於反映型序列化程式，`XmlSerializer`、`DataContractSerializer` 和 `DataContractJsonSerializer` 原則是要用來啟用 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈已知的序列化程式集。</span><span class="sxs-lookup"><span data-stu-id="ee683-413">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the `XmlSerializer`, `DataContractSerializer`, and `DataContractJsonSerializer` policies are used to enable a set of serializers that are known to the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain.</span></span> <span data-ttu-id="ee683-414">這些序列化程式不是使用反映來實作，但是可以用類似可反映式類型的方法，來判斷可以在執行階段序列化的類型集。</span><span class="sxs-lookup"><span data-stu-id="ee683-414">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>  
  
 <span data-ttu-id="ee683-415">將這些原則的其中之一套用至類型，可讓該類型以相符的序列化程式來進行序列化。</span><span class="sxs-lookup"><span data-stu-id="ee683-415">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="ee683-416">此外，序列化引擎可以用靜態方式判斷為需要序列化的任何類型，也都可以序列化。</span><span class="sxs-lookup"><span data-stu-id="ee683-416">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>  
  
 <span data-ttu-id="ee683-417">這些原則對方法或欄位沒有任何效果。</span><span class="sxs-lookup"><span data-stu-id="ee683-417">These policies have no effect on methods or fields.</span></span>  
  
 <span data-ttu-id="ee683-418">如需詳細資訊，請參閱[將您的 Windows 市集應用程式移轉至 .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)中的＜序列化程式的差異＞一節。</span><span class="sxs-lookup"><span data-stu-id="ee683-418">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee683-419">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee683-419">See also</span></span>
- [<span data-ttu-id="ee683-420">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="ee683-420">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="ee683-421">反映和 .NET Native</span><span class="sxs-lookup"><span data-stu-id="ee683-421">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)
