---
title: <mailSettings> 項目 (網路設定)
description: <mailSettings>Network settings 元素會設定 .NET Framework 中的郵件傳送選項。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: ce7b8564e4ee5ea73d42259612c077420d36645b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504559"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="c1ee2-103">\<mailSettings> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="c1ee2-103">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="c1ee2-104">設定郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="c1ee2-104">Configures mail sending options.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a><span data-ttu-id="c1ee2-105">語法</span><span class="sxs-lookup"><span data-stu-id="c1ee2-105">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1ee2-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c1ee2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c1ee2-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c1ee2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1ee2-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c1ee2-108">Attributes</span></span>  
 <span data-ttu-id="c1ee2-109">無。</span><span class="sxs-lookup"><span data-stu-id="c1ee2-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c1ee2-110">子元素</span><span class="sxs-lookup"><span data-stu-id="c1ee2-110">Child Elements</span></span>  
  
|<span data-ttu-id="c1ee2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c1ee2-111">Attribute</span></span>|<span data-ttu-id="c1ee2-112">說明</span><span class="sxs-lookup"><span data-stu-id="c1ee2-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c1ee2-113">\<smtp>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="c1ee2-113">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="c1ee2-114">設定簡單郵件傳輸通訊協定選項。</span><span class="sxs-lookup"><span data-stu-id="c1ee2-114">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1ee2-115">父項目</span><span class="sxs-lookup"><span data-stu-id="c1ee2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c1ee2-116">**元素**</span><span class="sxs-lookup"><span data-stu-id="c1ee2-116">**Element**</span></span>|<span data-ttu-id="c1ee2-117">**描述**</span><span class="sxs-lookup"><span data-stu-id="c1ee2-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c1ee2-118">\<system.Net>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="c1ee2-118">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="c1ee2-119">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="c1ee2-119">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c1ee2-120">範例</span><span class="sxs-lookup"><span data-stu-id="c1ee2-120">Example</span></span>  
 <span data-ttu-id="c1ee2-121">下列範例會指定適當的 SMTP 參數，以使用預設網路認證來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="c1ee2-121">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c1ee2-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1ee2-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="c1ee2-123">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c1ee2-123">Network Settings Schema</span></span>](index.md)
