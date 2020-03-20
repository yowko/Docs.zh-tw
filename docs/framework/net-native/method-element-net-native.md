---
title: <Method>元素（.NET 本機）
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 8db32c660846b4f4071fff2a40c760a3d1ef2489
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180980"
---
# <a name="method-element-net-native"></a><span data-ttu-id="f89ab-102">\<方法>元素（.NET 本機）</span><span class="sxs-lookup"><span data-stu-id="f89ab-102">\<Method> Element (.NET Native)</span></span>
<span data-ttu-id="f89ab-103">將執行階段反映原則套用到建構函式或方法。</span><span class="sxs-lookup"><span data-stu-id="f89ab-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f89ab-104">語法</span><span class="sxs-lookup"><span data-stu-id="f89ab-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f89ab-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f89ab-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f89ab-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f89ab-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f89ab-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f89ab-107">Attributes</span></span>  
  
|<span data-ttu-id="f89ab-108">屬性</span><span class="sxs-lookup"><span data-stu-id="f89ab-108">Attribute</span></span>|<span data-ttu-id="f89ab-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="f89ab-109">Attribute type</span></span>|<span data-ttu-id="f89ab-110">描述</span><span class="sxs-lookup"><span data-stu-id="f89ab-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="f89ab-111">一般</span><span class="sxs-lookup"><span data-stu-id="f89ab-111">General</span></span>|<span data-ttu-id="f89ab-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f89ab-112">Required attribute.</span></span> <span data-ttu-id="f89ab-113">指定方法名稱。</span><span class="sxs-lookup"><span data-stu-id="f89ab-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="f89ab-114">一般</span><span class="sxs-lookup"><span data-stu-id="f89ab-114">General</span></span>|<span data-ttu-id="f89ab-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f89ab-115">Optional attribute.</span></span> <span data-ttu-id="f89ab-116">指定方法簽章。</span><span class="sxs-lookup"><span data-stu-id="f89ab-116">Specifies the method signature.</span></span> <span data-ttu-id="f89ab-117">如果有多個參數存在，會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="f89ab-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="f89ab-118">例如，下列 `<Method>` 元素會定義 <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> 方法的原則。</span><span class="sxs-lookup"><span data-stu-id="f89ab-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="f89ab-119">如果屬性不存在，執行階段指示詞會套用到方法的所有多載。</span><span class="sxs-lookup"><span data-stu-id="f89ab-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="f89ab-120">反射</span><span class="sxs-lookup"><span data-stu-id="f89ab-120">Reflection</span></span>|<span data-ttu-id="f89ab-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f89ab-121">Optional attribute.</span></span> <span data-ttu-id="f89ab-122">控制對方法相關資訊的查詢，或控制方法的列舉，但不會在執行階段啟用任何動態引動過程。</span><span class="sxs-lookup"><span data-stu-id="f89ab-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="f89ab-123">反射</span><span class="sxs-lookup"><span data-stu-id="f89ab-123">Reflection</span></span>|<span data-ttu-id="f89ab-124">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f89ab-124">Optional attribute.</span></span> <span data-ttu-id="f89ab-125">控制對建構函式或方法的執行階段存取權，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="f89ab-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="f89ab-126">此原則確保能夠在執行階段動態叫用成員。</span><span class="sxs-lookup"><span data-stu-id="f89ab-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="f89ab-127">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="f89ab-127">Name attribute</span></span>  
  
|<span data-ttu-id="f89ab-128">值</span><span class="sxs-lookup"><span data-stu-id="f89ab-128">Value</span></span>|<span data-ttu-id="f89ab-129">描述</span><span class="sxs-lookup"><span data-stu-id="f89ab-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f89ab-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="f89ab-130">*method_name*</span></span>|<span data-ttu-id="f89ab-131">方法名稱。</span><span class="sxs-lookup"><span data-stu-id="f89ab-131">The method name.</span></span> <span data-ttu-id="f89ab-132">該方法的類型由父[\<類型>](type-element-net-native.md)或[\<類型即時>](typeinstantiation-element-net-native.md)元素定義。</span><span class="sxs-lookup"><span data-stu-id="f89ab-132">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="f89ab-133">簽章屬性</span><span class="sxs-lookup"><span data-stu-id="f89ab-133">Signature attribute</span></span>  
  
|<span data-ttu-id="f89ab-134">值</span><span class="sxs-lookup"><span data-stu-id="f89ab-134">Value</span></span>|<span data-ttu-id="f89ab-135">描述</span><span class="sxs-lookup"><span data-stu-id="f89ab-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f89ab-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="f89ab-136">*method_signature*</span></span>|<span data-ttu-id="f89ab-137">構成方法簽章的參數類型。</span><span class="sxs-lookup"><span data-stu-id="f89ab-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="f89ab-138">若有多個參數，會以逗號分隔，例如，`"System.String,System.Int32,System.Int32)"`。</span><span class="sxs-lookup"><span data-stu-id="f89ab-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="f89ab-139">參數類型名稱應該是完整名稱。</span><span class="sxs-lookup"><span data-stu-id="f89ab-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="f89ab-140">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="f89ab-140">All other attributes</span></span>  
  
|<span data-ttu-id="f89ab-141">值</span><span class="sxs-lookup"><span data-stu-id="f89ab-141">Value</span></span>|<span data-ttu-id="f89ab-142">描述</span><span class="sxs-lookup"><span data-stu-id="f89ab-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f89ab-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="f89ab-143">*policy_setting*</span></span>|<span data-ttu-id="f89ab-144">要套用到此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="f89ab-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="f89ab-145">可能的值為 `Auto`、`Excluded`、`Included` 和 `Required`。</span><span class="sxs-lookup"><span data-stu-id="f89ab-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="f89ab-146">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="f89ab-146">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f89ab-147">子元素</span><span class="sxs-lookup"><span data-stu-id="f89ab-147">Child Elements</span></span>  
  
|<span data-ttu-id="f89ab-148">元素</span><span class="sxs-lookup"><span data-stu-id="f89ab-148">Element</span></span>|<span data-ttu-id="f89ab-149">描述</span><span class="sxs-lookup"><span data-stu-id="f89ab-149">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f89ab-150">\<參數></span><span class="sxs-lookup"><span data-stu-id="f89ab-150">\<Parameter></span></span>](parameter-element-net-native.md)|<span data-ttu-id="f89ab-151">將原則套用到傳遞至方法的引數類型。</span><span class="sxs-lookup"><span data-stu-id="f89ab-151">Applies policy to the type of the argument passed to a method.</span></span>|  
|[<span data-ttu-id="f89ab-152">\<泛型參數></span><span class="sxs-lookup"><span data-stu-id="f89ab-152">\<GenericParameter></span></span>](genericparameter-element-net-native.md)|<span data-ttu-id="f89ab-153">將原則套用到泛型類型或方法的參數類型。</span><span class="sxs-lookup"><span data-stu-id="f89ab-153">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[<span data-ttu-id="f89ab-154">\<暗示類型></span><span class="sxs-lookup"><span data-stu-id="f89ab-154">\<ImpliesType></span></span>](impliestype-element-net-native.md)|<span data-ttu-id="f89ab-155">如果原則已套用至包含 `<Method>` 元素所表示的方法，則會將該原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="f89ab-155">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[<span data-ttu-id="f89ab-156">\<類型參數></span><span class="sxs-lookup"><span data-stu-id="f89ab-156">\<TypeParameter></span></span>](typeparameter-element-net-native.md)|<span data-ttu-id="f89ab-157">將原則套用至傳遞給方法之 <xref:System.Type> 引數所表示的類型。</span><span class="sxs-lookup"><span data-stu-id="f89ab-157">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f89ab-158">父項目</span><span class="sxs-lookup"><span data-stu-id="f89ab-158">Parent Elements</span></span>  
  
|<span data-ttu-id="f89ab-159">元素</span><span class="sxs-lookup"><span data-stu-id="f89ab-159">Element</span></span>|<span data-ttu-id="f89ab-160">描述</span><span class="sxs-lookup"><span data-stu-id="f89ab-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f89ab-161">\<鍵入></span><span class="sxs-lookup"><span data-stu-id="f89ab-161">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="f89ab-162">將反映原則套用至類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="f89ab-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="f89ab-163">\<類型即時></span><span class="sxs-lookup"><span data-stu-id="f89ab-163">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="f89ab-164">將反映原則套用至建構泛型類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="f89ab-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f89ab-165">備註</span><span class="sxs-lookup"><span data-stu-id="f89ab-165">Remarks</span></span>  
 <span data-ttu-id="f89ab-166">泛型方法的 `<Method>` 的元素會將其原則套用至沒有自己原則的所有具現化。</span><span class="sxs-lookup"><span data-stu-id="f89ab-166">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="f89ab-167">您可以使用 `Signature` 屬性來指定適用於特定方法多載的原則。</span><span class="sxs-lookup"><span data-stu-id="f89ab-167">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="f89ab-168">否則，如果 `Signature` 屬性不存在，執行階段指示詞就會套用到方法的所有多載。</span><span class="sxs-lookup"><span data-stu-id="f89ab-168">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="f89ab-169">您不能使用 `<Method>` 元素來為建構函式定義執行階段反映原則，</span><span class="sxs-lookup"><span data-stu-id="f89ab-169">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="f89ab-170">`Activate`而是使用[\<程式集>、](assembly-element-net-native.md)[\<命名空間>、](namespace-element-net-native.md)[\<類型>](type-element-net-native.md)或[\<類型即時性>](typeinstantiation-element-net-native.md)元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="f89ab-170">Instead, use the `Activate` attribute of the  [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), [\<Type>](type-element-net-native.md), or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f89ab-171">範例</span><span class="sxs-lookup"><span data-stu-id="f89ab-171">Example</span></span>  
 <span data-ttu-id="f89ab-172">下列範例中的 `Stringify` 方法是一般用途的格式化方法，它會使用反映將物件轉換成其字串表示法。</span><span class="sxs-lookup"><span data-stu-id="f89ab-172">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="f89ab-173">除了呼叫物件的預設 `ToString` 方法，此方法還可以將格式字串及/或 `ToString` 實作傳遞給物件的 <xref:System.IFormatProvider> 方法，以產生格式化的結果字串。</span><span class="sxs-lookup"><span data-stu-id="f89ab-173">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="f89ab-174">它也可以呼叫其中一個 <xref:System.Convert.ToString%2A?displayProperty=nameWithType> 多載，將數字轉換成二進位、十六進位或八進位表示法。</span><span class="sxs-lookup"><span data-stu-id="f89ab-174">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="f89ab-175">您可以用類似下列程式碼來呼叫 `Stringify` 方法：</span><span class="sxs-lookup"><span data-stu-id="f89ab-175">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="f89ab-176">不過，以 .NET Native 來編譯時，此範例可能會在執行階段擲回一些例外狀況，包括 <xref:System.NullReferenceException> 和 [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 例外狀況。這是因為 `Stringify` 方法主要的目的是支援將 .NET Framework Class Library 中的基本類型動態格式化。</span><span class="sxs-lookup"><span data-stu-id="f89ab-176">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="f89ab-177">不過，預設指示詞檔案並沒有提供其中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f89ab-177">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="f89ab-178">但是，即使其中繼資料可供使用，範例還是會擲回 [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 例外狀況，因為適當的 `ToString` 實作尚未包含在機器碼中。</span><span class="sxs-lookup"><span data-stu-id="f89ab-178">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="f89ab-179">通過使用[\<Type>](type-element-net-native.md)元素定義其中繼資料必須存在的類型，以及添加`<Method>`元素以確保存在可動態調用的方法重載的實現，可以全部消除這些異常。</span><span class="sxs-lookup"><span data-stu-id="f89ab-179">These exceptions can all be eliminated by using the [\<Type>](type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="f89ab-180">以下是可消除這些例外狀況，並可讓範例執行而不會發生錯誤的 default.rd.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="f89ab-180">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f89ab-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f89ab-181">See also</span></span>

- [<span data-ttu-id="f89ab-182">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="f89ab-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="f89ab-183">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="f89ab-183">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="f89ab-184">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="f89ab-184">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="f89ab-185">\<方法具現化>元素</span><span class="sxs-lookup"><span data-stu-id="f89ab-185">\<MethodInstantiation> Element</span></span>](methodinstantiation-element-net-native.md)
