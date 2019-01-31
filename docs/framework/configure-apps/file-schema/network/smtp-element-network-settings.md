---
title: <smtp> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: ecd780da7224389685b61c39c796c7a80587709c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273578"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="a10fe-102">\<smtp > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="a10fe-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="a10fe-103">設定的傳遞格式、 傳遞方法，以及從來傳送電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="a10fe-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="a10fe-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a10fe-104">\<configuration></span></span>  
<span data-ttu-id="a10fe-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="a10fe-105">\<system.net></span></span>  
<span data-ttu-id="a10fe-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="a10fe-106">\<mailSettings></span></span>  
<span data-ttu-id="a10fe-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="a10fe-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a10fe-108">語法</span><span class="sxs-lookup"><span data-stu-id="a10fe-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a10fe-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a10fe-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a10fe-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a10fe-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a10fe-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a10fe-111">Attributes</span></span>  
  
|<span data-ttu-id="a10fe-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a10fe-112">Attribute</span></span>|<span data-ttu-id="a10fe-113">描述</span><span class="sxs-lookup"><span data-stu-id="a10fe-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="a10fe-114">指定外寄電子郵件的傳遞格式。</span><span class="sxs-lookup"><span data-stu-id="a10fe-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="a10fe-115">可接受的值為 SevenBit 和 International。</span><span class="sxs-lookup"><span data-stu-id="a10fe-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="a10fe-116">指定電子郵件的傳遞方法。</span><span class="sxs-lookup"><span data-stu-id="a10fe-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="a10fe-117">可接受的值為網路、 PickupDirectoryFromIis 和 SpecifiedPickupDirectory。</span><span class="sxs-lookup"><span data-stu-id="a10fe-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="a10fe-118">指定從外寄電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="a10fe-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a10fe-119">子元素</span><span class="sxs-lookup"><span data-stu-id="a10fe-119">Child Elements</span></span>  
  
|<span data-ttu-id="a10fe-120">屬性</span><span class="sxs-lookup"><span data-stu-id="a10fe-120">Attribute</span></span>|<span data-ttu-id="a10fe-121">描述</span><span class="sxs-lookup"><span data-stu-id="a10fe-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="a10fe-122">設定 Simple Mail Transport Protocol (SMTP) 伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="a10fe-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="a10fe-123">設定外部 SMTP 伺服器的網路選項。</span><span class="sxs-lookup"><span data-stu-id="a10fe-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a10fe-124">父項目</span><span class="sxs-lookup"><span data-stu-id="a10fe-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a10fe-125">**目**</span><span class="sxs-lookup"><span data-stu-id="a10fe-125">**Element**</span></span>|<span data-ttu-id="a10fe-126">**描述**</span><span class="sxs-lookup"><span data-stu-id="a10fe-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a10fe-127">\<mailSettings> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="a10fe-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="a10fe-128">設定郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="a10fe-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a10fe-129">範例</span><span class="sxs-lookup"><span data-stu-id="a10fe-129">Example</span></span>  
 <span data-ttu-id="a10fe-130">下列範例會指定適當的 SMTP 參數，使用預設網路認證傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="a10fe-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
  
## <a name="see-also"></a><span data-ttu-id="a10fe-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a10fe-131">See also</span></span>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="a10fe-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a10fe-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
