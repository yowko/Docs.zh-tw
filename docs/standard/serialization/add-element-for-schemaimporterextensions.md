---
title: <schemaImporterExtensions> 的 <add> 項目
description: <add>元素會加入 XmlSchemaImporter 類別用來將 XSD 類型對應至 .NET Framework 類型的類型。
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 401d1ba9cc2f97e93d7851f96f73b552e6ed6356
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378471"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="f9f8c-103">\<新增 schemaImporterExtensions> 的> 元素 \<</span><span class="sxs-lookup"><span data-stu-id="f9f8c-103">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="f9f8c-104">加入 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的型別，將 XSD 型別對應至 .NET Framework 型別。</span><span class="sxs-lookup"><span data-stu-id="f9f8c-104">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="f9f8c-105">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f9f8c-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="f9f8c-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f9f8c-106">\<configuration></span></span>  
<span data-ttu-id="f9f8c-107">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="f9f8c-107">\<system.xml.serialization></span></span>  
<span data-ttu-id="f9f8c-108">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="f9f8c-108">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="f9f8c-109">\<add></span><span class="sxs-lookup"><span data-stu-id="f9f8c-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9f8c-110">語法</span><span class="sxs-lookup"><span data-stu-id="f9f8c-110">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9f8c-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f9f8c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f9f8c-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f9f8c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9f8c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f9f8c-113">Attributes</span></span>  
  
|<span data-ttu-id="f9f8c-114">屬性</span><span class="sxs-lookup"><span data-stu-id="f9f8c-114">Attribute</span></span>|<span data-ttu-id="f9f8c-115">描述</span><span class="sxs-lookup"><span data-stu-id="f9f8c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9f8c-116">**name**</span><span class="sxs-lookup"><span data-stu-id="f9f8c-116">**name**</span></span>|<span data-ttu-id="f9f8c-117">用來尋找執行個體的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="f9f8c-117">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="f9f8c-118">**type**</span><span class="sxs-lookup"><span data-stu-id="f9f8c-118">**type**</span></span>|<span data-ttu-id="f9f8c-119">必要。</span><span class="sxs-lookup"><span data-stu-id="f9f8c-119">Required.</span></span> <span data-ttu-id="f9f8c-120">指定要加入的結構描述擴充功能類別。</span><span class="sxs-lookup"><span data-stu-id="f9f8c-120">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="f9f8c-121">**type** 屬性值必須在同一行，且包括完整類型名稱。</span><span class="sxs-lookup"><span data-stu-id="f9f8c-121">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="f9f8c-122">當組件置於全域組件快取 (GAC) 中時，也必須包含簽署組件的版本、文化特性和公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f9f8c-122">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9f8c-123">子元素</span><span class="sxs-lookup"><span data-stu-id="f9f8c-123">Child Elements</span></span>  
 <span data-ttu-id="f9f8c-124">無。</span><span class="sxs-lookup"><span data-stu-id="f9f8c-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9f8c-125">父項目</span><span class="sxs-lookup"><span data-stu-id="f9f8c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f9f8c-126">元素</span><span class="sxs-lookup"><span data-stu-id="f9f8c-126">Element</span></span>|<span data-ttu-id="f9f8c-127">描述</span><span class="sxs-lookup"><span data-stu-id="f9f8c-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9f8c-128">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="f9f8c-128">\<schemaImporterExtensions></span></span>|<span data-ttu-id="f9f8c-129">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的型別。</span><span class="sxs-lookup"><span data-stu-id="f9f8c-129">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f9f8c-130">範例</span><span class="sxs-lookup"><span data-stu-id="f9f8c-130">Example</span></span>  
 <span data-ttu-id="f9f8c-131">下列程式碼範例會加入 XmlSchemaImporter 在對應型別時可使用的副檔名類型。</span><span class="sxs-lookup"><span data-stu-id="f9f8c-131">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <schemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a" />
    </schemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9f8c-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="f9f8c-132">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="f9f8c-133">\<> 元素的 system.object 序列化</span><span class="sxs-lookup"><span data-stu-id="f9f8c-133">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="f9f8c-134">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="f9f8c-134">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
