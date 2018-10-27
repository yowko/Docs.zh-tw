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
ms.openlocfilehash: ff2f895ca50f0d16ee9e16406f92b087b03e391e
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2018
ms.locfileid: "50049109"
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a><span data-ttu-id="d18a2-102">&lt;connectionManagement&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="d18a2-102">&lt;connectionManagement&gt; Element (Network Settings)</span></span>
<span data-ttu-id="d18a2-103">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="d18a2-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="d18a2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d18a2-104">\<configuration></span></span>  
<span data-ttu-id="d18a2-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d18a2-105">\<system.net></span></span>  
<span data-ttu-id="d18a2-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="d18a2-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d18a2-107">語法</span><span class="sxs-lookup"><span data-stu-id="d18a2-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d18a2-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d18a2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d18a2-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d18a2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d18a2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d18a2-110">Attributes</span></span>  
 <span data-ttu-id="d18a2-111">無。</span><span class="sxs-lookup"><span data-stu-id="d18a2-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d18a2-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d18a2-112">Child Elements</span></span>  
  
|<span data-ttu-id="d18a2-113">**目**</span><span class="sxs-lookup"><span data-stu-id="d18a2-113">**Element**</span></span>|<span data-ttu-id="d18a2-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="d18a2-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d18a2-115">add</span><span class="sxs-lookup"><span data-stu-id="d18a2-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="d18a2-116">將 IP 位址或 DNS 名稱加入連線管理清單中。</span><span class="sxs-lookup"><span data-stu-id="d18a2-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="d18a2-117">clear</span><span class="sxs-lookup"><span data-stu-id="d18a2-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="d18a2-118">清除連接管理清單中。</span><span class="sxs-lookup"><span data-stu-id="d18a2-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="d18a2-119">remove</span><span class="sxs-lookup"><span data-stu-id="d18a2-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="d18a2-120">從連線管理清單中，移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="d18a2-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d18a2-121">父項目</span><span class="sxs-lookup"><span data-stu-id="d18a2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d18a2-122">**目**</span><span class="sxs-lookup"><span data-stu-id="d18a2-122">**Element**</span></span>|<span data-ttu-id="d18a2-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="d18a2-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d18a2-124">system.net</span><span class="sxs-lookup"><span data-stu-id="d18a2-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="d18a2-125">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="d18a2-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d18a2-126">備註</span><span class="sxs-lookup"><span data-stu-id="d18a2-126">Remarks</span></span>  
 <span data-ttu-id="d18a2-127">`connectionManagement`項目至伺服器或伺服器群組中定義的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="d18a2-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d18a2-128">組態檔</span><span class="sxs-lookup"><span data-stu-id="d18a2-128">Configuration Files</span></span>  
 <span data-ttu-id="d18a2-129">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="d18a2-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d18a2-130">範例</span><span class="sxs-lookup"><span data-stu-id="d18a2-130">Example</span></span>  
 <span data-ttu-id="d18a2-131">下列範例會設定應用程式使用伺服器的四個通往`www.contoso.com`和所有其他伺服器的兩個連線。</span><span class="sxs-lookup"><span data-stu-id="d18a2-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d18a2-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d18a2-132">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="d18a2-133">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d18a2-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
