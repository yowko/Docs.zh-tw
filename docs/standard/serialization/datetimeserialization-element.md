---
title: <dateTimeSerialization> 項目
description: 本文描述專案 <dateTimeSerialization> ，這個元素會決定 DateTime 物件的序列化模式。
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: a2684ab72c1fb109d711e333e01836d3399caf86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289638"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="390a9-103">\<dateTimeSerialization> 項目</span><span class="sxs-lookup"><span data-stu-id="390a9-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="390a9-104">判斷 <xref:System.DateTime> 物件的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="390a9-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="390a9-105">語法</span><span class="sxs-lookup"><span data-stu-id="390a9-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="390a9-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="390a9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="390a9-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="390a9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="390a9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="390a9-108">Attributes</span></span>  
  
|<span data-ttu-id="390a9-109">屬性</span><span class="sxs-lookup"><span data-stu-id="390a9-109">Attributes</span></span>|<span data-ttu-id="390a9-110">描述</span><span class="sxs-lookup"><span data-stu-id="390a9-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="390a9-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="390a9-111">Optional.</span></span> <span data-ttu-id="390a9-112">指定序列化模式。</span><span class="sxs-lookup"><span data-stu-id="390a9-112">Specifies the serialization mode.</span></span> <span data-ttu-id="390a9-113">設定為其中一個 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> 值。</span><span class="sxs-lookup"><span data-stu-id="390a9-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="390a9-114">預設值為 **RoundTrip**。</span><span class="sxs-lookup"><span data-stu-id="390a9-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="390a9-115">子元素</span><span class="sxs-lookup"><span data-stu-id="390a9-115">Child Elements</span></span>  
 <span data-ttu-id="390a9-116">無。</span><span class="sxs-lookup"><span data-stu-id="390a9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="390a9-117">父項目</span><span class="sxs-lookup"><span data-stu-id="390a9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="390a9-118">元素</span><span class="sxs-lookup"><span data-stu-id="390a9-118">Element</span></span>|<span data-ttu-id="390a9-119">描述</span><span class="sxs-lookup"><span data-stu-id="390a9-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="390a9-120">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="390a9-120">system.xml.serialization</span></span>|<span data-ttu-id="390a9-121">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="390a9-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="390a9-122">備註</span><span class="sxs-lookup"><span data-stu-id="390a9-122">Remarks</span></span>  
 <span data-ttu-id="390a9-123">在版本1.0、1.1、2.0 和更新版本的 .NET Framework 中，當這個屬性設定為**local**時， <xref:System.DateTime> 物件一律會格式化為當地時間。</span><span class="sxs-lookup"><span data-stu-id="390a9-123">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="390a9-124">也就是說，本地時區資訊一定會包含在序列化資料中。</span><span class="sxs-lookup"><span data-stu-id="390a9-124">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="390a9-125">將此屬性設定為 **Local**，確保與舊版 .NET Framework 的相容性。</span><span class="sxs-lookup"><span data-stu-id="390a9-125">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="390a9-126">在版本2.0 和更新版本的 .NET Framework 中，將此屬性設定為 [**往返**]， <xref:System.DateTime> 會檢查物件以判斷它們是在當地、UTC 還是未指定的時區。</span><span class="sxs-lookup"><span data-stu-id="390a9-126">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="390a9-127">然後 <xref:System.DateTime> 物件會以保留此資訊的方式序列化。</span><span class="sxs-lookup"><span data-stu-id="390a9-127">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="390a9-128">這是預設行為，並建議所有新的應用程式不要與舊版 Framework 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="390a9-128">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="390a9-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="390a9-129">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="390a9-130">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="390a9-130">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="390a9-131">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="390a9-131">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="390a9-132">\<add>的元素\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="390a9-132">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="390a9-133">\<system.xml.serialization>元素</span><span class="sxs-lookup"><span data-stu-id="390a9-133">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
