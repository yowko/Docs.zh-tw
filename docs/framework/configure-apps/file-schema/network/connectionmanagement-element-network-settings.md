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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154890"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="7cca4-102">\<connectionManagement> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="7cca4-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="7cca4-103">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="7cca4-103">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="7cca4-104">語法</span><span class="sxs-lookup"><span data-stu-id="7cca4-104">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cca4-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7cca4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7cca4-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7cca4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cca4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="7cca4-107">Attributes</span></span>  
 <span data-ttu-id="7cca4-108">無。</span><span class="sxs-lookup"><span data-stu-id="7cca4-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7cca4-109">子元素</span><span class="sxs-lookup"><span data-stu-id="7cca4-109">Child Elements</span></span>  
  
|<span data-ttu-id="7cca4-110">**元素**</span><span class="sxs-lookup"><span data-stu-id="7cca4-110">**Element**</span></span>|<span data-ttu-id="7cca4-111">**說明**</span><span class="sxs-lookup"><span data-stu-id="7cca4-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7cca4-112">add</span><span class="sxs-lookup"><span data-stu-id="7cca4-112">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="7cca4-113">將 IP 位址或 DNS 名稱加入連線管理清單中。</span><span class="sxs-lookup"><span data-stu-id="7cca4-113">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="7cca4-114">明確</span><span class="sxs-lookup"><span data-stu-id="7cca4-114">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="7cca4-115">清除連接管理清單。</span><span class="sxs-lookup"><span data-stu-id="7cca4-115">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="7cca4-116">remove</span><span class="sxs-lookup"><span data-stu-id="7cca4-116">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="7cca4-117">從連接管理清單中移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="7cca4-117">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7cca4-118">父項目</span><span class="sxs-lookup"><span data-stu-id="7cca4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7cca4-119">**元素**</span><span class="sxs-lookup"><span data-stu-id="7cca4-119">**Element**</span></span>|<span data-ttu-id="7cca4-120">**說明**</span><span class="sxs-lookup"><span data-stu-id="7cca4-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7cca4-121">system.net</span><span class="sxs-lookup"><span data-stu-id="7cca4-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="7cca4-122">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="7cca4-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cca4-123">備註</span><span class="sxs-lookup"><span data-stu-id="7cca4-123">Remarks</span></span>  
 <span data-ttu-id="7cca4-124">`connectionManagement`元素會定義伺服器或伺服器群組的最大連接數目。</span><span class="sxs-lookup"><span data-stu-id="7cca4-124">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7cca4-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="7cca4-125">Configuration Files</span></span>  
 <span data-ttu-id="7cca4-126">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="7cca4-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cca4-127">範例</span><span class="sxs-lookup"><span data-stu-id="7cca4-127">Example</span></span>  
 <span data-ttu-id="7cca4-128">下列範例會將應用程式設定為使用伺服器的四個連接 `www.contoso.com` ，以及兩個連接到其他所有伺服器。</span><span class="sxs-lookup"><span data-stu-id="7cca4-128">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7cca4-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cca4-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="7cca4-130">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7cca4-130">Network Settings Schema</span></span>](index.md)
