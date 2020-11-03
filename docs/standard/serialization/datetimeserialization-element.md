---
title: <dateTimeSerialization> 項目
description: 本文描述專案 <dateTimeSerialization> ，它會決定 DateTime 物件的序列化模式。
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 90ae911c8942fef7a9e8238921990b0a52a47ca0
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281766"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="c09df-103">\<dateTimeSerialization> 項目</span><span class="sxs-lookup"><span data-stu-id="c09df-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="c09df-104">判斷 <xref:System.DateTime> 物件的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="c09df-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="c09df-105">語法</span><span class="sxs-lookup"><span data-stu-id="c09df-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c09df-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c09df-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c09df-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c09df-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c09df-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c09df-108">Attributes</span></span>  
  
|<span data-ttu-id="c09df-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c09df-109">Attributes</span></span>|<span data-ttu-id="c09df-110">描述</span><span class="sxs-lookup"><span data-stu-id="c09df-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="c09df-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c09df-111">Optional.</span></span> <span data-ttu-id="c09df-112">指定序列化模式。</span><span class="sxs-lookup"><span data-stu-id="c09df-112">Specifies the serialization mode.</span></span> <span data-ttu-id="c09df-113">設定為其中一個 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> 值。</span><span class="sxs-lookup"><span data-stu-id="c09df-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="c09df-114">預設值為 **RoundTrip** 。</span><span class="sxs-lookup"><span data-stu-id="c09df-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c09df-115">子元素</span><span class="sxs-lookup"><span data-stu-id="c09df-115">Child Elements</span></span>  
 <span data-ttu-id="c09df-116">無。</span><span class="sxs-lookup"><span data-stu-id="c09df-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c09df-117">父項目</span><span class="sxs-lookup"><span data-stu-id="c09df-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c09df-118">項目</span><span class="sxs-lookup"><span data-stu-id="c09df-118">Element</span></span>|<span data-ttu-id="c09df-119">描述</span><span class="sxs-lookup"><span data-stu-id="c09df-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c09df-120">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="c09df-120">system.xml.serialization</span></span>|<span data-ttu-id="c09df-121">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="c09df-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c09df-122">備註</span><span class="sxs-lookup"><span data-stu-id="c09df-122">Remarks</span></span>  

<span data-ttu-id="c09df-123">當這個屬性設定為 [ **本機** ] 時， <xref:System.DateTime> 物件一定會格式化為本地時間。</span><span class="sxs-lookup"><span data-stu-id="c09df-123">When this property is set to **Local** , <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="c09df-124">也就是說，本地時區資訊一定會包含在序列化資料中。</span><span class="sxs-lookup"><span data-stu-id="c09df-124">That is, local time zone information is always included with the serialized data.</span></span>
  
<span data-ttu-id="c09df-125">當這個屬性設定為 **往返** 時， <xref:System.DateTime> 會檢查物件以判斷它們是在本機、UTC 或未指定的時區。</span><span class="sxs-lookup"><span data-stu-id="c09df-125">When this property is set to **Roundtrip** , <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="c09df-126">然後 <xref:System.DateTime> 物件會以保留此資訊的方式序列化。</span><span class="sxs-lookup"><span data-stu-id="c09df-126">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="c09df-127">這是預設行為，並建議所有新的應用程式不要與舊版 Framework 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="c09df-127">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c09df-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c09df-128">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="c09df-129">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="c09df-129">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="c09df-130">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="c09df-130">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="c09df-131">\<add> 的元素 \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="c09df-131">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="c09df-132">\<system.xml.serialization> 元素</span><span class="sxs-lookup"><span data-stu-id="c09df-132">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
