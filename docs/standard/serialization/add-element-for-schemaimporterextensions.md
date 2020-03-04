---
title: <add> 的 <schemaImporterExtensions> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 4f47623aa305ae6e98625acc3d199a76e27d2ea5
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159932"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="d1c45-102">\<新增 \<schemaImporterExtensions 的 > 元素 ></span><span class="sxs-lookup"><span data-stu-id="d1c45-102">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="d1c45-103">加入 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的型別，將 XSD 型別對應至 .NET Framework 型別。</span><span class="sxs-lookup"><span data-stu-id="d1c45-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="d1c45-104">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d1c45-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="d1c45-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d1c45-105">\<configuration></span></span>  
<span data-ttu-id="d1c45-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="d1c45-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="d1c45-107">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="d1c45-107">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="d1c45-108">\<add></span><span class="sxs-lookup"><span data-stu-id="d1c45-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1c45-109">語法</span><span class="sxs-lookup"><span data-stu-id="d1c45-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1c45-110">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="d1c45-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d1c45-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d1c45-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1c45-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d1c45-112">Attributes</span></span>  
  
|<span data-ttu-id="d1c45-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d1c45-113">Attribute</span></span>|<span data-ttu-id="d1c45-114">描述</span><span class="sxs-lookup"><span data-stu-id="d1c45-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1c45-115">**name**</span><span class="sxs-lookup"><span data-stu-id="d1c45-115">**name**</span></span>|<span data-ttu-id="d1c45-116">用來尋找執行個體的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="d1c45-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="d1c45-117">**type**</span><span class="sxs-lookup"><span data-stu-id="d1c45-117">**type**</span></span>|<span data-ttu-id="d1c45-118">必要。</span><span class="sxs-lookup"><span data-stu-id="d1c45-118">Required.</span></span> <span data-ttu-id="d1c45-119">指定要加入的結構描述擴充功能類別。</span><span class="sxs-lookup"><span data-stu-id="d1c45-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="d1c45-120">**type** 屬性值必須在同一行，且包括完整類型名稱。</span><span class="sxs-lookup"><span data-stu-id="d1c45-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="d1c45-121">當組件置於全域組件快取 (GAC) 中時，也必須包含簽署組件的版本、文化特性和公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d1c45-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1c45-122">子元素</span><span class="sxs-lookup"><span data-stu-id="d1c45-122">Child Elements</span></span>  
 <span data-ttu-id="d1c45-123">無。</span><span class="sxs-lookup"><span data-stu-id="d1c45-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1c45-124">父項目</span><span class="sxs-lookup"><span data-stu-id="d1c45-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d1c45-125">元素</span><span class="sxs-lookup"><span data-stu-id="d1c45-125">Element</span></span>|<span data-ttu-id="d1c45-126">描述</span><span class="sxs-lookup"><span data-stu-id="d1c45-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1c45-127">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="d1c45-127">\<schemaImporterExtensions></span></span>|<span data-ttu-id="d1c45-128">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的型別。</span><span class="sxs-lookup"><span data-stu-id="d1c45-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d1c45-129">範例</span><span class="sxs-lookup"><span data-stu-id="d1c45-129">Example</span></span>  
 <span data-ttu-id="d1c45-130">下列程式碼範例會加入 XmlSchemaImporter 在對應型別時可使用的副檔名類型。</span><span class="sxs-lookup"><span data-stu-id="d1c45-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d1c45-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1c45-131">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="d1c45-132">\<system.xml.serialization> 項目</span><span class="sxs-lookup"><span data-stu-id="d1c45-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="d1c45-133">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="d1c45-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
