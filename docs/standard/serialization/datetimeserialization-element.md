---
title: <dateTimeSerialization> 項目
description: 本文描述專案 <dateTimeSerialization> ，這個元素會決定 DateTime 物件的序列化模式。
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 652a88e25f59cd905e47ef71351e47e67f375286
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375818"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="0da4e-103">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="0da4e-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="0da4e-104">判斷 <xref:System.DateTime> 物件的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="0da4e-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="0da4e-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0da4e-105">\<configuration></span></span>  
<span data-ttu-id="0da4e-106">\<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="0da4e-106">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0da4e-107">語法</span><span class="sxs-lookup"><span data-stu-id="0da4e-107">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0da4e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0da4e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0da4e-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0da4e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0da4e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0da4e-110">Attributes</span></span>  
  
|<span data-ttu-id="0da4e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0da4e-111">Attributes</span></span>|<span data-ttu-id="0da4e-112">描述</span><span class="sxs-lookup"><span data-stu-id="0da4e-112">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="0da4e-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0da4e-113">Optional.</span></span> <span data-ttu-id="0da4e-114">指定序列化模式。</span><span class="sxs-lookup"><span data-stu-id="0da4e-114">Specifies the serialization mode.</span></span> <span data-ttu-id="0da4e-115">設定為其中一個 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> 值。</span><span class="sxs-lookup"><span data-stu-id="0da4e-115">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="0da4e-116">預設值為 **RoundTrip**。</span><span class="sxs-lookup"><span data-stu-id="0da4e-116">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0da4e-117">子元素</span><span class="sxs-lookup"><span data-stu-id="0da4e-117">Child Elements</span></span>  
 <span data-ttu-id="0da4e-118">無。</span><span class="sxs-lookup"><span data-stu-id="0da4e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0da4e-119">父項目</span><span class="sxs-lookup"><span data-stu-id="0da4e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0da4e-120">元素</span><span class="sxs-lookup"><span data-stu-id="0da4e-120">Element</span></span>|<span data-ttu-id="0da4e-121">描述</span><span class="sxs-lookup"><span data-stu-id="0da4e-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0da4e-122">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="0da4e-122">system.xml.serialization</span></span>|<span data-ttu-id="0da4e-123">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="0da4e-123">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0da4e-124">備註</span><span class="sxs-lookup"><span data-stu-id="0da4e-124">Remarks</span></span>  
 <span data-ttu-id="0da4e-125">在版本1.0、1.1、2.0 和更新版本的 .NET Framework 中，當這個屬性設定為**local**時， <xref:System.DateTime> 物件一律會格式化為當地時間。</span><span class="sxs-lookup"><span data-stu-id="0da4e-125">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="0da4e-126">也就是說，本地時區資訊一定會包含在序列化資料中。</span><span class="sxs-lookup"><span data-stu-id="0da4e-126">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="0da4e-127">將此屬性設定為 **Local**，確保與舊版 .NET Framework 的相容性。</span><span class="sxs-lookup"><span data-stu-id="0da4e-127">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="0da4e-128">在版本2.0 和更新版本的 .NET Framework 中，將此屬性設定為 [**往返**]， <xref:System.DateTime> 會檢查物件以判斷它們是在當地、UTC 還是未指定的時區。</span><span class="sxs-lookup"><span data-stu-id="0da4e-128">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="0da4e-129">然後 <xref:System.DateTime> 物件會以保留此資訊的方式序列化。</span><span class="sxs-lookup"><span data-stu-id="0da4e-129">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="0da4e-130">這是預設行為，並建議所有新的應用程式不要與舊版 Framework 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="0da4e-130">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da4e-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="0da4e-131">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="0da4e-132">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="0da4e-132">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="0da4e-133">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="0da4e-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="0da4e-134">\<新增 schemaImporterExtensions>的> 元素 \<</span><span class="sxs-lookup"><span data-stu-id="0da4e-134">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="0da4e-135">\<> 元素的 system.object 序列化</span><span class="sxs-lookup"><span data-stu-id="0da4e-135">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
