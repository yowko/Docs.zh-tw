---
title: "&lt;mailSettings&gt;項目 （網路設定）"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 5ae9ecdfa9cccb7c70c153153b921151aad50e7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="116fa-102">&lt;mailSettings&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="116fa-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="116fa-103">設定郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="116fa-103">Configures mail sending options.</span></span>  

<span data-ttu-id="116fa-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="116fa-104">\<configuration></span></span>  
<span data-ttu-id="116fa-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="116fa-105">\<system.net></span></span>  
<span data-ttu-id="116fa-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="116fa-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="116fa-107">語法</span><span class="sxs-lookup"><span data-stu-id="116fa-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="116fa-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="116fa-108">Attributes and Elements</span></span>  
 <span data-ttu-id="116fa-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="116fa-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="116fa-110">屬性</span><span class="sxs-lookup"><span data-stu-id="116fa-110">Attributes</span></span>  
 <span data-ttu-id="116fa-111">無。</span><span class="sxs-lookup"><span data-stu-id="116fa-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="116fa-112">子元素</span><span class="sxs-lookup"><span data-stu-id="116fa-112">Child Elements</span></span>  
  
|<span data-ttu-id="116fa-113">屬性</span><span class="sxs-lookup"><span data-stu-id="116fa-113">Attribute</span></span>|<span data-ttu-id="116fa-114">描述</span><span class="sxs-lookup"><span data-stu-id="116fa-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="116fa-115">\<smtp > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="116fa-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="116fa-116">設定簡易郵件傳輸通訊協定選項。</span><span class="sxs-lookup"><span data-stu-id="116fa-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="116fa-117">父項目</span><span class="sxs-lookup"><span data-stu-id="116fa-117">Parent Elements</span></span>  
  
|<span data-ttu-id="116fa-118">**目**</span><span class="sxs-lookup"><span data-stu-id="116fa-118">**Element**</span></span>|<span data-ttu-id="116fa-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="116fa-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="116fa-120">\<system.Net> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="116fa-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="116fa-121">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="116fa-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="116fa-122">範例</span><span class="sxs-lookup"><span data-stu-id="116fa-122">Example</span></span>  
 <span data-ttu-id="116fa-123">下列範例會指定適當的 SMTP 參數使用預設網路認證傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="116fa-123">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="116fa-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="116fa-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="116fa-125">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="116fa-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
