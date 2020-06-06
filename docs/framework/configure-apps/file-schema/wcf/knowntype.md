---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 61f51b2ecd572ba254317a01e0f514503c7cc9e4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397878"
---
# \<knownType>
<span data-ttu-id="1ade9-101">指定還原序列化期間要由 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的型別。</span><span class="sxs-lookup"><span data-stu-id="1ade9-101">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="1ade9-102">項目會指定由「宣告型別」的欄位或屬性所傳回的「已知型別」。</span><span class="sxs-lookup"><span data-stu-id="1ade9-102">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="1ade9-103">如需詳細資訊，請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1ade9-103">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**  
  
## <a name="syntax"></a><span data-ttu-id="1ade9-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ade9-104">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="1ade9-105">類型</span><span class="sxs-lookup"><span data-stu-id="1ade9-105">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ade9-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1ade9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="1ade9-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1ade9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ade9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="1ade9-108">Attributes</span></span>  
  
|<span data-ttu-id="1ade9-109">屬性</span><span class="sxs-lookup"><span data-stu-id="1ade9-109">Attribute</span></span>|<span data-ttu-id="1ade9-110">描述</span><span class="sxs-lookup"><span data-stu-id="1ade9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ade9-111">type</span><span class="sxs-lookup"><span data-stu-id="1ade9-111">type</span></span>|<span data-ttu-id="1ade9-112">指定型別 (包括命名空間)、組件名稱、版本、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="1ade9-112">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ade9-113">子元素</span><span class="sxs-lookup"><span data-stu-id="1ade9-113">Child Elements</span></span>  
  
|<span data-ttu-id="1ade9-114">元素</span><span class="sxs-lookup"><span data-stu-id="1ade9-114">Element</span></span>|<span data-ttu-id="1ade9-115">描述</span><span class="sxs-lookup"><span data-stu-id="1ade9-115">Description</span></span>|  
|-------------|-----------------|  
|[\<parameter>](parameter.md)|<span data-ttu-id="1ade9-116">指定當宣告型別為泛型型別時的參數索引。</span><span class="sxs-lookup"><span data-stu-id="1ade9-116">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ade9-117">父項目</span><span class="sxs-lookup"><span data-stu-id="1ade9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1ade9-118">元素</span><span class="sxs-lookup"><span data-stu-id="1ade9-118">Element</span></span>|<span data-ttu-id="1ade9-119">描述</span><span class="sxs-lookup"><span data-stu-id="1ade9-119">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="1ade9-120">將宣告型別新增至宣告型別集合中。</span><span class="sxs-lookup"><span data-stu-id="1ade9-120">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ade9-121">備註</span><span class="sxs-lookup"><span data-stu-id="1ade9-121">Remarks</span></span>  
 <span data-ttu-id="1ade9-122">如需已知類型的詳細資訊，請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)和 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="1ade9-122">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="1ade9-123">如需 [\<dataContractSerializer>](datacontractserializer-element.md) 使用此元素的範例，請參閱。</span><span class="sxs-lookup"><span data-stu-id="1ade9-123">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ade9-124">範例</span><span class="sxs-lookup"><span data-stu-id="1ade9-124">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1ade9-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ade9-125">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="1ade9-126">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="1ade9-126">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
