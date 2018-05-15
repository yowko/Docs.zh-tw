---
title: '&lt;specifiedPickupDirectory&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3a982bdbe4953691d4e8e7663f14059ff4771934
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="e7ded-102">&lt;specifiedPickupDirectory&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="e7ded-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="e7ded-103">設定簡易郵件傳輸通訊協定 (SMTP) 伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="e7ded-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="e7ded-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e7ded-104">\<configuration></span></span>  
<span data-ttu-id="e7ded-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e7ded-105">\<system.net></span></span>  
<span data-ttu-id="e7ded-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="e7ded-106">\<mailSettings></span></span>  
<span data-ttu-id="e7ded-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="e7ded-107">\<smtp></span></span>  
<span data-ttu-id="e7ded-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="e7ded-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7ded-109">語法</span><span class="sxs-lookup"><span data-stu-id="e7ded-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7ded-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e7ded-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e7ded-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e7ded-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7ded-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e7ded-112">Attributes</span></span>  
  
|<span data-ttu-id="e7ded-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e7ded-113">Attribute</span></span>|<span data-ttu-id="e7ded-114">描述</span><span class="sxs-lookup"><span data-stu-id="e7ded-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="e7ded-115">目錄，讓應用程式儲存供稍後處理 SMTP 伺服器的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="e7ded-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7ded-116">子項目</span><span class="sxs-lookup"><span data-stu-id="e7ded-116">Child Elements</span></span>  
 <span data-ttu-id="e7ded-117">無。</span><span class="sxs-lookup"><span data-stu-id="e7ded-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7ded-118">父項目</span><span class="sxs-lookup"><span data-stu-id="e7ded-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e7ded-119">項目</span><span class="sxs-lookup"><span data-stu-id="e7ded-119">Element</span></span>|<span data-ttu-id="e7ded-120">描述</span><span class="sxs-lookup"><span data-stu-id="e7ded-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7ded-121">\<smtp > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="e7ded-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="e7ded-122">設定簡易郵件傳輸通訊協定 (SMTP) 郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="e7ded-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7ded-123">備註</span><span class="sxs-lookup"><span data-stu-id="e7ded-123">Remarks</span></span>  
 <span data-ttu-id="e7ded-124">`specifiedPickupDirectory` 屬性會設定目錄，讓應用程式儲存郵件以供 SMTP 伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="e7ded-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7ded-125">範例</span><span class="sxs-lookup"><span data-stu-id="e7ded-125">Example</span></span>  
 <span data-ttu-id="e7ded-126">下列範例會指定 c:\maildrop 為郵件收取目錄。</span><span class="sxs-lookup"><span data-stu-id="e7ded-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="specifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7ded-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7ded-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="e7ded-128">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e7ded-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
