---
title: 執行階段指示詞 (rd.xml) 組態檔參考
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: adfc0ae6d9bdae333daacee525c7775acd5a8029
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049144"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="d3f18-102">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="d3f18-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="d3f18-103">執行階段指示詞 (.rd.xml) 檔案是 XML 組態檔，指定所委任的程式元素是否適用於反映。</span><span class="sxs-lookup"><span data-stu-id="d3f18-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="d3f18-104">以下是執行階段指示詞檔案的範例：</span><span class="sxs-lookup"><span data-stu-id="d3f18-104">Here’s an example of a runtime directives file:</span></span>

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

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="d3f18-105">執行階段指示詞檔案的結構</span><span class="sxs-lookup"><span data-stu-id="d3f18-105">The structure of a runtime directives file</span></span>

<span data-ttu-id="d3f18-106">執行階段指示詞檔案使用 `http://schemas.microsoft.com/netfx/2013/01/metadata` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="d3f18-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="d3f18-107">根項目是 [Directives](directives-element-net-native.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="d3f18-107">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="d3f18-108">它可以包含零 (含) 個以上的 [Library](library-element-net-native.md) 項目，以及零或一個的 [Application](application-element-net-native.md) 項目，如下列結構所示。</span><span class="sxs-lookup"><span data-stu-id="d3f18-108">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="d3f18-109">[Application](application-element-net-native.md) 項目的屬性可以定義整個應用程式的執行階段反映原則，或是作為子項目的容器。</span><span class="sxs-lookup"><span data-stu-id="d3f18-109">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="d3f18-110">另一方面，[Library](library-element-net-native.md) 項目只是容器。</span><span class="sxs-lookup"><span data-stu-id="d3f18-110">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="d3f18-111">[Application](application-element-net-native.md) 和 [Library](library-element-net-native.md) 項目的子項可定義適用於反映的類型、方法、欄位、屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="d3f18-111">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="d3f18-112">如需參考資訊，請從下列結構中選擇項目，或參閱[執行階段指示詞項目](runtime-directive-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f18-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="d3f18-113">在下列階層中，省略符號標記了遞迴結構。</span><span class="sxs-lookup"><span data-stu-id="d3f18-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="d3f18-114">方括號中的資訊指出該元素是選用或必要元素，以及如果使用該元素，可允許多少執行個體 (一個或多個)。</span><span class="sxs-lookup"><span data-stu-id="d3f18-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

<span data-ttu-id="d3f18-115">[指示詞](directives-element-net-native.md)[1:1][應用程式](application-element-net-native.md)[0:1][元件](assembly-element-net-native.md)[0： M] [Namespace](namespace-element-net-native.md) [0： m]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-115">[Directives](directives-element-net-native.md) [1:1] [Application](application-element-net-native.md) [0:1] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="d3f18-116">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-116">.</span></span> <span data-ttu-id="d3f18-117">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-117">.</span></span>
<span data-ttu-id="d3f18-118">[類型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-118">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="d3f18-119">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-119">.</span></span> <span data-ttu-id="d3f18-120">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-120">.</span></span>
<span data-ttu-id="d3f18-121">[TypeInstantiation](typeinstantiation-element-net-native.md)（結構化的泛型型別）[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-121">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="d3f18-122">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-122">.</span></span> <span data-ttu-id="d3f18-123">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-123">.</span></span>
<span data-ttu-id="d3f18-124">[命名空間](namespace-element-net-native.md)[0： M][命名空間](namespace-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-124">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="d3f18-125">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-125">.</span></span> <span data-ttu-id="d3f18-126">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-126">.</span></span>
<span data-ttu-id="d3f18-127">[類型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-127">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="d3f18-128">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-128">.</span></span> <span data-ttu-id="d3f18-129">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-129">.</span></span>
<span data-ttu-id="d3f18-130">[TypeInstantiation](typeinstantiation-element-net-native.md)（結構化的泛型型別）[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-130">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="d3f18-131">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-131">.</span></span> <span data-ttu-id="d3f18-132">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-132">.</span></span>
<span data-ttu-id="d3f18-133">[類型](type-element-net-native.md)[0： M][子類型](subtypes-element-net-native.md)（包含類型的子類別）O：1[類型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-133">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="d3f18-134">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-134">.</span></span> <span data-ttu-id="d3f18-135">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-135">.</span></span>
<span data-ttu-id="d3f18-136">[TypeInstantiation](typeinstantiation-element-net-native.md)（結構化的泛型型別）[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-136">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="d3f18-137">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-137">.</span></span> <span data-ttu-id="d3f18-138">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-138">.</span></span>
<span data-ttu-id="d3f18-139">[AttributeImplies](attributeimplies-element-net-native.md)（包含類型是屬性）O：1[GenericParameter](genericparameter-element-net-native.md)[0： M][方法](method-element-net-native.md)[0： M][參數](parameter-element-net-native.md)[0： M][TypeParameter](typeparameter-element-net-native.md)[0： M][GenericParameter](genericparameter-element-net-native.md)[0： M][MethodInstantiation](methodinstantiation-element-net-native.md)（已結構化的泛型方法）[0： M][屬性](property-element-net-native.md)[0： M][欄位](field-element-net-native.md)[0： M][事件](event-element-net-native.md)[0： M][TypeInstantiation](typeinstantiation-element-net-native.md)（結構化的泛型型別）[0： M][類型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-139">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="d3f18-140">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-140">.</span></span> <span data-ttu-id="d3f18-141">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-141">.</span></span>
<span data-ttu-id="d3f18-142">[TypeInstantiation](typeinstantiation-element-net-native.md)（結構化的泛型型別）[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="d3f18-143">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-143">.</span></span> <span data-ttu-id="d3f18-144">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-144">.</span></span>
<span data-ttu-id="d3f18-145">[方法](method-element-net-native.md)[0： M][參數](parameter-element-net-native.md)[0： M][TypeParameter](typeparameter-element-net-native.md)[0： M][GenericParameter](genericparameter-element-net-native.md)[0： M][MethodInstantiation](methodinstantiation-element-net-native.md)（已結構化的泛型方法）[0： M][屬性](property-element-net-native.md)[0： M][欄位](field-element-net-native.md)[0： M][事件](event-element-net-native.md)[0： M]連結[庫](library-element-net-native.md)[0： M][元件](assembly-element-net-native.md)[0： M][命名空間](namespace-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-145">[Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [Library](library-element-net-native.md) [0:M] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="d3f18-146">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-146">.</span></span> <span data-ttu-id="d3f18-147">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-147">.</span></span>
<span data-ttu-id="d3f18-148">[類型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-148">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="d3f18-149">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-149">.</span></span> <span data-ttu-id="d3f18-150">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-150">.</span></span>
<span data-ttu-id="d3f18-151">[TypeInstantiation](typeinstantiation-element-net-native.md)（結構化的泛型型別）[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-151">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="d3f18-152">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-152">.</span></span> <span data-ttu-id="d3f18-153">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-153">.</span></span>
<span data-ttu-id="d3f18-154">[命名空間](namespace-element-net-native.md)[0： M][命名空間](namespace-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-154">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="d3f18-155">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-155">.</span></span> <span data-ttu-id="d3f18-156">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-156">.</span></span>
<span data-ttu-id="d3f18-157">[類型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-157">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="d3f18-158">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-158">.</span></span> <span data-ttu-id="d3f18-159">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-159">.</span></span>
<span data-ttu-id="d3f18-160">[TypeInstantiation](typeinstantiation-element-net-native.md)（結構化的泛型型別）[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-160">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="d3f18-161">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-161">.</span></span> <span data-ttu-id="d3f18-162">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-162">.</span></span>
<span data-ttu-id="d3f18-163">[類型](type-element-net-native.md)[0： M][子類型](subtypes-element-net-native.md)（包含類型的子類別）O：1[類型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-163">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="d3f18-164">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-164">.</span></span> <span data-ttu-id="d3f18-165">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-165">.</span></span>
<span data-ttu-id="d3f18-166">[TypeInstantiation](typeinstantiation-element-net-native.md)（結構化的泛型型別）[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-166">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="d3f18-167">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-167">.</span></span> <span data-ttu-id="d3f18-168">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-168">.</span></span>
<span data-ttu-id="d3f18-169">[AttributeImplies](attributeimplies-element-net-native.md)（包含類型是屬性）O：1[GenericParameter](genericparameter-element-net-native.md)[0： M][方法](method-element-net-native.md)[0： M][MethodInstantiation](methodinstantiation-element-net-native.md)（已結構化的泛型方法）[0： M][屬性](property-element-net-native.md)[0： M][欄位](field-element-net-native.md)[0： M][事件](event-element-net-native.md)[0： M][TypeInstantiation](typeinstantiation-element-net-native.md)（結構化的泛型型別）[0： M][類型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-169">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="d3f18-170">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-170">.</span></span> <span data-ttu-id="d3f18-171">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-171">.</span></span>
<span data-ttu-id="d3f18-172">[TypeInstantiation](typeinstantiation-element-net-native.md)（結構化的泛型型別）[0： M]。</span><span class="sxs-lookup"><span data-stu-id="d3f18-172">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="d3f18-173">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-173">.</span></span> <span data-ttu-id="d3f18-174">.</span><span class="sxs-lookup"><span data-stu-id="d3f18-174">.</span></span>
<span data-ttu-id="d3f18-175">[方法](method-element-net-native.md)[0： M][MethodInstantiation](methodinstantiation-element-net-native.md)（已結構化的泛型方法）[0： M][屬性](property-element-net-native.md)[0： M][欄位](field-element-net-native.md)[0： M][事件](event-element-net-native.md)[0： M]</span><span class="sxs-lookup"><span data-stu-id="d3f18-175">[Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="d3f18-176">[Application](application-element-net-native.md) 項目可以沒有任何屬性，或者可以有[執行階段指示詞和原則](#Directives)一節中所描述的原則屬性。</span><span class="sxs-lookup"><span data-stu-id="d3f18-176">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="d3f18-177">[Library](library-element-net-native.md) 項目具有單一屬性 `Name`，可指定程式庫或組件的名稱，但不含副檔名。</span><span class="sxs-lookup"><span data-stu-id="d3f18-177">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="d3f18-178">例如，下列 [Library](library-element-net-native.md) 項目套用於名為 Extensions.dll 的組件。</span><span class="sxs-lookup"><span data-stu-id="d3f18-178">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

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

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="d3f18-179">執行階段指示詞和原則</span><span class="sxs-lookup"><span data-stu-id="d3f18-179">Runtime directives and policy</span></span>

<span data-ttu-id="d3f18-180">[Application](application-element-net-native.md) 項目本身以及 [Library](library-element-net-native.md) 和 [Application](application-element-net-native.md) 項目的子項目表示原則；也就是說，其定義應用程式可以將反映套用於程式項目的方式。</span><span class="sxs-lookup"><span data-stu-id="d3f18-180">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="d3f18-181">原則類型是由元素的屬性 (例如 `Serialize`) 來定義。</span><span class="sxs-lookup"><span data-stu-id="d3f18-181">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="d3f18-182">原則值是由屬性的值 (例如 `Serialize="Required"`) 來定義。</span><span class="sxs-lookup"><span data-stu-id="d3f18-182">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="d3f18-183">元素屬性所指定的任何原則，都會套用至沒有為該原則指定值的所有子元素。</span><span class="sxs-lookup"><span data-stu-id="d3f18-183">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="d3f18-184">例如，如果以 [Type](type-element-net-native.md) 項目來指定原則，則該原則會套用至未明確指定原則的所有內含類型和成員。</span><span class="sxs-lookup"><span data-stu-id="d3f18-184">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="d3f18-185">可以使用 [Application](application-element-net-native.md)、[Assembly](assembly-element-net-native.md)、[AttributeImplies](attributeimplies-element-net-native.md)、[Namespace](namespace-element-net-native.md)、[Subtypes](subtypes-element-net-native.md) 和 [Type](type-element-net-native.md) 項目表示的原則，不同於可以為個別成員表示的原則 (使用 [Method](method-element-net-native.md)、[Property](property-element-net-native.md)、[Field](field-element-net-native.md) 和 [Event](event-element-net-native.md) 項目)。</span><span class="sxs-lookup"><span data-stu-id="d3f18-185">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="d3f18-186">為組件、命名空間和類型指定原則</span><span class="sxs-lookup"><span data-stu-id="d3f18-186">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="d3f18-187">[Application](application-element-net-native.md)、[Assembly](assembly-element-net-native.md)、[AttributeImplies](attributeimplies-element-net-native.md)、[Namespace](namespace-element-net-native.md)、[Subtypes](subtypes-element-net-native.md) 和 [Type](type-element-net-native.md) 項目支援下列原則類型：</span><span class="sxs-lookup"><span data-stu-id="d3f18-187">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="d3f18-188">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-188">`Activate`.</span></span> <span data-ttu-id="d3f18-189">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="d3f18-189">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="d3f18-190">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-190">`Browse`.</span></span> <span data-ttu-id="d3f18-191">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="d3f18-191">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="d3f18-192">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-192">`Dynamic`.</span></span> <span data-ttu-id="d3f18-193">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="d3f18-193">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="d3f18-194">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-194">`Serialize`.</span></span> <span data-ttu-id="d3f18-195">控制對建構函式、欄位和屬性的執行階段存取，讓類型執行個體能夠以 Newtonsoft JSON 序列化程式之類的協力廠商程式庫來序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="d3f18-195">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="d3f18-196">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-196">`DataContractSerializer`.</span></span> <span data-ttu-id="d3f18-197">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-197">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="d3f18-198">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-198">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="d3f18-199">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-199">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="d3f18-200">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-200">`XmlSerializer`.</span></span> <span data-ttu-id="d3f18-201">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-201">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="d3f18-202">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-202">`MarshalObject`.</span></span> <span data-ttu-id="d3f18-203">控制將參考類型封送處理至 WinRT 及 COM 的原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-203">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="d3f18-204">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-204">`MarshalDelegate`.</span></span> <span data-ttu-id="d3f18-205">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-205">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="d3f18-206">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="d3f18-206">`MarshalStructure` .</span></span> <span data-ttu-id="d3f18-207">控制將結構封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-207">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="d3f18-208">與這些原則類型相關聯的設定如下：</span><span class="sxs-lookup"><span data-stu-id="d3f18-208">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="d3f18-209">`All`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-209">`All`.</span></span> <span data-ttu-id="d3f18-210">針對工具鏈未移除的所有類型和成員，啟用原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-210">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="d3f18-211">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-211">`Auto`.</span></span> <span data-ttu-id="d3f18-212">使用預設行為。</span><span class="sxs-lookup"><span data-stu-id="d3f18-212">Use the default behavior.</span></span> <span data-ttu-id="d3f18-213">(除非原則被 (例如父元素) 覆寫，否則，不指定原則相當於將該原則設定為 `Auto`。)</span><span class="sxs-lookup"><span data-stu-id="d3f18-213">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="d3f18-214">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-214">`Excluded`.</span></span> <span data-ttu-id="d3f18-215">為程式元素停用原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-215">Disable the policy for the program element.</span></span>

- <span data-ttu-id="d3f18-216">`Public`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-216">`Public`.</span></span> <span data-ttu-id="d3f18-217">為公用類型或成員啟用原則，除非工具鏈判斷該成員是不必要的，並因此將它移除。</span><span class="sxs-lookup"><span data-stu-id="d3f18-217">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="d3f18-218">(在後者的情況下，您必須使用 `Required Public` 以確保該成員會保留，而且具有反映功能。)</span><span class="sxs-lookup"><span data-stu-id="d3f18-218">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="d3f18-219">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-219">`PublicAndInternal`.</span></span> <span data-ttu-id="d3f18-220">如果公用和內部類型或成員沒有被工具鏈移除，則為其啟用原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-220">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="d3f18-221">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-221">`Required Public`.</span></span> <span data-ttu-id="d3f18-222">需要工具鏈保留公用類型和成員 (無論是否使用)，並為其啟用原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-222">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="d3f18-223">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-223">`Required PublicAndInternal`.</span></span> <span data-ttu-id="d3f18-224">需要工具鏈同時保留公用和內部類型和成員 (無論是否使用)，並為其啟用原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-224">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="d3f18-225">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="d3f18-225">`Required All`.</span></span> <span data-ttu-id="d3f18-226">需要工具鏈保留所有類型和成員 (無論是否使用)，並為其啟用原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-226">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="d3f18-227">例如，下列執行階段指示詞檔案會為組件 DataClasses.dll 中的所有類型和成員定義原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-227">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="d3f18-228">它會為所有公用屬性 (property) 的序列化啟用反映功能，為所有類型和類型成員啟用瀏覽功能，為所有類型啟用啟動功能 (因為 `Dynamic` 屬性 (attribute))，並為所有公用類型和成員啟用反映功能。</span><span class="sxs-lookup"><span data-stu-id="d3f18-228">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

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

### <a name="specifying-policy-for-members"></a><span data-ttu-id="d3f18-229">為成員指定原則</span><span class="sxs-lookup"><span data-stu-id="d3f18-229">Specifying policy for members</span></span>

<span data-ttu-id="d3f18-230">[Property](property-element-net-native.md) 和 [Field](field-element-net-native.md) 項目支援下列原則類型：</span><span class="sxs-lookup"><span data-stu-id="d3f18-230">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="d3f18-231">`Browse` - 控制對此成員相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="d3f18-231">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="d3f18-232">`Dynamic` - 控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="d3f18-232">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="d3f18-233">另外也會控制對包含類型相關資訊的查詢。</span><span class="sxs-lookup"><span data-stu-id="d3f18-233">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="d3f18-234">`Serialize` - 控制對成員的執行階段存取，讓類型執行個體能夠以 Newtonsoft JSON 序列化程式之類的程式庫來序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="d3f18-234">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="d3f18-235">這個原則可以套用至建構函式、欄位和屬性。</span><span class="sxs-lookup"><span data-stu-id="d3f18-235">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="d3f18-236">[Method](method-element-net-native.md) 和 [Event](event-element-net-native.md) 項目支援下列原則類型：</span><span class="sxs-lookup"><span data-stu-id="d3f18-236">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="d3f18-237">`Browse` - 控制對此成員相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="d3f18-237">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="d3f18-238">`Dynamic` - 控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="d3f18-238">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="d3f18-239">另外也會控制對包含類型相關資訊的查詢。</span><span class="sxs-lookup"><span data-stu-id="d3f18-239">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="d3f18-240">與這些原則類型相關聯的設定如下：</span><span class="sxs-lookup"><span data-stu-id="d3f18-240">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="d3f18-241">`Auto` - 使用預設行為。</span><span class="sxs-lookup"><span data-stu-id="d3f18-241">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="d3f18-242">(除非原則被覆寫，否則，不指定原則相當於將該原則設定為 `Auto`。）</span><span class="sxs-lookup"><span data-stu-id="d3f18-242">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="d3f18-243">`Excluded` - 永不包含成員的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d3f18-243">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="d3f18-244">`Included` - 如果父類型出現在輸出中，則啟用原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-244">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="d3f18-245">`Required` - 需要工具鏈保留此成員 (即使看似未使用)，並為其啟用原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-245">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="d3f18-246">執行階段指示詞檔案語意</span><span class="sxs-lookup"><span data-stu-id="d3f18-246">Runtime directives file semantics</span></span>

<span data-ttu-id="d3f18-247">可以將原則同時定義給較高層級和較低層級的元素。</span><span class="sxs-lookup"><span data-stu-id="d3f18-247">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="d3f18-248">例如，可以將原則定義給組件，以及該組件內含的一些類型。</span><span class="sxs-lookup"><span data-stu-id="d3f18-248">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="d3f18-249">如果未表示特定較低層級的元素，它會繼承其父元素的原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-249">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="d3f18-250">例如，如果 `Assembly` 元素存在，但 `Type` 元素不存在，則 `Assembly` 元素中指定的原則會套用至組件中的每個類型。</span><span class="sxs-lookup"><span data-stu-id="d3f18-250">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="d3f18-251">多個元素也可以將原則套用至相同的程式元素。</span><span class="sxs-lookup"><span data-stu-id="d3f18-251">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="d3f18-252">例如，個別的 [Assembly](assembly-element-net-native.md) 項目可能會以不同的方式，為相同的組件定義相同的原則項目。</span><span class="sxs-lookup"><span data-stu-id="d3f18-252">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="d3f18-253">以下章節將說明在這些情況下，如何解析特定類型的原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-253">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="d3f18-254">泛型型別或方法的 [Type](type-element-net-native.md) 或 [Method](method-element-net-native.md) 項目，會將其原則套用至沒有自己原則的所有具現化。</span><span class="sxs-lookup"><span data-stu-id="d3f18-254">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="d3f18-255">例如，為 `Type` 指定原則的 <xref:System.Collections.Generic.List%601> 元素，會套用至該泛型類型的所有建構執行個體，除非已針對特定的建構泛型類型 (例如 `List<Int32>`)，以 `TypeInstantiation` 元素將它覆寫，</span><span class="sxs-lookup"><span data-stu-id="d3f18-255">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="d3f18-256">否則，元素會為所指名的程式元素定義原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-256">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="d3f18-257">當元素模稜兩可時，引擎會尋找相符項目，如果找到完全相符的項目，就會使用它。</span><span class="sxs-lookup"><span data-stu-id="d3f18-257">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="d3f18-258">如果找到多個相符項目，則會產生警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="d3f18-258">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="d3f18-259">如果有兩個指示詞將原則套用至相同的程式元素</span><span class="sxs-lookup"><span data-stu-id="d3f18-259">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="d3f18-260">如果不同執行階段指示詞檔案中的兩個元素，嘗試將相同程式元素 (例如組件或類型) 的相同原則類型設定為不同的值，則會以下列方式解決衝突：</span><span class="sxs-lookup"><span data-stu-id="d3f18-260">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="d3f18-261">如果 `Excluded` 元素存在，則以它為優先。</span><span class="sxs-lookup"><span data-stu-id="d3f18-261">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="d3f18-262">`Required` 的優先順序高於非 `Required`。</span><span class="sxs-lookup"><span data-stu-id="d3f18-262">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="d3f18-263">`All` 的優先順序高於 `PublicAndInternal`，而後者的優先順序高於 `Public`。</span><span class="sxs-lookup"><span data-stu-id="d3f18-263">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="d3f18-264">任何明確的設定皆優先於 `Auto`。</span><span class="sxs-lookup"><span data-stu-id="d3f18-264">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="d3f18-265">例如，如果單一專案包含下列兩個執行階段指示詞檔案，則 DataClasses.dll 的序列化原則會同時設為 `Required Public` 和 `All`。</span><span class="sxs-lookup"><span data-stu-id="d3f18-265">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="d3f18-266">在此情況下，序列化原則會被解析成 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="d3f18-266">In this case, the serialization policy would be resolved as `Required All`.</span></span>

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

<span data-ttu-id="d3f18-267">不過，如果單一執行階段指示詞檔案中的兩個指示詞嘗試為相同的程式元素設定相同的原則類型，則 XML 配置定義工具會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="d3f18-267">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="d3f18-268">如果子元素和父元素套用相同的原則類型</span><span class="sxs-lookup"><span data-stu-id="d3f18-268">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="d3f18-269">子元素會覆寫其父元素，包括 `Excluded` 設定。</span><span class="sxs-lookup"><span data-stu-id="d3f18-269">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="d3f18-270">覆寫是您會想要指定 `Auto` 的主要原因。</span><span class="sxs-lookup"><span data-stu-id="d3f18-270">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="d3f18-271">在下列範例中，針對 `DataClasses` 中不在 `DataClasses.ViewModels` 內的所有項目，序列化原則設定為 `Required Public`，而針對不在 `DataClasses` 和 `DataClasses.ViewModels` 內的所有項目，則為 `All`。</span><span class="sxs-lookup"><span data-stu-id="d3f18-271">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="d3f18-272">如果開放式泛型和具現化的元素套用相同的原則類型</span><span class="sxs-lookup"><span data-stu-id="d3f18-272">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="d3f18-273">在下列範例中，當引擎有必須為 `Dictionary<int,int>` 指定 `Browse` 原則的其他理由時，才會為其指派 `Browse` 原則 (否則為預設行為)；<xref:System.Collections.Generic.Dictionary%602> 的每個其他具現化都會使其所有成員可供瀏覽。</span><span class="sxs-lookup"><span data-stu-id="d3f18-273">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
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

### <a name="how-policy-is-inferred"></a><span data-ttu-id="d3f18-274">推斷原則的方式</span><span class="sxs-lookup"><span data-stu-id="d3f18-274">How policy is inferred</span></span>

<span data-ttu-id="d3f18-275">每個原則類型都有一組不同的規則，用以判斷該原則類型的存在對其他建構有何影響。</span><span class="sxs-lookup"><span data-stu-id="d3f18-275">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="d3f18-276">瀏覽原則的效果</span><span class="sxs-lookup"><span data-stu-id="d3f18-276">The effect of Browse policy</span></span>

<span data-ttu-id="d3f18-277">將 `Browse` 原則套用至類型牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="d3f18-277">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="d3f18-278">類型的基底類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-278">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-279">如果類型是具現化泛型，則該類型的未具現化版本會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-279">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-280">如果類型是委派，則該類型上的 `Invoke` 方法會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-280">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="d3f18-281">類型的每個介面都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-281">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-282">套用至類型的每個屬性類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-282">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-283">如果類型是泛型，則每個條件約束類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-283">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-284">如果類型是泛型，則具現化類型之下的類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-284">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="d3f18-285">將 `Browse` 原則套用至方法牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="d3f18-285">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="d3f18-286">方法的每個參數類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-286">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-287">方法的傳回型別會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-287">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-288">方法的包含類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-288">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-289">如果方法是具現化泛型方法，則未具現化的泛型方法會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-289">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-290">套用至方法的每個屬性類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-290">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-291">如果方法是泛型，則每個條件約束類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-291">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-292">如果方法是泛型，則具現化方法之下的類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-292">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="d3f18-293">將 `Browse` 原則套用至欄位牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="d3f18-293">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="d3f18-294">套用至欄位的每個屬性類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-294">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-295">欄位的類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-295">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-296">欄位所屬的類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-296">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="d3f18-297">動態原則的效果</span><span class="sxs-lookup"><span data-stu-id="d3f18-297">The effect of Dynamic policy</span></span>

<span data-ttu-id="d3f18-298">將 `Dynamic` 原則套用至類型牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="d3f18-298">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="d3f18-299">類型的基底類型會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-299">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="d3f18-300">如果類型是具現化泛型，則該類型的未具現化版本會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-300">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="d3f18-301">如果類型是委派類型，則該類型上的 `Invoke` 方法會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-301">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="d3f18-302">類型的每個介面都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-302">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-303">套用至類型的每個屬性類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-303">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-304">如果類型是泛型，則每個條件約束類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-304">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-305">如果類型是泛型，則具現化類型之下的類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-305">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="d3f18-306">將 `Dynamic` 原則套用至方法牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="d3f18-306">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="d3f18-307">方法的每個參數類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-307">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-308">方法的傳回型別會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-308">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="d3f18-309">方法的包含類型會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-309">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="d3f18-310">如果方法是具現化泛型方法，則未具現化的泛型方法會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-310">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-311">套用至方法的每個屬性類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-311">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-312">如果方法是泛型，則每個條件約束類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-312">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-313">如果方法是泛型，則具現化方法之下的類型會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-313">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-314">可以藉由 `MethodInfo.Invoke` 來叫用方法，而藉由 <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType> 就能夠進行委派建立。</span><span class="sxs-lookup"><span data-stu-id="d3f18-314">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d3f18-315">將 `Dynamic` 原則套用至欄位牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="d3f18-315">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="d3f18-316">套用至欄位的每個屬性類型都會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-316">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-317">欄位的類型會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-317">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="d3f18-318">欄位所屬的類型會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-318">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="d3f18-319">啟動原則的效果</span><span class="sxs-lookup"><span data-stu-id="d3f18-319">The effect of Activation policy</span></span>

<span data-ttu-id="d3f18-320">將啟動原則套用至類型牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="d3f18-320">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="d3f18-321">如果類型是具現化泛型，則該類型的未具現化版本會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-321">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-322">如果類型是委派類型，則該類型上的 `Invoke` 方法會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-322">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="d3f18-323">類型的建構函式會標示 `Activation` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-323">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="d3f18-324">將 `Activation` 原則套用至方法牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="d3f18-324">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="d3f18-325">可以藉由 <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> 和 <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 方法來叫用建構函式。</span><span class="sxs-lookup"><span data-stu-id="d3f18-325">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="d3f18-326">對於方法，`Activation` 原則只會影響建構函式。</span><span class="sxs-lookup"><span data-stu-id="d3f18-326">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="d3f18-327">將 `Activation` 原則套用至欄位並沒有效果。</span><span class="sxs-lookup"><span data-stu-id="d3f18-327">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="d3f18-328">序列化原則的效果</span><span class="sxs-lookup"><span data-stu-id="d3f18-328">The effect of Serialize policy</span></span>

<span data-ttu-id="d3f18-329">`Serialize` 原則可以啟用一般反映型序列化程式。</span><span class="sxs-lookup"><span data-stu-id="d3f18-329">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="d3f18-330">不過，由於 Microsoft 並不清楚非 Microsoft 序列化程式的確切反映存取模式，所以此原則可能不是全面有效。</span><span class="sxs-lookup"><span data-stu-id="d3f18-330">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="d3f18-331">將 `Serialize` 原則套用至類型牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="d3f18-331">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="d3f18-332">類型的基底類型會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-332">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="d3f18-333">如果類型是具現化泛型，則該類型的未具現化版本會標示 `Browse` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-333">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="d3f18-334">如果類型是委派類型，則該類型上的 `Invoke` 方法會標示 `Dynamic` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-334">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="d3f18-335">如果類型是列舉，則類型的陣列會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-335">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="d3f18-336">如果類型實作 <xref:System.Collections.Generic.IEnumerable%601>，則 `T` 會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-336">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="d3f18-337">如果類型是 <xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.Generic.IList%601>、<xref:System.Collections.Generic.ICollection%601>、<xref:System.Collections.Generic.IReadOnlyCollection%601> 或 <xref:System.Collections.Generic.IReadOnlyList%601>，則 `T[]` 和 <xref:System.Collections.Generic.List%601> 會標示 `Serialize` 原則，但介面類型沒有任何成員會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-337">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="d3f18-338">如果類型是 <xref:System.Collections.Generic.List%601>，則沒有任何類型成員會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-338">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="d3f18-339">如果類型是 <xref:System.Collections.Generic.IDictionary%602>，則 <xref:System.Collections.Generic.Dictionary%602> 會標示 `Serialize` 原則，</span><span class="sxs-lookup"><span data-stu-id="d3f18-339">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="d3f18-340">但沒有任何類型成員會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-340">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="d3f18-341">如果類型是 <xref:System.Collections.Generic.Dictionary%602>，則沒有任何類型成員會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-341">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="d3f18-342">如果類型實作 <xref:System.Collections.Generic.IDictionary%602>，則 `TKey` 和 `TValue` 會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-342">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="d3f18-343">每個建構函式、每個屬性存取子和每個欄位都會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-343">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="d3f18-344">將 `Serialize` 原則套用至方法牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="d3f18-344">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="d3f18-345">包含類型會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-345">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="d3f18-346">方法的傳回型別會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-346">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="d3f18-347">將 `Serialize` 原則套用至欄位牽涉到下列原則變更：</span><span class="sxs-lookup"><span data-stu-id="d3f18-347">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="d3f18-348">包含類型會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-348">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="d3f18-349">欄位的類型會標示 `Serialize` 原則。</span><span class="sxs-lookup"><span data-stu-id="d3f18-349">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="d3f18-350">XmlSerializer、DataContractSerializer 和 DataContractJsonSerializer 原則的效果</span><span class="sxs-lookup"><span data-stu-id="d3f18-350">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="d3f18-351">不同于用於反映型<xref:System.Xml.Serialization.XmlSerializer>序列化程式的<xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> `Serialize`原則，、和原則是用來啟用一組 .NET Native 工具鏈已知的序列化程式。</span><span class="sxs-lookup"><span data-stu-id="d3f18-351">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="d3f18-352">這些序列化程式不是使用反映來實作，但是可以用類似可反映式類型的方法，來判斷可以在執行階段序列化的類型集。</span><span class="sxs-lookup"><span data-stu-id="d3f18-352">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="d3f18-353">將這些原則的其中之一套用至類型，可讓該類型以相符的序列化程式來進行序列化。</span><span class="sxs-lookup"><span data-stu-id="d3f18-353">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="d3f18-354">此外，序列化引擎可以用靜態方式判斷為需要序列化的任何類型，也都可以序列化。</span><span class="sxs-lookup"><span data-stu-id="d3f18-354">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="d3f18-355">這些原則對方法或欄位沒有任何效果。</span><span class="sxs-lookup"><span data-stu-id="d3f18-355">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="d3f18-356">如需詳細資訊，請參閱[將您的 Windows 市集應用程式移轉至 .NET Native](migrating-your-windows-store-app-to-net-native.md)中的＜序列化程式的差異＞一節。</span><span class="sxs-lookup"><span data-stu-id="d3f18-356">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d3f18-357">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3f18-357">See also</span></span>

- [<span data-ttu-id="d3f18-358">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="d3f18-358">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="d3f18-359">反映和 .NET Native</span><span class="sxs-lookup"><span data-stu-id="d3f18-359">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
