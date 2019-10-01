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
ms.openlocfilehash: 47aa357dac8b6bf71ce8c391004af16f8c98e347
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697597"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="f756b-102">@no__t 0specifiedPickupDirectory > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="f756b-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="f756b-103">設定簡單郵件傳輸通訊協定（SMTP）伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="f756b-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[<span data-ttu-id="f756b-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="f756b-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="f756b-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f756b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="f756b-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f756b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>  
<span data-ttu-id="f756b-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<smtp >** ](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f756b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>  
<span data-ttu-id="f756b-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<specifiedPickupDirectory >**</span><span class="sxs-lookup"><span data-stu-id="f756b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f756b-109">語法</span><span class="sxs-lookup"><span data-stu-id="f756b-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f756b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f756b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f756b-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f756b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f756b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f756b-112">Attributes</span></span>  
  
|<span data-ttu-id="f756b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f756b-113">Attribute</span></span>|<span data-ttu-id="f756b-114">描述</span><span class="sxs-lookup"><span data-stu-id="f756b-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="f756b-115">應用程式儲存電子郵件以供 SMTP 伺服器稍後處理的目錄。</span><span class="sxs-lookup"><span data-stu-id="f756b-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f756b-116">子元素</span><span class="sxs-lookup"><span data-stu-id="f756b-116">Child Elements</span></span>  
 <span data-ttu-id="f756b-117">無。</span><span class="sxs-lookup"><span data-stu-id="f756b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f756b-118">父項目</span><span class="sxs-lookup"><span data-stu-id="f756b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f756b-119">項目</span><span class="sxs-lookup"><span data-stu-id="f756b-119">Element</span></span>|<span data-ttu-id="f756b-120">描述</span><span class="sxs-lookup"><span data-stu-id="f756b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f756b-121">@no__t 1smtp > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="f756b-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="f756b-122">設定簡單郵件傳輸通訊協定（SMTP）郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="f756b-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f756b-123">備註</span><span class="sxs-lookup"><span data-stu-id="f756b-123">Remarks</span></span>  
 <span data-ttu-id="f756b-124">`specifiedPickupDirectory` 屬性會設定目錄，讓應用程式儲存郵件以供 SMTP 伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="f756b-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f756b-125">範例</span><span class="sxs-lookup"><span data-stu-id="f756b-125">Example</span></span>  
 <span data-ttu-id="f756b-126">下列範例會將 c:\maildrop 指定為郵件收取目錄。</span><span class="sxs-lookup"><span data-stu-id="f756b-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f756b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f756b-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="f756b-128">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f756b-128">Network Settings Schema</span></span>](index.md)
