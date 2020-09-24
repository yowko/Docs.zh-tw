---
title: <mailSettings> 項目 (網路設定)
description: <mailSettings>網路設定元素會設定 .NET Framework 中的郵件傳送選項。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: a146874acc21f52507b37b1751c648792e23c8bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158847"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="c1a7f-103">\<mailSettings> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="c1a7f-103">\<mailSettings> Element (Network Settings)</span></span>

<span data-ttu-id="c1a7f-104">設定郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="c1a7f-104">Configures mail sending options.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a><span data-ttu-id="c1a7f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c1a7f-105">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1a7f-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c1a7f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c1a7f-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c1a7f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1a7f-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c1a7f-108">Attributes</span></span>  

 <span data-ttu-id="c1a7f-109">無。</span><span class="sxs-lookup"><span data-stu-id="c1a7f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c1a7f-110">子元素</span><span class="sxs-lookup"><span data-stu-id="c1a7f-110">Child Elements</span></span>  
  
|<span data-ttu-id="c1a7f-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c1a7f-111">Attribute</span></span>|<span data-ttu-id="c1a7f-112">描述</span><span class="sxs-lookup"><span data-stu-id="c1a7f-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c1a7f-113">\<smtp> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="c1a7f-113">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="c1a7f-114">設定簡易郵件傳輸通訊協定選項。</span><span class="sxs-lookup"><span data-stu-id="c1a7f-114">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1a7f-115">父項目</span><span class="sxs-lookup"><span data-stu-id="c1a7f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c1a7f-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="c1a7f-116">**Element**</span></span>|<span data-ttu-id="c1a7f-117">**說明**</span><span class="sxs-lookup"><span data-stu-id="c1a7f-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c1a7f-118">\<system.Net> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="c1a7f-118">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="c1a7f-119">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="c1a7f-119">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c1a7f-120">範例</span><span class="sxs-lookup"><span data-stu-id="c1a7f-120">Example</span></span>  

 <span data-ttu-id="c1a7f-121">下列範例會指定適當的 SMTP 參數，以使用預設網路認證來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="c1a7f-121">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c1a7f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1a7f-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="c1a7f-123">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c1a7f-123">Network Settings Schema</span></span>](index.md)
