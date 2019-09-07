---
title: <add> 項目的 <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: a001e8743b2c24f68b1b23cbccf3e5ac162c4e71
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400663"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="afcbb-102">\<新增 declaredTypes > \<元素的 ></span><span class="sxs-lookup"><span data-stu-id="afcbb-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="afcbb-103">在還原序列化期間，新增 <xref:System.Runtime.Serialization.DataContractSerializer> 所使用的型別。</span><span class="sxs-lookup"><span data-stu-id="afcbb-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="afcbb-104">每個宣告的型別都包含已知型別，這些已知型別將傳回做為宣告型別的欄位或屬性。</span><span class="sxs-lookup"><span data-stu-id="afcbb-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
<span data-ttu-id="afcbb-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="afcbb-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="afcbb-106">&nbsp;&nbsp;[ **\<> 的序列化**](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="afcbb-106">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="afcbb-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dataContractSerializer >** ](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="afcbb-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="afcbb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="afcbb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="afcbb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="afcbb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afcbb-110">語法</span><span class="sxs-lookup"><span data-stu-id="afcbb-110">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afcbb-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="afcbb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="afcbb-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="afcbb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afcbb-113">屬性</span><span class="sxs-lookup"><span data-stu-id="afcbb-113">Attributes</span></span>  
  
|<span data-ttu-id="afcbb-114">屬性</span><span class="sxs-lookup"><span data-stu-id="afcbb-114">Attribute</span></span>|<span data-ttu-id="afcbb-115">描述</span><span class="sxs-lookup"><span data-stu-id="afcbb-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="afcbb-116">型別</span><span class="sxs-lookup"><span data-stu-id="afcbb-116">type</span></span>|<span data-ttu-id="afcbb-117">必要的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="afcbb-117">Required string attribute.</span></span><br /><br /> <span data-ttu-id="afcbb-118">指定型別名稱 (包括命名空間)、組件名稱、版本號碼、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="afcbb-118">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afcbb-119">子元素</span><span class="sxs-lookup"><span data-stu-id="afcbb-119">Child Elements</span></span>  
  
|<span data-ttu-id="afcbb-120">項目</span><span class="sxs-lookup"><span data-stu-id="afcbb-120">Element</span></span>|<span data-ttu-id="afcbb-121">描述</span><span class="sxs-lookup"><span data-stu-id="afcbb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afcbb-122">\<knownType></span><span class="sxs-lookup"><span data-stu-id="afcbb-122">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="afcbb-123">為要加入的宣告型別指定已知型別。</span><span class="sxs-lookup"><span data-stu-id="afcbb-123">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="afcbb-124">如果宣告的型別是泛型型別，您也必須將參數項目加入至 `<knownType>` 項目，以指定要用於傳回已知型別的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="afcbb-124">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afcbb-125">父項目</span><span class="sxs-lookup"><span data-stu-id="afcbb-125">Parent Elements</span></span>  
  
|<span data-ttu-id="afcbb-126">項目</span><span class="sxs-lookup"><span data-stu-id="afcbb-126">Element</span></span>|<span data-ttu-id="afcbb-127">說明</span><span class="sxs-lookup"><span data-stu-id="afcbb-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afcbb-128">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="afcbb-128">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="afcbb-129">包含還原序列化期間 <xref:System.Runtime.Serialization.DataContractSerializer> 所需已知型別的型別。</span><span class="sxs-lookup"><span data-stu-id="afcbb-129">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afcbb-130">備註</span><span class="sxs-lookup"><span data-stu-id="afcbb-130">Remarks</span></span>  
 <span data-ttu-id="afcbb-131">如需已知類型的詳細資訊，請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="afcbb-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="afcbb-132">如需使用此元素的範例，請參閱[ dataContractSerializer>。\< ](datacontractserializer-element.md)</span><span class="sxs-lookup"><span data-stu-id="afcbb-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="afcbb-133">如果您將 <xref:System.Object> 型別加入做為 `<declaredType>`，則會擲回 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="afcbb-133">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="afcbb-134">這是因為 <xref:System.Object> 型別無法用來做為組態中的宣告型別。</span><span class="sxs-lookup"><span data-stu-id="afcbb-134">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afcbb-135">範例</span><span class="sxs-lookup"><span data-stu-id="afcbb-135">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="afcbb-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afcbb-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="afcbb-137">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="afcbb-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="afcbb-138">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="afcbb-138">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="afcbb-139">\<新增 declaredTypes > \<的 ></span><span class="sxs-lookup"><span data-stu-id="afcbb-139">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
