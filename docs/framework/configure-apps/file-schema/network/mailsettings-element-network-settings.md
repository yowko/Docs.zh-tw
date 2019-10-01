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
ms.openlocfilehash: fb4c8844ed3eb13af483c214d659090c0c563c33
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698083"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="de6b1-102">@no__t 0mailSettings > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="de6b1-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="de6b1-103">設定郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="de6b1-103">Configures mail sending options.</span></span>  

[<span data-ttu-id="de6b1-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="de6b1-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="de6b1-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="de6b1-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="de6b1-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<mailSettings >**</span><span class="sxs-lookup"><span data-stu-id="de6b1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de6b1-107">語法</span><span class="sxs-lookup"><span data-stu-id="de6b1-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de6b1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="de6b1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="de6b1-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="de6b1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de6b1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="de6b1-110">Attributes</span></span>  
 <span data-ttu-id="de6b1-111">無。</span><span class="sxs-lookup"><span data-stu-id="de6b1-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de6b1-112">子元素</span><span class="sxs-lookup"><span data-stu-id="de6b1-112">Child Elements</span></span>  
  
|<span data-ttu-id="de6b1-113">屬性</span><span class="sxs-lookup"><span data-stu-id="de6b1-113">Attribute</span></span>|<span data-ttu-id="de6b1-114">描述</span><span class="sxs-lookup"><span data-stu-id="de6b1-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="de6b1-115">@no__t 1smtp > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="de6b1-115">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="de6b1-116">設定簡單郵件傳輸通訊協定選項。</span><span class="sxs-lookup"><span data-stu-id="de6b1-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de6b1-117">父項目</span><span class="sxs-lookup"><span data-stu-id="de6b1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="de6b1-118">**目**</span><span class="sxs-lookup"><span data-stu-id="de6b1-118">**Element**</span></span>|<span data-ttu-id="de6b1-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="de6b1-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="de6b1-120">\<system.Net> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="de6b1-120">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="de6b1-121">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="de6b1-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="de6b1-122">範例</span><span class="sxs-lookup"><span data-stu-id="de6b1-122">Example</span></span>  
 <span data-ttu-id="de6b1-123">下列範例會指定適當的 SMTP 參數，以使用預設網路認證來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="de6b1-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="de6b1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de6b1-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="de6b1-125">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="de6b1-125">Network Settings Schema</span></span>](index.md)
