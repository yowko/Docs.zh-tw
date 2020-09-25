---
title: <smtp> 項目 (網路設定)
description: <smtp>網路設定元素可設定 .NET Framework 中傳送電子郵件選項的傳遞格式、傳遞方法和寄件者位址。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 58f496b4a07f7d5531df897dd54bb6176111f1c4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178316"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="d8af1-103">\<smtp> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="d8af1-103">\<smtp> Element (Network Settings)</span></span>

<span data-ttu-id="d8af1-104">設定傳送電子郵件的傳遞格式、傳遞方法和寄件者位址。</span><span class="sxs-lookup"><span data-stu-id="d8af1-104">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="d8af1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8af1-105">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8af1-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8af1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d8af1-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d8af1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8af1-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d8af1-108">Attributes</span></span>  
  
|<span data-ttu-id="d8af1-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d8af1-109">Attribute</span></span>|<span data-ttu-id="d8af1-110">描述</span><span class="sxs-lookup"><span data-stu-id="d8af1-110">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="d8af1-111">指定外寄電子郵件的傳遞格式。</span><span class="sxs-lookup"><span data-stu-id="d8af1-111">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="d8af1-112">可接受的值為 SevenBit 和 International。</span><span class="sxs-lookup"><span data-stu-id="d8af1-112">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="d8af1-113">指定電子郵件的傳遞方法。</span><span class="sxs-lookup"><span data-stu-id="d8af1-113">Specifies the delivery method for emails.</span></span> <span data-ttu-id="d8af1-114">可接受的值為 Network、PickupDirectoryFromIis 和 SpecifiedPickupDirectory。</span><span class="sxs-lookup"><span data-stu-id="d8af1-114">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="d8af1-115">指定外寄電子郵件的寄件者位址。</span><span class="sxs-lookup"><span data-stu-id="d8af1-115">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8af1-116">子元素</span><span class="sxs-lookup"><span data-stu-id="d8af1-116">Child Elements</span></span>  
  
|<span data-ttu-id="d8af1-117">屬性</span><span class="sxs-lookup"><span data-stu-id="d8af1-117">Attribute</span></span>|<span data-ttu-id="d8af1-118">描述</span><span class="sxs-lookup"><span data-stu-id="d8af1-118">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="d8af1-119">設定簡易郵件傳輸通訊協定 (SMTP) 伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="d8af1-119">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="d8af1-120">設定外部 SMTP 伺服器的網路選項。</span><span class="sxs-lookup"><span data-stu-id="d8af1-120">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8af1-121">父項目</span><span class="sxs-lookup"><span data-stu-id="d8af1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d8af1-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="d8af1-122">**Element**</span></span>|<span data-ttu-id="d8af1-123">**說明**</span><span class="sxs-lookup"><span data-stu-id="d8af1-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d8af1-124">\<mailSettings> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="d8af1-124">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="d8af1-125">設定郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="d8af1-125">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d8af1-126">範例</span><span class="sxs-lookup"><span data-stu-id="d8af1-126">Example</span></span>  

 <span data-ttu-id="d8af1-127">下列範例會指定適當的 SMTP 參數，以使用預設網路認證來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="d8af1-127">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8af1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8af1-128">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="d8af1-129">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d8af1-129">Network Settings Schema</span></span>](index.md)
