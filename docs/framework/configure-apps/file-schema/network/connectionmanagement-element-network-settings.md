---
title: <connectionManagement> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 9f1e382bbbaad2cb95e2c33bbbdfb4c505378c9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154890"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="b1199-102">\<connectionManagement> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="b1199-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="b1199-103">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="b1199-103">Specifies the maximum number of connections to a network host.</span></span>  

<span data-ttu-id="b1199-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1199-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b1199-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b1199-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="b1199-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<連接管理>**</span><span class="sxs-lookup"><span data-stu-id="b1199-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b1199-107">語法</span><span class="sxs-lookup"><span data-stu-id="b1199-107">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1199-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b1199-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b1199-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b1199-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1199-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b1199-110">Attributes</span></span>  
 <span data-ttu-id="b1199-111">無。</span><span class="sxs-lookup"><span data-stu-id="b1199-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b1199-112">子元素</span><span class="sxs-lookup"><span data-stu-id="b1199-112">Child Elements</span></span>  
  
|<span data-ttu-id="b1199-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="b1199-113">**Element**</span></span>|<span data-ttu-id="b1199-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="b1199-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b1199-115">新增</span><span class="sxs-lookup"><span data-stu-id="b1199-115">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="b1199-116">將 IP 位址或 DNS 名稱加入連線管理清單中。</span><span class="sxs-lookup"><span data-stu-id="b1199-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="b1199-117">清楚</span><span class="sxs-lookup"><span data-stu-id="b1199-117">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="b1199-118">清除連接管理清單。</span><span class="sxs-lookup"><span data-stu-id="b1199-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="b1199-119">移除</span><span class="sxs-lookup"><span data-stu-id="b1199-119">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="b1199-120">從連接管理清單中刪除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="b1199-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1199-121">父項目</span><span class="sxs-lookup"><span data-stu-id="b1199-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b1199-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="b1199-122">**Element**</span></span>|<span data-ttu-id="b1199-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="b1199-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b1199-124">system.net</span><span class="sxs-lookup"><span data-stu-id="b1199-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="b1199-125">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="b1199-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1199-126">備註</span><span class="sxs-lookup"><span data-stu-id="b1199-126">Remarks</span></span>  
 <span data-ttu-id="b1199-127">該`connectionManagement`元素定義與伺服器或伺服器組的最大連接數。</span><span class="sxs-lookup"><span data-stu-id="b1199-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b1199-128">組態檔</span><span class="sxs-lookup"><span data-stu-id="b1199-128">Configuration Files</span></span>  
 <span data-ttu-id="b1199-129">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="b1199-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1199-130">範例</span><span class="sxs-lookup"><span data-stu-id="b1199-130">Example</span></span>  
 <span data-ttu-id="b1199-131">下面的示例將應用程式佈建為使用到伺服器`www.contoso.com`的四個連接和到所有其他伺服器的兩個連接。</span><span class="sxs-lookup"><span data-stu-id="b1199-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1199-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1199-132">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="b1199-133">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="b1199-133">Network Settings Schema</span></span>](index.md)
