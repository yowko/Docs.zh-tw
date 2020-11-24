---
title: <xmlSerializer> 項目
description: <xmlSerializer>元素會指定是否要執行其他檢查 XmlSerializer 的進度。
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 6f368880c97a21dc3e9593ecb2319d265a1b8932
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676487"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="0f5f3-103">\<xmlSerializer> 項目</span><span class="sxs-lookup"><span data-stu-id="0f5f3-103">\<xmlSerializer> Element</span></span>

<span data-ttu-id="0f5f3-104">指定是否已完成 <xref:System.Xml.Serialization.XmlSerializer> 進度的其他檢查。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-104">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 \<configuration>  
\<system.xml.serialization>  
  
## <a name="syntax"></a><span data-ttu-id="0f5f3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0f5f3-105">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f5f3-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0f5f3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0f5f3-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f5f3-108">屬性</span><span class="sxs-lookup"><span data-stu-id="0f5f3-108">Attributes</span></span>  
  
|<span data-ttu-id="0f5f3-109">屬性</span><span class="sxs-lookup"><span data-stu-id="0f5f3-109">Attribute</span></span>|<span data-ttu-id="0f5f3-110">描述</span><span class="sxs-lookup"><span data-stu-id="0f5f3-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f5f3-111">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="0f5f3-111">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="0f5f3-112">指定是否已檢查 <xref:System.Xml.Serialization.XmlSerializer>的進度。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-112">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="0f5f3-113">設定屬性為 "true" 或 "false"。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-113">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="0f5f3-114">預設為 "true"。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-114">The default is "true".</span></span>|  
|<span data-ttu-id="0f5f3-115">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="0f5f3-115">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="0f5f3-116">指定 <xref:System.Xml.Serialization.XmlSerializer> 是否使用舊版序列化產生作業，此作業會將 C# 程式碼寫入至檔案並編譯成組件，藉此產成組件。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-116">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="0f5f3-117">預設值為 **false**。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-117">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f5f3-118">子元素</span><span class="sxs-lookup"><span data-stu-id="0f5f3-118">Child Elements</span></span>  

 <span data-ttu-id="0f5f3-119">無。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f5f3-120">父項目</span><span class="sxs-lookup"><span data-stu-id="0f5f3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0f5f3-121">元素</span><span class="sxs-lookup"><span data-stu-id="0f5f3-121">Element</span></span>|<span data-ttu-id="0f5f3-122">描述</span><span class="sxs-lookup"><span data-stu-id="0f5f3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f5f3-123">\<system.xml.serialization> 元素</span><span class="sxs-lookup"><span data-stu-id="0f5f3-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="0f5f3-124">包含 <xref:System.Xml.Serialization.XmlSerializer> 及 <xref:System.Xml.Serialization.XmlSchemaImporter> 類別的組態設定。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-124">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f5f3-125">備註</span><span class="sxs-lookup"><span data-stu-id="0f5f3-125">Remarks</span></span>  

 <span data-ttu-id="0f5f3-126">根據預設， <xref:System.Xml.Serialization.XmlSerializer> 提供額外層級的安全性，在還原序列化未受信任的資料時，避免潛在的拒絕服務攻擊。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-126">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="0f5f3-127">做法是嘗試在還原序列化期間，偵測無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-127">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="0f5f3-128">若偵測到這樣的狀況，將擲回例外狀況並顯示下列訊息：「內部錯誤: 還原序列化無法處理基礎資料流」。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-128">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="0f5f3-129">接收到此訊息並不表示正在進行阻絕服務攻擊。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-129">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="0f5f3-130">在某些罕見的狀況下，無限迴圈偵測機制產生誤判，使得合法的傳入訊息導致擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-130">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="0f5f3-131">如果您發現自己特定的應用程式合法訊息，遭到此額外的保護層級拒絕，請將 **checkDeserializeAdvances** 屬性設定為 "false"。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-131">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f5f3-132">範例</span><span class="sxs-lookup"><span data-stu-id="0f5f3-132">Example</span></span>  

 <span data-ttu-id="0f5f3-133">下列程式碼範例將 **checkDeserializeAdvances** 屬性設為 "false"。</span><span class="sxs-lookup"><span data-stu-id="0f5f3-133">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f5f3-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f5f3-134">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="0f5f3-135">\<system.xml.serialization> 元素</span><span class="sxs-lookup"><span data-stu-id="0f5f3-135">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
- [<span data-ttu-id="0f5f3-136">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="0f5f3-136">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
