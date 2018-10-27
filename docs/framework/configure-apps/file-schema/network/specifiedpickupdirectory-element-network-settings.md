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
ms.openlocfilehash: eec7c5b41fabcb5ee4566f8b96f67322c1d6c47b
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50170753"
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="d8267-102">&lt;specifiedPickupDirectory&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="d8267-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="d8267-103">設定 Simple Mail Transport Protocol (SMTP) 伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="d8267-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="d8267-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d8267-104">\<configuration></span></span>  
<span data-ttu-id="d8267-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d8267-105">\<system.net></span></span>  
<span data-ttu-id="d8267-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="d8267-106">\<mailSettings></span></span>  
<span data-ttu-id="d8267-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="d8267-107">\<smtp></span></span>  
<span data-ttu-id="d8267-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="d8267-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8267-109">語法</span><span class="sxs-lookup"><span data-stu-id="d8267-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8267-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8267-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d8267-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d8267-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8267-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d8267-112">Attributes</span></span>  
  
|<span data-ttu-id="d8267-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d8267-113">Attribute</span></span>|<span data-ttu-id="d8267-114">描述</span><span class="sxs-lookup"><span data-stu-id="d8267-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="d8267-115">目錄，讓應用程式會儲存供稍後處理 SMTP 伺服器的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="d8267-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8267-116">子元素</span><span class="sxs-lookup"><span data-stu-id="d8267-116">Child Elements</span></span>  
 <span data-ttu-id="d8267-117">無。</span><span class="sxs-lookup"><span data-stu-id="d8267-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8267-118">父項目</span><span class="sxs-lookup"><span data-stu-id="d8267-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d8267-119">項目</span><span class="sxs-lookup"><span data-stu-id="d8267-119">Element</span></span>|<span data-ttu-id="d8267-120">描述</span><span class="sxs-lookup"><span data-stu-id="d8267-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8267-121">\<smtp > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="d8267-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="d8267-122">設定 Simple Mail Transport Protocol (SMTP) 郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="d8267-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8267-123">備註</span><span class="sxs-lookup"><span data-stu-id="d8267-123">Remarks</span></span>  
 <span data-ttu-id="d8267-124">`specifiedPickupDirectory` 屬性會設定目錄，讓應用程式儲存郵件以供 SMTP 伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="d8267-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8267-125">範例</span><span class="sxs-lookup"><span data-stu-id="d8267-125">Example</span></span>  
 <span data-ttu-id="d8267-126">下列範例會指定 c:\maildrop 為郵件收取目錄。</span><span class="sxs-lookup"><span data-stu-id="d8267-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8267-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8267-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="d8267-128">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d8267-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
