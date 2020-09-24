---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 6bb6a419d863172951d82a67de044cb8cfc30f49
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183789"
---
# \<knownType>

<span data-ttu-id="466b5-101">指定還原序列化期間要由 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的型別。</span><span class="sxs-lookup"><span data-stu-id="466b5-101">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="466b5-102">項目會指定由「宣告型別」的欄位或屬性所傳回的「已知型別」。</span><span class="sxs-lookup"><span data-stu-id="466b5-102">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="466b5-103">如需詳細資訊，請參閱 [資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="466b5-103">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**  
  
## <a name="syntax"></a><span data-ttu-id="466b5-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="466b5-104">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="466b5-105">類型</span><span class="sxs-lookup"><span data-stu-id="466b5-105">Type</span></span>  

 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="466b5-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="466b5-106">Attributes and Elements</span></span>  

 <span data-ttu-id="466b5-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="466b5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="466b5-108">屬性</span><span class="sxs-lookup"><span data-stu-id="466b5-108">Attributes</span></span>  
  
|<span data-ttu-id="466b5-109">屬性</span><span class="sxs-lookup"><span data-stu-id="466b5-109">Attribute</span></span>|<span data-ttu-id="466b5-110">描述</span><span class="sxs-lookup"><span data-stu-id="466b5-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="466b5-111">type</span><span class="sxs-lookup"><span data-stu-id="466b5-111">type</span></span>|<span data-ttu-id="466b5-112">指定型別 (包括命名空間)、組件名稱、版本、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="466b5-112">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="466b5-113">子元素</span><span class="sxs-lookup"><span data-stu-id="466b5-113">Child Elements</span></span>  
  
|<span data-ttu-id="466b5-114">項目</span><span class="sxs-lookup"><span data-stu-id="466b5-114">Element</span></span>|<span data-ttu-id="466b5-115">描述</span><span class="sxs-lookup"><span data-stu-id="466b5-115">Description</span></span>|  
|-------------|-----------------|  
|[\<parameter>](parameter.md)|<span data-ttu-id="466b5-116">指定當宣告型別為泛型型別時的參數索引。</span><span class="sxs-lookup"><span data-stu-id="466b5-116">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="466b5-117">父項目</span><span class="sxs-lookup"><span data-stu-id="466b5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="466b5-118">項目</span><span class="sxs-lookup"><span data-stu-id="466b5-118">Element</span></span>|<span data-ttu-id="466b5-119">描述</span><span class="sxs-lookup"><span data-stu-id="466b5-119">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="466b5-120">將宣告型別新增至宣告型別集合中。</span><span class="sxs-lookup"><span data-stu-id="466b5-120">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="466b5-121">備註</span><span class="sxs-lookup"><span data-stu-id="466b5-121">Remarks</span></span>  

 <span data-ttu-id="466b5-122">如需已知類型的詳細資訊，請參閱 [資料合約已知](../../../wcf/feature-details/data-contract-known-types.md) 型別和 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="466b5-122">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="466b5-123">如需 [\<dataContractSerializer>](datacontractserializer-element.md) 使用這個元素的範例，請參閱。</span><span class="sxs-lookup"><span data-stu-id="466b5-123">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="466b5-124">範例</span><span class="sxs-lookup"><span data-stu-id="466b5-124">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="466b5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="466b5-125">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="466b5-126">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="466b5-126">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
