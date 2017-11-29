---
title: "&lt;connectionManagement&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e3380ce1e8e798740214feee0e76d9949caa6bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a><span data-ttu-id="c0d79-102">&lt;connectionManagement&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="c0d79-102">&lt;connectionManagement&gt; Element (Network Settings)</span></span>
<span data-ttu-id="c0d79-103">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="c0d79-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="c0d79-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c0d79-104">\<configuration></span></span>  
<span data-ttu-id="c0d79-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="c0d79-105">\<system.net></span></span>  
<span data-ttu-id="c0d79-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="c0d79-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0d79-107">語法</span><span class="sxs-lookup"><span data-stu-id="c0d79-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0d79-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c0d79-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c0d79-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c0d79-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0d79-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c0d79-110">Attributes</span></span>  
 <span data-ttu-id="c0d79-111">無。</span><span class="sxs-lookup"><span data-stu-id="c0d79-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c0d79-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c0d79-112">Child Elements</span></span>  
  
|<span data-ttu-id="c0d79-113">**目**</span><span class="sxs-lookup"><span data-stu-id="c0d79-113">**Element**</span></span>|<span data-ttu-id="c0d79-114">**說明**</span><span class="sxs-lookup"><span data-stu-id="c0d79-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c0d79-115">add</span><span class="sxs-lookup"><span data-stu-id="c0d79-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="c0d79-116">將 IP 位址或 DNS 名稱加入連線管理清單中。</span><span class="sxs-lookup"><span data-stu-id="c0d79-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="c0d79-117">clear</span><span class="sxs-lookup"><span data-stu-id="c0d79-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="c0d79-118">清除連線管理清單中。</span><span class="sxs-lookup"><span data-stu-id="c0d79-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="c0d79-119">remove</span><span class="sxs-lookup"><span data-stu-id="c0d79-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="c0d79-120">從連線管理清單中移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="c0d79-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0d79-121">父項目</span><span class="sxs-lookup"><span data-stu-id="c0d79-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c0d79-122">**目**</span><span class="sxs-lookup"><span data-stu-id="c0d79-122">**Element**</span></span>|<span data-ttu-id="c0d79-123">**說明**</span><span class="sxs-lookup"><span data-stu-id="c0d79-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c0d79-124">system.net</span><span class="sxs-lookup"><span data-stu-id="c0d79-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="c0d79-125">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="c0d79-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0d79-126">備註</span><span class="sxs-lookup"><span data-stu-id="c0d79-126">Remarks</span></span>  
 <span data-ttu-id="c0d79-127">`connectionManagement`元素以伺服器或伺服器群組中定義的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="c0d79-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c0d79-128">組態檔</span><span class="sxs-lookup"><span data-stu-id="c0d79-128">Configuration Files</span></span>  
 <span data-ttu-id="c0d79-129">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="c0d79-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0d79-130">範例</span><span class="sxs-lookup"><span data-stu-id="c0d79-130">Example</span></span>  
 <span data-ttu-id="c0d79-131">下列範例會設定應用程式使用四個連接至 www.contoso.com 伺服器和所有其他伺服器的兩個連線。</span><span class="sxs-lookup"><span data-stu-id="c0d79-131">The following example configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0d79-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0d79-132">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="c0d79-133">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c0d79-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
