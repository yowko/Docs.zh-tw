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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154604"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="0d016-102">\<specifiedPickupDirectory> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="0d016-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="0d016-103">設定簡單郵件傳輸通訊協定（SMTP）伺服器的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="0d016-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="0d016-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d016-104">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d016-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0d016-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0d016-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0d016-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d016-107">屬性</span><span class="sxs-lookup"><span data-stu-id="0d016-107">Attributes</span></span>  
  
|<span data-ttu-id="0d016-108">屬性</span><span class="sxs-lookup"><span data-stu-id="0d016-108">Attribute</span></span>|<span data-ttu-id="0d016-109">描述</span><span class="sxs-lookup"><span data-stu-id="0d016-109">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="0d016-110">應用程式儲存電子郵件以供 SMTP 伺服器稍後處理的目錄。</span><span class="sxs-lookup"><span data-stu-id="0d016-110">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d016-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0d016-111">Child Elements</span></span>  
 <span data-ttu-id="0d016-112">無。</span><span class="sxs-lookup"><span data-stu-id="0d016-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d016-113">父項目</span><span class="sxs-lookup"><span data-stu-id="0d016-113">Parent Elements</span></span>  
  
|<span data-ttu-id="0d016-114">元素</span><span class="sxs-lookup"><span data-stu-id="0d016-114">Element</span></span>|<span data-ttu-id="0d016-115">描述</span><span class="sxs-lookup"><span data-stu-id="0d016-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d016-116">\<smtp>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="0d016-116">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="0d016-117">設定簡單郵件傳輸通訊協定（SMTP）郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="0d016-117">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d016-118">備註</span><span class="sxs-lookup"><span data-stu-id="0d016-118">Remarks</span></span>  
 <span data-ttu-id="0d016-119">`specifiedPickupDirectory` 屬性會設定目錄，讓應用程式儲存郵件以供 SMTP 伺服器處理。</span><span class="sxs-lookup"><span data-stu-id="0d016-119">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d016-120">範例</span><span class="sxs-lookup"><span data-stu-id="0d016-120">Example</span></span>  
 <span data-ttu-id="0d016-121">下列範例會將 c:\maildrop 指定為郵件收取目錄。</span><span class="sxs-lookup"><span data-stu-id="0d016-121">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0d016-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d016-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="0d016-123">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0d016-123">Network Settings Schema</span></span>](index.md)
