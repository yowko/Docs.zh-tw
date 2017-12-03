---
title: "&lt;system.xml.serialization&gt; 元素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d70879d5e0a579af7b5c507910d4dcb19ddee52
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemxmlserializationgt-element"></a><span data-ttu-id="3d68f-102">&lt;system.xml.serialization&gt; 元素</span><span class="sxs-lookup"><span data-stu-id="3d68f-102">&lt;system.xml.serialization&gt; Element</span></span>
<span data-ttu-id="3d68f-103">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="3d68f-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="3d68f-104">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3d68f-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="3d68f-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3d68f-105">\<configuration></span></span>  
<span data-ttu-id="3d68f-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="3d68f-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d68f-107">語法</span><span class="sxs-lookup"><span data-stu-id="3d68f-107">Syntax</span></span>  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d68f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3d68f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3d68f-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3d68f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d68f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3d68f-110">Attributes</span></span>  
 <span data-ttu-id="3d68f-111">無。</span><span class="sxs-lookup"><span data-stu-id="3d68f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3d68f-112">子項目</span><span class="sxs-lookup"><span data-stu-id="3d68f-112">Child Elements</span></span>  
  
|<span data-ttu-id="3d68f-113">項目</span><span class="sxs-lookup"><span data-stu-id="3d68f-113">Element</span></span>|<span data-ttu-id="3d68f-114">說明</span><span class="sxs-lookup"><span data-stu-id="3d68f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d68f-115">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="3d68f-115">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="3d68f-116">判斷 <xref:System.DateTime> 物件的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="3d68f-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|  
|[<span data-ttu-id="3d68f-117">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="3d68f-117">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="3d68f-118">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 用來對應 XSD 型別至 .NET Framework 型別的型別。</span><span class="sxs-lookup"><span data-stu-id="3d68f-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d68f-119">父項目</span><span class="sxs-lookup"><span data-stu-id="3d68f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3d68f-120">項目</span><span class="sxs-lookup"><span data-stu-id="3d68f-120">Element</span></span>|<span data-ttu-id="3d68f-121">說明</span><span class="sxs-lookup"><span data-stu-id="3d68f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d68f-122">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="3d68f-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="3d68f-123">Common Language Runtime 與 .NET Framework 應用程式使用的所有組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="3d68f-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3d68f-124">範例</span><span class="sxs-lookup"><span data-stu-id="3d68f-124">Example</span></span>  
 <span data-ttu-id="3d68f-125">下列程式碼範例描述如何指定 <xref:System.DateTime> 物件的序列化模式，以及在對應 XSD 型別至 .NET Framework 型別時 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的新增型別。</span><span class="sxs-lookup"><span data-stu-id="3d68f-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
    <dateTimeSerialization mode = "Local" />  
    <schemaImporterExtensions>  
        <add   
        name = "MobileCapabilities"   
        type = "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neuutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.sxml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d68f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d68f-126">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="3d68f-127">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="3d68f-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="3d68f-128">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="3d68f-128">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="3d68f-129">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="3d68f-129">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [<span data-ttu-id="3d68f-130">\<xmlSchemaImporterExtensions> 的 \<add> 項目</span><span class="sxs-lookup"><span data-stu-id="3d68f-130">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)
