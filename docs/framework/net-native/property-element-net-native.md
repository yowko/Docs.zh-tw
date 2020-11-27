---
title: '<Property> 元素 ( .NET Native) '
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
ms.openlocfilehash: a0bdf95a1d1cadf7423f8c6595add13eda4d0d9a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250849"
---
# <a name="property-element-net-native"></a><span data-ttu-id="ff3ac-102">\<Property> 元素 ( .NET Native) </span><span class="sxs-lookup"><span data-stu-id="ff3ac-102">\<Property> Element (.NET Native)</span></span>

<span data-ttu-id="ff3ac-103">將執行階段反映原則套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-103">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff3ac-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ff3ac-104">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff3ac-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ff3ac-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ff3ac-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff3ac-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ff3ac-107">Attributes</span></span>  
  
|<span data-ttu-id="ff3ac-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ff3ac-108">Attribute</span></span>|<span data-ttu-id="ff3ac-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="ff3ac-109">Attribute type</span></span>|<span data-ttu-id="ff3ac-110">描述</span><span class="sxs-lookup"><span data-stu-id="ff3ac-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="ff3ac-111">一般</span><span class="sxs-lookup"><span data-stu-id="ff3ac-111">General</span></span>|<span data-ttu-id="ff3ac-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-112">Required attribute.</span></span> <span data-ttu-id="ff3ac-113">指定屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-113">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="ff3ac-114">反射</span><span class="sxs-lookup"><span data-stu-id="ff3ac-114">Reflection</span></span>|<span data-ttu-id="ff3ac-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-115">Optional attribute.</span></span> <span data-ttu-id="ff3ac-116">控制對屬性相關資訊的查詢，或控制屬性的列舉，但不會在執行階段啟用任何動態存取。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-116">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="ff3ac-117">反射</span><span class="sxs-lookup"><span data-stu-id="ff3ac-117">Reflection</span></span>|<span data-ttu-id="ff3ac-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-118">Optional attribute.</span></span> <span data-ttu-id="ff3ac-119">控制對屬性的執行階段存取權，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-119">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="ff3ac-120">此原則可確保能夠在執行階段動態設定或擷取屬性。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-120">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="ff3ac-121">序列化</span><span class="sxs-lookup"><span data-stu-id="ff3ac-121">Serialization</span></span>|<span data-ttu-id="ff3ac-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-122">Optional attribute.</span></span> <span data-ttu-id="ff3ac-123">控制對屬性的執行階段存取權，使類型執行個體能夠由 Newtonsoft JSON 序列化程式之類的程式庫來序列化，或是用於資料繫結。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-123">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="ff3ac-124">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="ff3ac-124">Name attribute</span></span>  
  
|<span data-ttu-id="ff3ac-125">值</span><span class="sxs-lookup"><span data-stu-id="ff3ac-125">Value</span></span>|<span data-ttu-id="ff3ac-126">描述</span><span class="sxs-lookup"><span data-stu-id="ff3ac-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ff3ac-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="ff3ac-127">*method_name*</span></span>|<span data-ttu-id="ff3ac-128">屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-128">The property name.</span></span> <span data-ttu-id="ff3ac-129">屬性的類型是由父系 [\<Type>](type-element-net-native.md) 或 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 元素定義。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-129">The type of the property is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="ff3ac-130">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="ff3ac-130">All other attributes</span></span>  
  
|<span data-ttu-id="ff3ac-131">值</span><span class="sxs-lookup"><span data-stu-id="ff3ac-131">Value</span></span>|<span data-ttu-id="ff3ac-132">描述</span><span class="sxs-lookup"><span data-stu-id="ff3ac-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ff3ac-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ff3ac-133">*policy_setting*</span></span>|<span data-ttu-id="ff3ac-134">要為屬性套用此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-134">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="ff3ac-135">可能的值為 `Auto`、`Excluded`、`Included` 和 `Required`。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="ff3ac-136">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff3ac-137">子元素</span><span class="sxs-lookup"><span data-stu-id="ff3ac-137">Child Elements</span></span>  

 <span data-ttu-id="ff3ac-138">無。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff3ac-139">父項目</span><span class="sxs-lookup"><span data-stu-id="ff3ac-139">Parent Elements</span></span>  
  
|<span data-ttu-id="ff3ac-140">元素</span><span class="sxs-lookup"><span data-stu-id="ff3ac-140">Element</span></span>|<span data-ttu-id="ff3ac-141">描述</span><span class="sxs-lookup"><span data-stu-id="ff3ac-141">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="ff3ac-142">將反映原則套用至類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-142">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="ff3ac-143">將反映原則套用至建構泛型類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-143">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff3ac-144">備註</span><span class="sxs-lookup"><span data-stu-id="ff3ac-144">Remarks</span></span>  

 <span data-ttu-id="ff3ac-145">如果未明確定義屬性的原則，則會繼承其父元素的執行階段原則。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-145">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff3ac-146">範例</span><span class="sxs-lookup"><span data-stu-id="ff3ac-146">Example</span></span>  

 <span data-ttu-id="ff3ac-147">下列範例會使用反映來具現化 `Book` 物件，並顯示其屬性值。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-147">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="ff3ac-148">專案的原始 default.rd.xml 檔案會像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="ff3ac-148">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="ff3ac-149">檔案會針對 `All` 類別，將 `Activate` 值套用至 `Book` 原則，如此可允許透過反映來存取類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-149">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="ff3ac-150">`Browse` 類別的 `Book` 原則繼承自其父命名空間。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-150">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="ff3ac-151">其設定為 `Required Public`，讓中繼資料在執行階段可供使用。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-151">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="ff3ac-152">以下是範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-152">The following is the source code for the example.</span></span> <span data-ttu-id="ff3ac-153">`outputBlock`變數代表 <xref:Windows.UI.Xaml.Controls.TextBlock> 控制項。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-153">The `outputBlock` variable represents a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="ff3ac-154">不過，編譯和執行此範例會擲回 [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-154">However, compiling and executing this example throws a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="ff3ac-155">雖然我們已經讓 `Book` 類型的中繼資料可供使用，但我們無法讓屬性 getter 的實作供動態使用。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-155">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="ff3ac-156">我們可以用下列兩種方法之一來更正這個錯誤：</span><span class="sxs-lookup"><span data-stu-id="ff3ac-156">We can correct this error by either in one of two ways:</span></span>  
  
- <span data-ttu-id="ff3ac-157">藉由 `Dynamic` 在專案中定義 `Book` 類型的原則 [\<Type>](type-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-157">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](type-element-net-native.md) element.</span></span>  
  
- <span data-ttu-id="ff3ac-158">藉由 [\<Property>](property-element-net-native.md) 為要叫用其 getter 的每個屬性加入一個 nested 元素，如下 default.rd.xml 檔案所示。</span><span class="sxs-lookup"><span data-stu-id="ff3ac-158">By adding a nested [\<Property>](property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ff3ac-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff3ac-159">See also</span></span>

- [<span data-ttu-id="ff3ac-160">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="ff3ac-160">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ff3ac-161">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="ff3ac-161">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="ff3ac-162">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="ff3ac-162">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
