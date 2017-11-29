---
title: "&lt;declaredTypes&gt; 項目的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 699d18b4c49d2915724309d96d4ad501b98601eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltdeclaredtypesgt-element"></a><span data-ttu-id="c2652-102">&lt;declaredTypes&gt; 項目的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="c2652-102">&lt;add&gt; of &lt;declaredTypes&gt; Element</span></span>
<span data-ttu-id="c2652-103">在還原序列化期間，新增 <xref:System.Runtime.Serialization.DataContractSerializer> 所使用的型別。</span><span class="sxs-lookup"><span data-stu-id="c2652-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="c2652-104">每個宣告的型別都包含已知型別，這些已知型別將傳回做為宣告型別的欄位或屬性。</span><span class="sxs-lookup"><span data-stu-id="c2652-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="c2652-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="c2652-105">system.runtime.serialization</span></span>  
<span data-ttu-id="c2652-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c2652-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="c2652-107">\<p ></span><span class="sxs-lookup"><span data-stu-id="c2652-107">\<declaredTypes></span></span>  
<span data-ttu-id="c2652-108">\<新增 > 的\<p ></span><span class="sxs-lookup"><span data-stu-id="c2652-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2652-109">語法</span><span class="sxs-lookup"><span data-stu-id="c2652-109">Syntax</span></span>  
  
```xml  
<add type="String">  
   <knownType type="String">  
       <parameter index="Integer"  
                  type="String" />  
   </knownType>  
</add>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2652-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c2652-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c2652-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c2652-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2652-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c2652-112">Attributes</span></span>  
  
|<span data-ttu-id="c2652-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c2652-113">Attribute</span></span>|<span data-ttu-id="c2652-114">描述</span><span class="sxs-lookup"><span data-stu-id="c2652-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2652-115">類型</span><span class="sxs-lookup"><span data-stu-id="c2652-115">type</span></span>|<span data-ttu-id="c2652-116">必要的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="c2652-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="c2652-117">指定型別名稱 (包括命名空間)、組件名稱、版本號碼、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="c2652-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2652-118">子元素</span><span class="sxs-lookup"><span data-stu-id="c2652-118">Child Elements</span></span>  
  
|<span data-ttu-id="c2652-119">項目</span><span class="sxs-lookup"><span data-stu-id="c2652-119">Element</span></span>|<span data-ttu-id="c2652-120">說明</span><span class="sxs-lookup"><span data-stu-id="c2652-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2652-121">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="c2652-121">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="c2652-122">為要加入的宣告型別指定已知型別。</span><span class="sxs-lookup"><span data-stu-id="c2652-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="c2652-123">如果宣告的型別是泛型型別，您也必須將參數項目加入至 `<knownType>` 項目，以指定要用於傳回已知型別的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="c2652-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2652-124">父項目</span><span class="sxs-lookup"><span data-stu-id="c2652-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c2652-125">項目</span><span class="sxs-lookup"><span data-stu-id="c2652-125">Element</span></span>|<span data-ttu-id="c2652-126">說明</span><span class="sxs-lookup"><span data-stu-id="c2652-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2652-127">\<p ></span><span class="sxs-lookup"><span data-stu-id="c2652-127">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="c2652-128">包含還原序列化期間 <xref:System.Runtime.Serialization.DataContractSerializer> 所需已知型別的型別。</span><span class="sxs-lookup"><span data-stu-id="c2652-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2652-129">備註</span><span class="sxs-lookup"><span data-stu-id="c2652-129">Remarks</span></span>  
 <span data-ttu-id="c2652-130">如需已知型別的詳細資訊，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="c2652-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="c2652-131">請參閱[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)如需使用此元素的範例。</span><span class="sxs-lookup"><span data-stu-id="c2652-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2652-132">如果您將 <xref:System.Object> 型別加入做為 `<declaredType>`，則會擲回 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="c2652-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="c2652-133">這是因為 <xref:System.Object> 型別無法用來做為組態中的宣告型別。</span><span class="sxs-lookup"><span data-stu-id="c2652-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2652-134">範例</span><span class="sxs-lookup"><span data-stu-id="c2652-134">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2652-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2652-135">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="c2652-136">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="c2652-136">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="c2652-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c2652-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="c2652-138">\<新增 > 的\<p ></span><span class="sxs-lookup"><span data-stu-id="c2652-138">\<add> of \<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
