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
ms.openlocfilehash: 54fb68ab0bf8aa2665d70391350c626131ccb4bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180619"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="e5d25-102">\<mailSettings > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="e5d25-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="e5d25-103">設定郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="e5d25-103">Configures mail sending options.</span></span>  

<span data-ttu-id="e5d25-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e5d25-104">\<configuration></span></span>  
<span data-ttu-id="e5d25-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e5d25-105">\<system.net></span></span>  
<span data-ttu-id="e5d25-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="e5d25-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5d25-107">語法</span><span class="sxs-lookup"><span data-stu-id="e5d25-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5d25-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e5d25-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e5d25-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e5d25-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5d25-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e5d25-110">Attributes</span></span>  
 <span data-ttu-id="e5d25-111">無。</span><span class="sxs-lookup"><span data-stu-id="e5d25-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e5d25-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e5d25-112">Child Elements</span></span>  
  
|<span data-ttu-id="e5d25-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e5d25-113">Attribute</span></span>|<span data-ttu-id="e5d25-114">描述</span><span class="sxs-lookup"><span data-stu-id="e5d25-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="e5d25-115">\<smtp > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="e5d25-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="e5d25-116">設定簡易郵件傳輸通訊協定選項。</span><span class="sxs-lookup"><span data-stu-id="e5d25-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5d25-117">父項目</span><span class="sxs-lookup"><span data-stu-id="e5d25-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e5d25-118">**目**</span><span class="sxs-lookup"><span data-stu-id="e5d25-118">**Element**</span></span>|<span data-ttu-id="e5d25-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="e5d25-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e5d25-120">\<system.Net> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="e5d25-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="e5d25-121">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="e5d25-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e5d25-122">範例</span><span class="sxs-lookup"><span data-stu-id="e5d25-122">Example</span></span>  
 <span data-ttu-id="e5d25-123">下列範例會指定適當的 SMTP 參數，使用預設網路認證傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="e5d25-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e5d25-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5d25-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="e5d25-125">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e5d25-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
