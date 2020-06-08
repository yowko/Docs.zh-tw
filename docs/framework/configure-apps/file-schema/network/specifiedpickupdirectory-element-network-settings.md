---
title: <specifiedPickupDirectory> 項目 (網路設定)
description: <specifiedPickupDirectory>網路設定元素會針對 .NET Framework 中的 SMTP 伺服器選項設定本機目錄。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: f0c4c1845e9542d0f3b836ff03f16bdf2979ebd8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504494"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="d30af-103">\<specifiedPickupDirectory> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="d30af-103">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="d30af-104">設定簡單郵件傳輸通訊協定（SMTP）伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="d30af-104">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="d30af-105">語法</span><span class="sxs-lookup"><span data-stu-id="d30af-105">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d30af-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d30af-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d30af-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d30af-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d30af-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d30af-108">Attributes</span></span>  
  
|<span data-ttu-id="d30af-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d30af-109">Attribute</span></span>|<span data-ttu-id="d30af-110">說明</span><span class="sxs-lookup"><span data-stu-id="d30af-110">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="d30af-111">應用程式儲存電子郵件以供 SMTP 伺服器稍後處理的目錄。</span><span class="sxs-lookup"><span data-stu-id="d30af-111">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d30af-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d30af-112">Child Elements</span></span>  
 <span data-ttu-id="d30af-113">無。</span><span class="sxs-lookup"><span data-stu-id="d30af-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d30af-114">父項目</span><span class="sxs-lookup"><span data-stu-id="d30af-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d30af-115">元素</span><span class="sxs-lookup"><span data-stu-id="d30af-115">Element</span></span>|<span data-ttu-id="d30af-116">說明</span><span class="sxs-lookup"><span data-stu-id="d30af-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d30af-117">\<smtp>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="d30af-117">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="d30af-118">設定簡單郵件傳輸通訊協定（SMTP）郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="d30af-118">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d30af-119">備註</span><span class="sxs-lookup"><span data-stu-id="d30af-119">Remarks</span></span>  
 <span data-ttu-id="d30af-120">`specifiedPickupDirectory` 屬性會設定目錄，讓應用程式儲存郵件以供 SMTP 伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="d30af-120">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d30af-121">範例</span><span class="sxs-lookup"><span data-stu-id="d30af-121">Example</span></span>  
 <span data-ttu-id="d30af-122">下列範例會將 c:\maildrop 指定為郵件收取目錄。</span><span class="sxs-lookup"><span data-stu-id="d30af-122">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d30af-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d30af-123">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="d30af-124">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d30af-124">Network Settings Schema</span></span>](index.md)
