---
title: <schemaImporterExtensions> 的 <add> 項目
description: 專案會 <add> 加入 XmlSchemaImporter 類別用來將 XSD 類型對應至 .net 類型的類型。
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 38d8ebd6e973632b23865ad60e007d9aa21e7da6
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281994"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="eb6a7-103">\<schemaImporterExtensions> 的 \<add> 項目</span><span class="sxs-lookup"><span data-stu-id="eb6a7-103">\<add> Element for \<schemaImporterExtensions></span></span>

<span data-ttu-id="eb6a7-104">加入用來將 <xref:System.Xml.Serialization.XmlSchemaImporter> XSD 類型對應至 .net 類型的類型。</span><span class="sxs-lookup"><span data-stu-id="eb6a7-104">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET types.</span></span> <span data-ttu-id="eb6a7-105">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="eb6a7-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
\<configuration>  
\<system.xml.serialization>  
\<schemaImporterExtensions>  
\<add>  
  
## <a name="syntax"></a><span data-ttu-id="eb6a7-106">語法</span><span class="sxs-lookup"><span data-stu-id="eb6a7-106">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb6a7-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eb6a7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="eb6a7-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="eb6a7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb6a7-109">屬性</span><span class="sxs-lookup"><span data-stu-id="eb6a7-109">Attributes</span></span>  
  
|<span data-ttu-id="eb6a7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="eb6a7-110">Attribute</span></span>|<span data-ttu-id="eb6a7-111">描述</span><span class="sxs-lookup"><span data-stu-id="eb6a7-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb6a7-112">**name**</span><span class="sxs-lookup"><span data-stu-id="eb6a7-112">**name**</span></span>|<span data-ttu-id="eb6a7-113">用來尋找執行個體的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="eb6a7-113">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="eb6a7-114">**type**</span><span class="sxs-lookup"><span data-stu-id="eb6a7-114">**type**</span></span>|<span data-ttu-id="eb6a7-115">必要。</span><span class="sxs-lookup"><span data-stu-id="eb6a7-115">Required.</span></span> <span data-ttu-id="eb6a7-116">指定要加入的結構描述擴充功能類別。</span><span class="sxs-lookup"><span data-stu-id="eb6a7-116">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="eb6a7-117">**type** 屬性值必須在同一行，且包括完整類型名稱。</span><span class="sxs-lookup"><span data-stu-id="eb6a7-117">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="eb6a7-118">當組件置於全域組件快取 (GAC) 中時，也必須包含簽署組件的版本、文化特性和公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="eb6a7-118">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb6a7-119">子元素</span><span class="sxs-lookup"><span data-stu-id="eb6a7-119">Child Elements</span></span>  
 <span data-ttu-id="eb6a7-120">無。</span><span class="sxs-lookup"><span data-stu-id="eb6a7-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb6a7-121">父項目</span><span class="sxs-lookup"><span data-stu-id="eb6a7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="eb6a7-122">項目</span><span class="sxs-lookup"><span data-stu-id="eb6a7-122">Element</span></span>|<span data-ttu-id="eb6a7-123">描述</span><span class="sxs-lookup"><span data-stu-id="eb6a7-123">Description</span></span>|  
|-------------|-----------------|  
|\<schemaImporterExtensions>|<span data-ttu-id="eb6a7-124">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的型別。</span><span class="sxs-lookup"><span data-stu-id="eb6a7-124">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="eb6a7-125">範例</span><span class="sxs-lookup"><span data-stu-id="eb6a7-125">Example</span></span>  
 <span data-ttu-id="eb6a7-126">下列程式碼範例會加入 XmlSchemaImporter 在對應型別時可使用的副檔名類型。</span><span class="sxs-lookup"><span data-stu-id="eb6a7-126">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eb6a7-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb6a7-127">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="eb6a7-128">\<system.xml.serialization> 元素</span><span class="sxs-lookup"><span data-stu-id="eb6a7-128">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
- [<span data-ttu-id="eb6a7-129">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="eb6a7-129">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
