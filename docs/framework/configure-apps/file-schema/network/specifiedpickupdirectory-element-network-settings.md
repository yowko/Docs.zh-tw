---
title: <specifiedPickupDirectory> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: 1acc724bb14c3610f14d06452c30b3d5dac42e13
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089080"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="bc3bd-102">\<specifiedPickupDirectory > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="bc3bd-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="bc3bd-103">設定簡單郵件傳輸通訊協定（SMTP）伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="bc3bd-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
<span data-ttu-id="bc3bd-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bc3bd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bc3bd-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="bc3bd-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="bc3bd-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="bc3bd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="bc3bd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**smtp >** ](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="bc3bd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="bc3bd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<specifiedPickupDirectory >**</span><span class="sxs-lookup"><span data-stu-id="bc3bd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc3bd-109">語法</span><span class="sxs-lookup"><span data-stu-id="bc3bd-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc3bd-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bc3bd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bc3bd-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bc3bd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc3bd-112">屬性</span><span class="sxs-lookup"><span data-stu-id="bc3bd-112">Attributes</span></span>  
  
|<span data-ttu-id="bc3bd-113">屬性</span><span class="sxs-lookup"><span data-stu-id="bc3bd-113">Attribute</span></span>|<span data-ttu-id="bc3bd-114">描述</span><span class="sxs-lookup"><span data-stu-id="bc3bd-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="bc3bd-115">應用程式儲存電子郵件以供 SMTP 伺服器稍後處理的目錄。</span><span class="sxs-lookup"><span data-stu-id="bc3bd-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc3bd-116">子項目</span><span class="sxs-lookup"><span data-stu-id="bc3bd-116">Child Elements</span></span>  
 <span data-ttu-id="bc3bd-117">無。</span><span class="sxs-lookup"><span data-stu-id="bc3bd-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc3bd-118">父項目</span><span class="sxs-lookup"><span data-stu-id="bc3bd-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bc3bd-119">項目</span><span class="sxs-lookup"><span data-stu-id="bc3bd-119">Element</span></span>|<span data-ttu-id="bc3bd-120">描述</span><span class="sxs-lookup"><span data-stu-id="bc3bd-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc3bd-121">\<smtp > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="bc3bd-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="bc3bd-122">設定簡單郵件傳輸通訊協定（SMTP）郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="bc3bd-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc3bd-123">備註</span><span class="sxs-lookup"><span data-stu-id="bc3bd-123">Remarks</span></span>  
 <span data-ttu-id="bc3bd-124">`specifiedPickupDirectory` 屬性會設定目錄，讓應用程式儲存郵件以供 SMTP 伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="bc3bd-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc3bd-125">範例</span><span class="sxs-lookup"><span data-stu-id="bc3bd-125">Example</span></span>  
 <span data-ttu-id="bc3bd-126">下列範例會將 c:\maildrop 指定為郵件收取目錄。</span><span class="sxs-lookup"><span data-stu-id="bc3bd-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bc3bd-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="bc3bd-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="bc3bd-128">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="bc3bd-128">Network Settings Schema</span></span>](index.md)
