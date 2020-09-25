---
title: <add> 項目的 <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 9af47848b03074ec88f38a5884089bc50239ee50
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201664"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="3f42b-102">\<add> 項目的 \<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="3f42b-102">\<add> of \<declaredTypes> Element</span></span>

<span data-ttu-id="3f42b-103">在還原序列化期間，新增 <xref:System.Runtime.Serialization.DataContractSerializer> 所使用的型別。</span><span class="sxs-lookup"><span data-stu-id="3f42b-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="3f42b-104">每個宣告的型別都包含已知型別，這些已知型別將傳回做為宣告型別的欄位或屬性。</span><span class="sxs-lookup"><span data-stu-id="3f42b-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="3f42b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3f42b-105">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f42b-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3f42b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3f42b-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3f42b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f42b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3f42b-108">Attributes</span></span>  
  
|<span data-ttu-id="3f42b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="3f42b-109">Attribute</span></span>|<span data-ttu-id="3f42b-110">描述</span><span class="sxs-lookup"><span data-stu-id="3f42b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f42b-111">type</span><span class="sxs-lookup"><span data-stu-id="3f42b-111">type</span></span>|<span data-ttu-id="3f42b-112">必要的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="3f42b-112">Required string attribute.</span></span><br /><br /> <span data-ttu-id="3f42b-113">指定型別名稱 (包括命名空間)、組件名稱、版本號碼、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="3f42b-113">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f42b-114">子元素</span><span class="sxs-lookup"><span data-stu-id="3f42b-114">Child Elements</span></span>  
  
|<span data-ttu-id="3f42b-115">項目</span><span class="sxs-lookup"><span data-stu-id="3f42b-115">Element</span></span>|<span data-ttu-id="3f42b-116">描述</span><span class="sxs-lookup"><span data-stu-id="3f42b-116">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="3f42b-117">為要加入的宣告型別指定已知型別。</span><span class="sxs-lookup"><span data-stu-id="3f42b-117">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="3f42b-118">如果宣告的型別是泛型型別，您也必須將參數項目加入至 `<knownType>` 項目，以指定要用於傳回已知型別的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="3f42b-118">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f42b-119">父項目</span><span class="sxs-lookup"><span data-stu-id="3f42b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3f42b-120">項目</span><span class="sxs-lookup"><span data-stu-id="3f42b-120">Element</span></span>|<span data-ttu-id="3f42b-121">描述</span><span class="sxs-lookup"><span data-stu-id="3f42b-121">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="3f42b-122">包含還原序列化期間 <xref:System.Runtime.Serialization.DataContractSerializer> 所需已知型別的型別。</span><span class="sxs-lookup"><span data-stu-id="3f42b-122">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f42b-123">備註</span><span class="sxs-lookup"><span data-stu-id="3f42b-123">Remarks</span></span>  

 <span data-ttu-id="3f42b-124">如需已知類型的詳細資訊，請參閱 [資料合約已知](../../../wcf/feature-details/data-contract-known-types.md) 型別和 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="3f42b-124">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="3f42b-125">如需 [\<dataContractSerializer>](datacontractserializer-element.md) 使用這個元素的範例，請參閱。</span><span class="sxs-lookup"><span data-stu-id="3f42b-125">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f42b-126">如果您將 <xref:System.Object> 型別加入做為 `<declaredType>`，則會擲回 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="3f42b-126">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="3f42b-127">這是因為 <xref:System.Object> 型別無法用來做為組態中的宣告型別。</span><span class="sxs-lookup"><span data-stu-id="3f42b-127">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f42b-128">範例</span><span class="sxs-lookup"><span data-stu-id="3f42b-128">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f42b-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f42b-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="3f42b-130">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="3f42b-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="3f42b-131">\<add> 次數 \<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="3f42b-131">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
