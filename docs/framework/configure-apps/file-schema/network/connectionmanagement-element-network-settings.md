---
title: '&lt;connectionManagement&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
author: mcleblanc
ms.author: markl
ms.openlocfilehash: bc0b75db5b3f35087df70c9155a1ba3b39ceae4d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47173066"
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a><span data-ttu-id="6244f-102">&lt;connectionManagement&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="6244f-102">&lt;connectionManagement&gt; Element (Network Settings)</span></span>
<span data-ttu-id="6244f-103">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="6244f-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="6244f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6244f-104">\<configuration></span></span>  
<span data-ttu-id="6244f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="6244f-105">\<system.net></span></span>  
<span data-ttu-id="6244f-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="6244f-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6244f-107">語法</span><span class="sxs-lookup"><span data-stu-id="6244f-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6244f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6244f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6244f-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6244f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6244f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6244f-110">Attributes</span></span>  
 <span data-ttu-id="6244f-111">無。</span><span class="sxs-lookup"><span data-stu-id="6244f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6244f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="6244f-112">Child Elements</span></span>  
  
|<span data-ttu-id="6244f-113">**目**</span><span class="sxs-lookup"><span data-stu-id="6244f-113">**Element**</span></span>|<span data-ttu-id="6244f-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="6244f-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6244f-115">add</span><span class="sxs-lookup"><span data-stu-id="6244f-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="6244f-116">將 IP 位址或 DNS 名稱加入連線管理清單中。</span><span class="sxs-lookup"><span data-stu-id="6244f-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="6244f-117">clear</span><span class="sxs-lookup"><span data-stu-id="6244f-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="6244f-118">清除連接管理清單中。</span><span class="sxs-lookup"><span data-stu-id="6244f-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="6244f-119">remove</span><span class="sxs-lookup"><span data-stu-id="6244f-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="6244f-120">從連線管理清單中，移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="6244f-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6244f-121">父項目</span><span class="sxs-lookup"><span data-stu-id="6244f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6244f-122">**目**</span><span class="sxs-lookup"><span data-stu-id="6244f-122">**Element**</span></span>|<span data-ttu-id="6244f-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="6244f-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6244f-124">system.net</span><span class="sxs-lookup"><span data-stu-id="6244f-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="6244f-125">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="6244f-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6244f-126">備註</span><span class="sxs-lookup"><span data-stu-id="6244f-126">Remarks</span></span>  
 <span data-ttu-id="6244f-127">`connectionManagement`項目至伺服器或伺服器群組中定義的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="6244f-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6244f-128">組態檔</span><span class="sxs-lookup"><span data-stu-id="6244f-128">Configuration Files</span></span>  
 <span data-ttu-id="6244f-129">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="6244f-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6244f-130">範例</span><span class="sxs-lookup"><span data-stu-id="6244f-130">Example</span></span>  
 <span data-ttu-id="6244f-131">下列範例會設定應用程式使用四個連接至 www.contoso.com 伺服器和兩個連線到所有其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="6244f-131">The following example configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6244f-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6244f-132">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="6244f-133">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6244f-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
