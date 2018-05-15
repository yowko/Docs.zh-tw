---
title: '&lt;mailSettings&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5bc7cc649b18a5330d056bbddfe96db4ecca2ec8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="a1d2a-102">&lt;mailSettings&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="a1d2a-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="a1d2a-103">設定郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="a1d2a-103">Configures mail sending options.</span></span>  

<span data-ttu-id="a1d2a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a1d2a-104">\<configuration></span></span>  
<span data-ttu-id="a1d2a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="a1d2a-105">\<system.net></span></span>  
<span data-ttu-id="a1d2a-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="a1d2a-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1d2a-107">語法</span><span class="sxs-lookup"><span data-stu-id="a1d2a-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1d2a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a1d2a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a1d2a-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a1d2a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1d2a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a1d2a-110">Attributes</span></span>  
 <span data-ttu-id="a1d2a-111">無。</span><span class="sxs-lookup"><span data-stu-id="a1d2a-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a1d2a-112">子項目</span><span class="sxs-lookup"><span data-stu-id="a1d2a-112">Child Elements</span></span>  
  
|<span data-ttu-id="a1d2a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a1d2a-113">Attribute</span></span>|<span data-ttu-id="a1d2a-114">描述</span><span class="sxs-lookup"><span data-stu-id="a1d2a-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="a1d2a-115">\<smtp > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="a1d2a-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="a1d2a-116">設定簡易郵件傳輸通訊協定選項。</span><span class="sxs-lookup"><span data-stu-id="a1d2a-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1d2a-117">父項目</span><span class="sxs-lookup"><span data-stu-id="a1d2a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a1d2a-118">**目**</span><span class="sxs-lookup"><span data-stu-id="a1d2a-118">**Element**</span></span>|<span data-ttu-id="a1d2a-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="a1d2a-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a1d2a-120">\<system.Net> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="a1d2a-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="a1d2a-121">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="a1d2a-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a1d2a-122">範例</span><span class="sxs-lookup"><span data-stu-id="a1d2a-122">Example</span></span>  
 <span data-ttu-id="a1d2a-123">下列範例會指定適當 SMTP 參數來傳送電子郵件使用預設網路認證。</span><span class="sxs-lookup"><span data-stu-id="a1d2a-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a1d2a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1d2a-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="a1d2a-125">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a1d2a-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
