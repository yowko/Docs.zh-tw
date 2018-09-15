---
title: '&lt;xmlSerializer&gt; 元素'
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 2770b82f71f3c4b43df4c44f75248e5392c528c2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45624948"
---
# <a name="ltxmlserializergt-element"></a><span data-ttu-id="a655d-102">&lt;xmlSerializer&gt; 元素</span><span class="sxs-lookup"><span data-stu-id="a655d-102">&lt;xmlSerializer&gt; Element</span></span>
<span data-ttu-id="a655d-103">指定是否已完成 <xref:System.Xml.Serialization.XmlSerializer> 進度的其他檢查。</span><span class="sxs-lookup"><span data-stu-id="a655d-103">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="a655d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a655d-104">\<configuration></span></span>  
<span data-ttu-id="a655d-105">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="a655d-105">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a655d-106">語法</span><span class="sxs-lookup"><span data-stu-id="a655d-106">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a655d-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a655d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a655d-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a655d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a655d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a655d-109">Attributes</span></span>  
  
|<span data-ttu-id="a655d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a655d-110">Attribute</span></span>|<span data-ttu-id="a655d-111">描述</span><span class="sxs-lookup"><span data-stu-id="a655d-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a655d-112">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="a655d-112">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="a655d-113">指定是否已檢查 <xref:System.Xml.Serialization.XmlSerializer>的進度。</span><span class="sxs-lookup"><span data-stu-id="a655d-113">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="a655d-114">設定屬性為 "true" 或 "false"。</span><span class="sxs-lookup"><span data-stu-id="a655d-114">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="a655d-115">預設為 "true"。</span><span class="sxs-lookup"><span data-stu-id="a655d-115">The default is "true".</span></span>|  
|<span data-ttu-id="a655d-116">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="a655d-116">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="a655d-117">指定 <xref:System.Xml.Serialization.XmlSerializer> 是否使用舊版序列化產生作業，此作業會將 C# 程式碼寫入至檔案並編譯成組件，藉此產成組件。</span><span class="sxs-lookup"><span data-stu-id="a655d-117">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="a655d-118">預設值為 **false**。</span><span class="sxs-lookup"><span data-stu-id="a655d-118">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a655d-119">子元素</span><span class="sxs-lookup"><span data-stu-id="a655d-119">Child Elements</span></span>  
 <span data-ttu-id="a655d-120">無。</span><span class="sxs-lookup"><span data-stu-id="a655d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a655d-121">父項目</span><span class="sxs-lookup"><span data-stu-id="a655d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a655d-122">項目</span><span class="sxs-lookup"><span data-stu-id="a655d-122">Element</span></span>|<span data-ttu-id="a655d-123">描述</span><span class="sxs-lookup"><span data-stu-id="a655d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a655d-124">\<system.xml.serialization> 項目</span><span class="sxs-lookup"><span data-stu-id="a655d-124">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="a655d-125">包含 <xref:System.Xml.Serialization.XmlSerializer> 及 <xref:System.Xml.Serialization.XmlSchemaImporter> 類別的組態設定。</span><span class="sxs-lookup"><span data-stu-id="a655d-125">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a655d-126">備註</span><span class="sxs-lookup"><span data-stu-id="a655d-126">Remarks</span></span>  
 <span data-ttu-id="a655d-127">根據預設， <xref:System.Xml.Serialization.XmlSerializer> 提供額外層級的安全性，在還原序列化未受信任的資料時，避免潛在的拒絕服務攻擊。</span><span class="sxs-lookup"><span data-stu-id="a655d-127">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="a655d-128">做法是嘗試在還原序列化期間，偵測無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="a655d-128">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="a655d-129">若偵測到這樣的狀況，將擲回例外狀況並顯示下列訊息：「內部錯誤: 還原序列化無法處理基礎資料流」。</span><span class="sxs-lookup"><span data-stu-id="a655d-129">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="a655d-130">接收到此訊息並不表示正在進行阻絕服務攻擊。</span><span class="sxs-lookup"><span data-stu-id="a655d-130">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="a655d-131">在某些罕見的狀況下，無限迴圈偵測機制產生誤判，使得合法的傳入訊息導致擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a655d-131">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="a655d-132">如果您發現自己特定的應用程式合法訊息，遭到此額外的保護層級拒絕，請將 **checkDeserializeAdvances** 屬性設定為 "false"。</span><span class="sxs-lookup"><span data-stu-id="a655d-132">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="a655d-133">範例</span><span class="sxs-lookup"><span data-stu-id="a655d-133">Example</span></span>  
 <span data-ttu-id="a655d-134">下列程式碼範例將 **checkDeserializeAdvances** 屬性設為 "false"。</span><span class="sxs-lookup"><span data-stu-id="a655d-134">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a655d-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a655d-135">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>  
- [<span data-ttu-id="a655d-136">\<system.xml.serialization> 項目</span><span class="sxs-lookup"><span data-stu-id="a655d-136">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
- [<span data-ttu-id="a655d-137">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="a655d-137">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
