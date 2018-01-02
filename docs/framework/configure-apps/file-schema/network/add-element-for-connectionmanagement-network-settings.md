---
title: "&lt;新增&gt;connectionManagement （網路設定） 的項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 654ada55d30ad95937fa05475ebcbf23ca86652d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="34e39-102">&lt;新增&gt;connectionManagement （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="34e39-102">&lt;add&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="34e39-103">將 IP 位址或 DNS 名稱加入連線管理清單中。</span><span class="sxs-lookup"><span data-stu-id="34e39-103">Adds an IP address or DNS name to the connection management list.</span></span>  
  
 <span data-ttu-id="34e39-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="34e39-104">\<configuration></span></span>  
<span data-ttu-id="34e39-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="34e39-105">\<system.net></span></span>  
<span data-ttu-id="34e39-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="34e39-106">\<connectionManagement></span></span>  
<span data-ttu-id="34e39-107">\<add></span><span class="sxs-lookup"><span data-stu-id="34e39-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34e39-108">語法</span><span class="sxs-lookup"><span data-stu-id="34e39-108">Syntax</span></span>  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34e39-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="34e39-109">Attributes and Elements</span></span>  
 <span data-ttu-id="34e39-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="34e39-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34e39-111">屬性</span><span class="sxs-lookup"><span data-stu-id="34e39-111">Attributes</span></span>  
  
|<span data-ttu-id="34e39-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="34e39-112">**Attribute**</span></span>|<span data-ttu-id="34e39-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="34e39-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="34e39-114">描述 IP 位址或 DNS 名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="34e39-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="34e39-115">允許連接到伺服器的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="34e39-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="34e39-116">如果未提供，預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="34e39-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34e39-117">子元素</span><span class="sxs-lookup"><span data-stu-id="34e39-117">Child Elements</span></span>  
 <span data-ttu-id="34e39-118">無。</span><span class="sxs-lookup"><span data-stu-id="34e39-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34e39-119">父項目</span><span class="sxs-lookup"><span data-stu-id="34e39-119">Parent Elements</span></span>  
  
|<span data-ttu-id="34e39-120">**目**</span><span class="sxs-lookup"><span data-stu-id="34e39-120">**Element**</span></span>|<span data-ttu-id="34e39-121">**描述**</span><span class="sxs-lookup"><span data-stu-id="34e39-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="34e39-122">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="34e39-122">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="34e39-123">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="34e39-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34e39-124">備註</span><span class="sxs-lookup"><span data-stu-id="34e39-124">Remarks</span></span>  
 <span data-ttu-id="34e39-125">`address` 屬性的值應該是表示所有連線的星號，或是 `<schema>://<idn_hostname>[:<port>]` 格式的字串。</span><span class="sxs-lookup"><span data-stu-id="34e39-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="34e39-126">如果傳遞至任何 HTTP 應用程式開發介面的 URI 包含 Unicode，將會使用 <xref:System.Uri.DnsSafeHost%2A> 在內部轉換名稱，可能會傳回 punicode 字串 (行為取決於目前的 IDN 組態)。</span><span class="sxs-lookup"><span data-stu-id="34e39-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="34e39-127">組態檔</span><span class="sxs-lookup"><span data-stu-id="34e39-127">Configuration Files</span></span>  
 <span data-ttu-id="34e39-128">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="34e39-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34e39-129">範例</span><span class="sxs-lookup"><span data-stu-id="34e39-129">Example</span></span>  
 <span data-ttu-id="34e39-130">下列範例會設定應用程式使用四個連接至 www.contoso.com 伺服器和所有其他伺服器的兩個連線。</span><span class="sxs-lookup"><span data-stu-id="34e39-130">The following example configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34e39-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="34e39-131">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="34e39-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="34e39-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
