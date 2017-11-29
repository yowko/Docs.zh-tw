---
title: "&lt;specifiedPickupDirectory&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ffe34e6a811dd644b149a0fda12f1d1cd338c761
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="89fd1-102">&lt;specifiedPickupDirectory&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="89fd1-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="89fd1-103">設定簡易郵件傳輸通訊協定 (SMTP) 伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="89fd1-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="89fd1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="89fd1-104">\<configuration></span></span>  
<span data-ttu-id="89fd1-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="89fd1-105">\<system.net></span></span>  
<span data-ttu-id="89fd1-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="89fd1-106">\<mailSettings></span></span>  
<span data-ttu-id="89fd1-107">\<smtp ></span><span class="sxs-lookup"><span data-stu-id="89fd1-107">\<smtp></span></span>  
<span data-ttu-id="89fd1-108">\<specifiedPickupDirectory ></span><span class="sxs-lookup"><span data-stu-id="89fd1-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89fd1-109">語法</span><span class="sxs-lookup"><span data-stu-id="89fd1-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89fd1-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="89fd1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="89fd1-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="89fd1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89fd1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="89fd1-112">Attributes</span></span>  
  
|<span data-ttu-id="89fd1-113">屬性</span><span class="sxs-lookup"><span data-stu-id="89fd1-113">Attribute</span></span>|<span data-ttu-id="89fd1-114">說明</span><span class="sxs-lookup"><span data-stu-id="89fd1-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="89fd1-115">目錄，讓應用程式儲存供稍後處理 SMTP 伺服器的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="89fd1-115">The directory where applications save e-mail for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89fd1-116">子元素</span><span class="sxs-lookup"><span data-stu-id="89fd1-116">Child Elements</span></span>  
 <span data-ttu-id="89fd1-117">無。</span><span class="sxs-lookup"><span data-stu-id="89fd1-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89fd1-118">父項目</span><span class="sxs-lookup"><span data-stu-id="89fd1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="89fd1-119">項目</span><span class="sxs-lookup"><span data-stu-id="89fd1-119">Element</span></span>|<span data-ttu-id="89fd1-120">說明</span><span class="sxs-lookup"><span data-stu-id="89fd1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89fd1-121">\<smtp > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="89fd1-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="89fd1-122">設定簡易郵件傳輸通訊協定 (SMTP) 郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="89fd1-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89fd1-123">備註</span><span class="sxs-lookup"><span data-stu-id="89fd1-123">Remarks</span></span>  
 <span data-ttu-id="89fd1-124">`specifiedPickupDirectory` 屬性會設定目錄，讓應用程式儲存郵件以供 SMTP 伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="89fd1-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89fd1-125">範例</span><span class="sxs-lookup"><span data-stu-id="89fd1-125">Example</span></span>  
 <span data-ttu-id="89fd1-126">下列範例會指定 c:\maildrop 為郵件收取目錄。</span><span class="sxs-lookup"><span data-stu-id="89fd1-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89fd1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89fd1-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="89fd1-128">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="89fd1-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
