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
ms.openlocfilehash: 4b0cbaf9a7bfe2a9b1610811f4201253d219a6b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154604"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="555d2-102">\<指定的收取目錄>元素（網路設置）</span><span class="sxs-lookup"><span data-stu-id="555d2-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="555d2-103">為簡單郵件傳輸協議 （SMTP） 伺服器配置本地目錄。</span><span class="sxs-lookup"><span data-stu-id="555d2-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
<span data-ttu-id="555d2-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="555d2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="555d2-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="555d2-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="555d2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<郵件設置>**](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="555d2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="555d2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<斯姆特普>**](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="555d2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="555d2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<指定的取件目錄>**</span><span class="sxs-lookup"><span data-stu-id="555d2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="555d2-109">語法</span><span class="sxs-lookup"><span data-stu-id="555d2-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="555d2-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="555d2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="555d2-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="555d2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="555d2-112">屬性</span><span class="sxs-lookup"><span data-stu-id="555d2-112">Attributes</span></span>  
  
|<span data-ttu-id="555d2-113">屬性</span><span class="sxs-lookup"><span data-stu-id="555d2-113">Attribute</span></span>|<span data-ttu-id="555d2-114">描述</span><span class="sxs-lookup"><span data-stu-id="555d2-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="555d2-115">應用程式保存電子郵件以供 SMTP 伺服器以後處理的目錄。</span><span class="sxs-lookup"><span data-stu-id="555d2-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="555d2-116">子元素</span><span class="sxs-lookup"><span data-stu-id="555d2-116">Child Elements</span></span>  
 <span data-ttu-id="555d2-117">無。</span><span class="sxs-lookup"><span data-stu-id="555d2-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="555d2-118">父項目</span><span class="sxs-lookup"><span data-stu-id="555d2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="555d2-119">元素</span><span class="sxs-lookup"><span data-stu-id="555d2-119">Element</span></span>|<span data-ttu-id="555d2-120">描述</span><span class="sxs-lookup"><span data-stu-id="555d2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="555d2-121">\<smtp>元素（網路設置）</span><span class="sxs-lookup"><span data-stu-id="555d2-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="555d2-122">配置簡單的郵件傳輸協議 （SMTP） 郵件發送選項。</span><span class="sxs-lookup"><span data-stu-id="555d2-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="555d2-123">備註</span><span class="sxs-lookup"><span data-stu-id="555d2-123">Remarks</span></span>  
 <span data-ttu-id="555d2-124">`specifiedPickupDirectory` 屬性會設定目錄，讓應用程式儲存郵件以供 SMTP 伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="555d2-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="555d2-125">範例</span><span class="sxs-lookup"><span data-stu-id="555d2-125">Example</span></span>  
 <span data-ttu-id="555d2-126">下面的示例指定 c：\maildrop 作為郵件取件目錄。</span><span class="sxs-lookup"><span data-stu-id="555d2-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="555d2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="555d2-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="555d2-128">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="555d2-128">Network Settings Schema</span></span>](index.md)
