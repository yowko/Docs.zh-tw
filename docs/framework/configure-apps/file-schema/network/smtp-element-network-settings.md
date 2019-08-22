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
ms.openlocfilehash: ac9405fdc6123a5a1352de06f94fefb6d7d4014b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659113"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="82ca0-102">\<smtp > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="82ca0-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="82ca0-103">設定傳送電子郵件的傳遞格式、傳遞方法和寄件者位址。</span><span class="sxs-lookup"><span data-stu-id="82ca0-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="82ca0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="82ca0-104">\<configuration></span></span>  
<span data-ttu-id="82ca0-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="82ca0-105">\<system.net></span></span>  
<span data-ttu-id="82ca0-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="82ca0-106">\<mailSettings></span></span>  
<span data-ttu-id="82ca0-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="82ca0-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82ca0-108">語法</span><span class="sxs-lookup"><span data-stu-id="82ca0-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82ca0-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="82ca0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="82ca0-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="82ca0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82ca0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="82ca0-111">Attributes</span></span>  
  
|<span data-ttu-id="82ca0-112">屬性</span><span class="sxs-lookup"><span data-stu-id="82ca0-112">Attribute</span></span>|<span data-ttu-id="82ca0-113">描述</span><span class="sxs-lookup"><span data-stu-id="82ca0-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="82ca0-114">指定外寄電子郵件的傳遞格式。</span><span class="sxs-lookup"><span data-stu-id="82ca0-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="82ca0-115">可接受的值為 SevenBit 和 International。</span><span class="sxs-lookup"><span data-stu-id="82ca0-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="82ca0-116">指定電子郵件的傳遞方法。</span><span class="sxs-lookup"><span data-stu-id="82ca0-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="82ca0-117">可接受的值為 Network、PickupDirectoryFromIis 和 SpecifiedPickupDirectory。</span><span class="sxs-lookup"><span data-stu-id="82ca0-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="82ca0-118">指定外寄電子郵件的寄件者位址。</span><span class="sxs-lookup"><span data-stu-id="82ca0-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82ca0-119">子元素</span><span class="sxs-lookup"><span data-stu-id="82ca0-119">Child Elements</span></span>  
  
|<span data-ttu-id="82ca0-120">屬性</span><span class="sxs-lookup"><span data-stu-id="82ca0-120">Attribute</span></span>|<span data-ttu-id="82ca0-121">說明</span><span class="sxs-lookup"><span data-stu-id="82ca0-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="82ca0-122">設定簡單郵件傳輸通訊協定 (SMTP) 伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="82ca0-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="82ca0-123">設定外部 SMTP 伺服器的網路選項。</span><span class="sxs-lookup"><span data-stu-id="82ca0-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82ca0-124">父項目</span><span class="sxs-lookup"><span data-stu-id="82ca0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="82ca0-125">**目**</span><span class="sxs-lookup"><span data-stu-id="82ca0-125">**Element**</span></span>|<span data-ttu-id="82ca0-126">**描述**</span><span class="sxs-lookup"><span data-stu-id="82ca0-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="82ca0-127">\<mailSettings> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="82ca0-127">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="82ca0-128">設定郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="82ca0-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="82ca0-129">範例</span><span class="sxs-lookup"><span data-stu-id="82ca0-129">Example</span></span>  
 <span data-ttu-id="82ca0-130">下列範例會指定適當的 SMTP 參數, 以使用預設網路認證來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="82ca0-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="82ca0-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82ca0-131">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="82ca0-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="82ca0-132">Network Settings Schema</span></span>](index.md)
