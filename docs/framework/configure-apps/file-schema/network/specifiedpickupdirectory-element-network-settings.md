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
ms.openlocfilehash: 7735aea55f03b0703ebb7b0e3c5f958b57f1238d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611302"
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="f81c9-102">&lt;specifiedPickupDirectory&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="f81c9-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="f81c9-103">設定 Simple Mail Transport Protocol (SMTP) 伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="f81c9-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="f81c9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f81c9-104">\<configuration></span></span>  
<span data-ttu-id="f81c9-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f81c9-105">\<system.net></span></span>  
<span data-ttu-id="f81c9-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="f81c9-106">\<mailSettings></span></span>  
<span data-ttu-id="f81c9-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="f81c9-107">\<smtp></span></span>  
<span data-ttu-id="f81c9-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="f81c9-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f81c9-109">語法</span><span class="sxs-lookup"><span data-stu-id="f81c9-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f81c9-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f81c9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f81c9-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f81c9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f81c9-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f81c9-112">Attributes</span></span>  
  
|<span data-ttu-id="f81c9-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f81c9-113">Attribute</span></span>|<span data-ttu-id="f81c9-114">描述</span><span class="sxs-lookup"><span data-stu-id="f81c9-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="f81c9-115">目錄，讓應用程式會儲存供稍後處理 SMTP 伺服器的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="f81c9-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f81c9-116">子元素</span><span class="sxs-lookup"><span data-stu-id="f81c9-116">Child Elements</span></span>  
 <span data-ttu-id="f81c9-117">無。</span><span class="sxs-lookup"><span data-stu-id="f81c9-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f81c9-118">父項目</span><span class="sxs-lookup"><span data-stu-id="f81c9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f81c9-119">項目</span><span class="sxs-lookup"><span data-stu-id="f81c9-119">Element</span></span>|<span data-ttu-id="f81c9-120">描述</span><span class="sxs-lookup"><span data-stu-id="f81c9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f81c9-121">\<smtp > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="f81c9-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="f81c9-122">設定 Simple Mail Transport Protocol (SMTP) 郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="f81c9-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f81c9-123">備註</span><span class="sxs-lookup"><span data-stu-id="f81c9-123">Remarks</span></span>  
 <span data-ttu-id="f81c9-124">`specifiedPickupDirectory` 屬性會設定目錄，讓應用程式儲存郵件以供 SMTP 伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="f81c9-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f81c9-125">範例</span><span class="sxs-lookup"><span data-stu-id="f81c9-125">Example</span></span>  
 <span data-ttu-id="f81c9-126">下列範例會指定 c:\maildrop 為郵件收取目錄。</span><span class="sxs-lookup"><span data-stu-id="f81c9-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f81c9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f81c9-127">See also</span></span>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="f81c9-128">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f81c9-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
