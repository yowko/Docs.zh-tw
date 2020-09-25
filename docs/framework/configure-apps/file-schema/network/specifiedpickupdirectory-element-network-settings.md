---
title: <specifiedPickupDirectory> 項目 (網路設定)
description: <specifiedPickupDirectory>網路設定元素會設定 .NET Framework 中 SMTP 伺服器選項的本機目錄。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: 5bb7fc5405b1ee2f0f054bc6e9f043a3f9fcd1ec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176158"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="c5aee-103">\<specifiedPickupDirectory> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="c5aee-103">\<specifiedPickupDirectory> Element (Network Settings)</span></span>

<span data-ttu-id="c5aee-104">設定簡易郵件傳輸通訊協定 (SMTP) 伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="c5aee-104">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="c5aee-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c5aee-105">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5aee-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c5aee-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c5aee-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c5aee-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5aee-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c5aee-108">Attributes</span></span>  
  
|<span data-ttu-id="c5aee-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c5aee-109">Attribute</span></span>|<span data-ttu-id="c5aee-110">描述</span><span class="sxs-lookup"><span data-stu-id="c5aee-110">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="c5aee-111">應用程式儲存電子郵件以供 SMTP 伺服器稍後處理的目錄。</span><span class="sxs-lookup"><span data-stu-id="c5aee-111">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5aee-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c5aee-112">Child Elements</span></span>  

 <span data-ttu-id="c5aee-113">無。</span><span class="sxs-lookup"><span data-stu-id="c5aee-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5aee-114">父項目</span><span class="sxs-lookup"><span data-stu-id="c5aee-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c5aee-115">項目</span><span class="sxs-lookup"><span data-stu-id="c5aee-115">Element</span></span>|<span data-ttu-id="c5aee-116">描述</span><span class="sxs-lookup"><span data-stu-id="c5aee-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5aee-117">\<smtp> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="c5aee-117">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="c5aee-118">設定 Simple Mail Transport Protocol (SMTP) Mail 傳送選項。</span><span class="sxs-lookup"><span data-stu-id="c5aee-118">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5aee-119">備註</span><span class="sxs-lookup"><span data-stu-id="c5aee-119">Remarks</span></span>  

 <span data-ttu-id="c5aee-120">`specifiedPickupDirectory` 屬性會設定目錄，讓應用程式儲存郵件以供 SMTP 伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="c5aee-120">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5aee-121">範例</span><span class="sxs-lookup"><span data-stu-id="c5aee-121">Example</span></span>  

 <span data-ttu-id="c5aee-122">下列範例會將 c:\maildrop 指定為郵件收取目錄。</span><span class="sxs-lookup"><span data-stu-id="c5aee-122">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5aee-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5aee-123">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="c5aee-124">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c5aee-124">Network Settings Schema</span></span>](index.md)
