---
title: "&lt;smtp&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 17b4050c43354da7e7ba6c3ea13a0c7621faf0a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="7e70e-102">&lt;smtp&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="7e70e-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="7e70e-103">設定傳送電子郵件的傳遞格式、傳遞方法和寄件地址。</span><span class="sxs-lookup"><span data-stu-id="7e70e-103">Configures the delivery format, delivery method, and from address for sending e-mails.</span></span>  
  
 <span data-ttu-id="7e70e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7e70e-104">\<configuration></span></span>  
<span data-ttu-id="7e70e-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="7e70e-105">\<system.net></span></span>  
<span data-ttu-id="7e70e-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="7e70e-106">\<mailSettings></span></span>  
<span data-ttu-id="7e70e-107">\<smtp ></span><span class="sxs-lookup"><span data-stu-id="7e70e-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e70e-108">語法</span><span class="sxs-lookup"><span data-stu-id="7e70e-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e70e-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7e70e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7e70e-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7e70e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e70e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7e70e-111">Attributes</span></span>  
  
|<span data-ttu-id="7e70e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7e70e-112">Attribute</span></span>|<span data-ttu-id="7e70e-113">說明</span><span class="sxs-lookup"><span data-stu-id="7e70e-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="7e70e-114">指定外送電子郵件的傳遞格式。</span><span class="sxs-lookup"><span data-stu-id="7e70e-114">Specifies the delivery format for outgoing e-mails.</span></span> <span data-ttu-id="7e70e-115">可接受的值為 SevenBit 和 International。</span><span class="sxs-lookup"><span data-stu-id="7e70e-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="7e70e-116">指定電子郵件的傳遞方法。</span><span class="sxs-lookup"><span data-stu-id="7e70e-116">Specifies the delivery method for e-mails.</span></span> <span data-ttu-id="7e70e-117">可接受的值為網路、 pickupDirectoryFromIis 和 specifiedPickupDirectory。</span><span class="sxs-lookup"><span data-stu-id="7e70e-117">Acceptable values are network, pickupDirectoryFromIis, and specifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="7e70e-118">指定外送電子郵件的寄件地址。</span><span class="sxs-lookup"><span data-stu-id="7e70e-118">Specifies the from address for outgoing e-mails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e70e-119">子元素</span><span class="sxs-lookup"><span data-stu-id="7e70e-119">Child Elements</span></span>  
  
|<span data-ttu-id="7e70e-120">屬性</span><span class="sxs-lookup"><span data-stu-id="7e70e-120">Attribute</span></span>|<span data-ttu-id="7e70e-121">說明</span><span class="sxs-lookup"><span data-stu-id="7e70e-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="7e70e-122">設定簡易郵件傳輸通訊協定 (SMTP) 伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="7e70e-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="7e70e-123">設定外部的 SMTP 伺服器的網路選項。</span><span class="sxs-lookup"><span data-stu-id="7e70e-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e70e-124">父項目</span><span class="sxs-lookup"><span data-stu-id="7e70e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7e70e-125">**目**</span><span class="sxs-lookup"><span data-stu-id="7e70e-125">**Element**</span></span>|<span data-ttu-id="7e70e-126">**說明**</span><span class="sxs-lookup"><span data-stu-id="7e70e-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7e70e-127">\<mailSettings> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="7e70e-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="7e70e-128">設定郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="7e70e-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7e70e-129">範例</span><span class="sxs-lookup"><span data-stu-id="7e70e-129">Example</span></span>  
 <span data-ttu-id="7e70e-130">下列範例會指定適當的 SMTP 參數使用預設網路認證傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="7e70e-130">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
  
## <a name="see-also"></a><span data-ttu-id="7e70e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e70e-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="7e70e-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7e70e-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
