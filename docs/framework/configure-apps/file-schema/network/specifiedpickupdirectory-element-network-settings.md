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
ms.openlocfilehash: 50ab7387fc5e2cac65cac1a6dba0e563225beec9
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874698"
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="56256-102">&lt;specifiedPickupDirectory&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="56256-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="56256-103">設定 Simple Mail Transport Protocol (SMTP) 伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="56256-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="56256-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="56256-104">\<configuration></span></span>  
<span data-ttu-id="56256-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="56256-105">\<system.net></span></span>  
<span data-ttu-id="56256-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="56256-106">\<mailSettings></span></span>  
<span data-ttu-id="56256-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="56256-107">\<smtp></span></span>  
<span data-ttu-id="56256-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="56256-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56256-109">語法</span><span class="sxs-lookup"><span data-stu-id="56256-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56256-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="56256-110">Attributes and Elements</span></span>  
 <span data-ttu-id="56256-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="56256-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56256-112">屬性</span><span class="sxs-lookup"><span data-stu-id="56256-112">Attributes</span></span>  
  
|<span data-ttu-id="56256-113">屬性</span><span class="sxs-lookup"><span data-stu-id="56256-113">Attribute</span></span>|<span data-ttu-id="56256-114">描述</span><span class="sxs-lookup"><span data-stu-id="56256-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="56256-115">目錄，讓應用程式會儲存供稍後處理 SMTP 伺服器的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="56256-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56256-116">子元素</span><span class="sxs-lookup"><span data-stu-id="56256-116">Child Elements</span></span>  
 <span data-ttu-id="56256-117">無。</span><span class="sxs-lookup"><span data-stu-id="56256-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56256-118">父項目</span><span class="sxs-lookup"><span data-stu-id="56256-118">Parent Elements</span></span>  
  
|<span data-ttu-id="56256-119">項目</span><span class="sxs-lookup"><span data-stu-id="56256-119">Element</span></span>|<span data-ttu-id="56256-120">描述</span><span class="sxs-lookup"><span data-stu-id="56256-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56256-121">\<smtp > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="56256-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="56256-122">設定 Simple Mail Transport Protocol (SMTP) 郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="56256-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56256-123">備註</span><span class="sxs-lookup"><span data-stu-id="56256-123">Remarks</span></span>  
 <span data-ttu-id="56256-124">`specifiedPickupDirectory` 屬性會設定目錄，讓應用程式儲存郵件以供 SMTP 伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="56256-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56256-125">範例</span><span class="sxs-lookup"><span data-stu-id="56256-125">Example</span></span>  
 <span data-ttu-id="56256-126">下列範例會指定 c:\maildrop 為郵件收取目錄。</span><span class="sxs-lookup"><span data-stu-id="56256-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="SpecifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="56256-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56256-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="56256-128">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="56256-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
