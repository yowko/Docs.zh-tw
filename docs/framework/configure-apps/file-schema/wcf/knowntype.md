---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 61f51b2ecd572ba254317a01e0f514503c7cc9e4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397878"
---
# <a name="knowntype"></a><span data-ttu-id="16adb-101">\<knownType></span><span class="sxs-lookup"><span data-stu-id="16adb-101">\<knownType></span></span>
<span data-ttu-id="16adb-102">指定還原序列化期間要由 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的型別。</span><span class="sxs-lookup"><span data-stu-id="16adb-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="16adb-103">項目會指定由「宣告型別」的欄位或屬性所傳回的「已知型別」。</span><span class="sxs-lookup"><span data-stu-id="16adb-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="16adb-104">如需詳細資訊，請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="16adb-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
<span data-ttu-id="16adb-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="16adb-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="16adb-106">&nbsp;&nbsp;[ **\<> 的序列化**](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="16adb-106">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="16adb-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dataContractSerializer >** ](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="16adb-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="16adb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="16adb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="16adb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<新增 >** ](add-of-declaredtypes-element.md)</span><span class="sxs-lookup"><span data-stu-id="16adb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)</span></span>\
<span data-ttu-id="16adb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<knownType >**</span><span class="sxs-lookup"><span data-stu-id="16adb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16adb-111">語法</span><span class="sxs-lookup"><span data-stu-id="16adb-111">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="16adb-112">類型</span><span class="sxs-lookup"><span data-stu-id="16adb-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16adb-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="16adb-113">Attributes and Elements</span></span>  
 <span data-ttu-id="16adb-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="16adb-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16adb-115">屬性</span><span class="sxs-lookup"><span data-stu-id="16adb-115">Attributes</span></span>  
  
|<span data-ttu-id="16adb-116">屬性</span><span class="sxs-lookup"><span data-stu-id="16adb-116">Attribute</span></span>|<span data-ttu-id="16adb-117">說明</span><span class="sxs-lookup"><span data-stu-id="16adb-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16adb-118">型別</span><span class="sxs-lookup"><span data-stu-id="16adb-118">type</span></span>|<span data-ttu-id="16adb-119">指定型別 (包括命名空間)、組件名稱、版本、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="16adb-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16adb-120">子元素</span><span class="sxs-lookup"><span data-stu-id="16adb-120">Child Elements</span></span>  
  
|<span data-ttu-id="16adb-121">項目</span><span class="sxs-lookup"><span data-stu-id="16adb-121">Element</span></span>|<span data-ttu-id="16adb-122">描述</span><span class="sxs-lookup"><span data-stu-id="16adb-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16adb-123">\<parameter></span><span class="sxs-lookup"><span data-stu-id="16adb-123">\<parameter></span></span>](parameter.md)|<span data-ttu-id="16adb-124">指定當宣告型別為泛型型別時的參數索引。</span><span class="sxs-lookup"><span data-stu-id="16adb-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="16adb-125">父項目</span><span class="sxs-lookup"><span data-stu-id="16adb-125">Parent Elements</span></span>  
  
|<span data-ttu-id="16adb-126">項目</span><span class="sxs-lookup"><span data-stu-id="16adb-126">Element</span></span>|<span data-ttu-id="16adb-127">說明</span><span class="sxs-lookup"><span data-stu-id="16adb-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16adb-128">\<add></span><span class="sxs-lookup"><span data-stu-id="16adb-128">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="16adb-129">將宣告型別新增至宣告型別集合中。</span><span class="sxs-lookup"><span data-stu-id="16adb-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16adb-130">備註</span><span class="sxs-lookup"><span data-stu-id="16adb-130">Remarks</span></span>  
 <span data-ttu-id="16adb-131">如需已知類型的詳細資訊，請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="16adb-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="16adb-132">如需使用此元素的範例，請參閱[ dataContractSerializer>。\< ](datacontractserializer-element.md)</span><span class="sxs-lookup"><span data-stu-id="16adb-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16adb-133">範例</span><span class="sxs-lookup"><span data-stu-id="16adb-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16adb-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16adb-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="16adb-135">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="16adb-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="16adb-136">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="16adb-136">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="16adb-137">\<add></span><span class="sxs-lookup"><span data-stu-id="16adb-137">\<add></span></span>](add-of-declaredtypes-element.md)
