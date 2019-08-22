---
title: <mailSettings> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: b8ea08cbd76e60a3665703bc50924dd94500cd87
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659324"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="acd5a-102">\<mailSettings > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="acd5a-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="acd5a-103">設定郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="acd5a-103">Configures mail sending options.</span></span>  

<span data-ttu-id="acd5a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="acd5a-104">\<configuration></span></span>  
<span data-ttu-id="acd5a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="acd5a-105">\<system.net></span></span>  
<span data-ttu-id="acd5a-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="acd5a-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acd5a-107">語法</span><span class="sxs-lookup"><span data-stu-id="acd5a-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="acd5a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="acd5a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="acd5a-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="acd5a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="acd5a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="acd5a-110">Attributes</span></span>  
 <span data-ttu-id="acd5a-111">無。</span><span class="sxs-lookup"><span data-stu-id="acd5a-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="acd5a-112">子元素</span><span class="sxs-lookup"><span data-stu-id="acd5a-112">Child Elements</span></span>  
  
|<span data-ttu-id="acd5a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="acd5a-113">Attribute</span></span>|<span data-ttu-id="acd5a-114">描述</span><span class="sxs-lookup"><span data-stu-id="acd5a-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="acd5a-115">\<smtp > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="acd5a-115">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="acd5a-116">設定簡單郵件傳輸通訊協定選項。</span><span class="sxs-lookup"><span data-stu-id="acd5a-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="acd5a-117">父項目</span><span class="sxs-lookup"><span data-stu-id="acd5a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="acd5a-118">**目**</span><span class="sxs-lookup"><span data-stu-id="acd5a-118">**Element**</span></span>|<span data-ttu-id="acd5a-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="acd5a-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="acd5a-120">\<system.Net> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="acd5a-120">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="acd5a-121">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="acd5a-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="acd5a-122">範例</span><span class="sxs-lookup"><span data-stu-id="acd5a-122">Example</span></span>  
 <span data-ttu-id="acd5a-123">下列範例會指定適當的 SMTP 參數, 以使用預設網路認證來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="acd5a-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="acd5a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acd5a-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="acd5a-125">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="acd5a-125">Network Settings Schema</span></span>](index.md)
