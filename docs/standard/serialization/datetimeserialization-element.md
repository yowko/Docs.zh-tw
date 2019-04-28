---
title: <dateTimeSerialization> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: af0d8eeb36e023b4d38f9ad5831de3d392a487fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922547"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="2f225-102">\<dateTimeSerialization > 項目</span><span class="sxs-lookup"><span data-stu-id="2f225-102">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="2f225-103">判斷 <xref:System.DateTime> 物件的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="2f225-103">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="2f225-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2f225-104">\<configuration></span></span>  
<span data-ttu-id="2f225-105">\<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="2f225-105">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f225-106">語法</span><span class="sxs-lookup"><span data-stu-id="2f225-106">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f225-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2f225-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2f225-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2f225-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f225-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2f225-109">Attributes</span></span>  
  
|<span data-ttu-id="2f225-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2f225-110">Attributes</span></span>|<span data-ttu-id="2f225-111">描述</span><span class="sxs-lookup"><span data-stu-id="2f225-111">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="2f225-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2f225-112">Optional.</span></span> <span data-ttu-id="2f225-113">指定序列化模式。</span><span class="sxs-lookup"><span data-stu-id="2f225-113">Specifies the serialization mode.</span></span> <span data-ttu-id="2f225-114">設定為其中一個 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> 值。</span><span class="sxs-lookup"><span data-stu-id="2f225-114">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="2f225-115">預設值為 **RoundTrip**。</span><span class="sxs-lookup"><span data-stu-id="2f225-115">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f225-116">子元素</span><span class="sxs-lookup"><span data-stu-id="2f225-116">Child Elements</span></span>  
 <span data-ttu-id="2f225-117">無。</span><span class="sxs-lookup"><span data-stu-id="2f225-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f225-118">父項目</span><span class="sxs-lookup"><span data-stu-id="2f225-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2f225-119">項目</span><span class="sxs-lookup"><span data-stu-id="2f225-119">Element</span></span>|<span data-ttu-id="2f225-120">描述</span><span class="sxs-lookup"><span data-stu-id="2f225-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f225-121">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="2f225-121">system.xml.serialization</span></span>|<span data-ttu-id="2f225-122">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="2f225-122">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f225-123">備註</span><span class="sxs-lookup"><span data-stu-id="2f225-123">Remarks</span></span>  
 <span data-ttu-id="2f225-124">在 .NET Framework 的 1.0、1.1 和 2.0 版以及更新版本中，將此屬性設定為 **Local** 時，<xref:System.DateTime> 物件一定會格式化為當地時間。</span><span class="sxs-lookup"><span data-stu-id="2f225-124">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="2f225-125">也就是說，本地時區資訊一定會包含在序列化資料中。</span><span class="sxs-lookup"><span data-stu-id="2f225-125">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="2f225-126">將此屬性設定為 **Local**，確保與舊版 .NET Framework 的相容性。</span><span class="sxs-lookup"><span data-stu-id="2f225-126">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="2f225-127">在將此屬性設定為 **Roundtrip** 的 .NET Framework 2.0 版及更新版本中，會檢查 <xref:System.DateTime> 物件以判斷其位於當地時區、UTC 或非特定時區。</span><span class="sxs-lookup"><span data-stu-id="2f225-127">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="2f225-128">然後 <xref:System.DateTime> 物件會以保留此資訊的方式序列化。</span><span class="sxs-lookup"><span data-stu-id="2f225-128">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="2f225-129">這是預設行為，並建議所有新的應用程式不要與舊版 Framework 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="2f225-129">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f225-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f225-130">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="2f225-131">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="2f225-131">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="2f225-132">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="2f225-132">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="2f225-133">\<新增 > 項目\<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="2f225-133">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="2f225-134">\<system.xml.serialization> 項目</span><span class="sxs-lookup"><span data-stu-id="2f225-134">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
