---
title: connectionManagement 的 <add> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: 3742a040e8c16c38e495a0fd886c4c1f23780758
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698378"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="5e7ee-102">適用于 Connectionmanagement 專案的 @no__t 0add > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="5e7ee-102">\<add> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="5e7ee-103">將 IP 位址或 DNS 名稱加入連線管理清單中。</span><span class="sxs-lookup"><span data-stu-id="5e7ee-103">Adds an IP address or DNS name to the connection management list.</span></span>  
  
[<span data-ttu-id="5e7ee-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="5e7ee-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="5e7ee-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5e7ee-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="5e7ee-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5e7ee-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>  
<span data-ttu-id="5e7ee-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="5e7ee-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e7ee-108">語法</span><span class="sxs-lookup"><span data-stu-id="5e7ee-108">Syntax</span></span>  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e7ee-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5e7ee-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5e7ee-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5e7ee-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e7ee-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5e7ee-111">Attributes</span></span>  
  
|<span data-ttu-id="5e7ee-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="5e7ee-112">**Attribute**</span></span>|<span data-ttu-id="5e7ee-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="5e7ee-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="5e7ee-114">描述 IP 位址或 DNS 名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="5e7ee-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="5e7ee-115">允許連接到伺服器的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="5e7ee-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="5e7ee-116">如果未提供，預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="5e7ee-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e7ee-117">子元素</span><span class="sxs-lookup"><span data-stu-id="5e7ee-117">Child Elements</span></span>  
 <span data-ttu-id="5e7ee-118">無。</span><span class="sxs-lookup"><span data-stu-id="5e7ee-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e7ee-119">父項目</span><span class="sxs-lookup"><span data-stu-id="5e7ee-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5e7ee-120">**目**</span><span class="sxs-lookup"><span data-stu-id="5e7ee-120">**Element**</span></span>|<span data-ttu-id="5e7ee-121">**描述**</span><span class="sxs-lookup"><span data-stu-id="5e7ee-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5e7ee-122">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="5e7ee-122">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="5e7ee-123">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="5e7ee-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e7ee-124">備註</span><span class="sxs-lookup"><span data-stu-id="5e7ee-124">Remarks</span></span>  
 <span data-ttu-id="5e7ee-125">`address` 屬性的值應該是表示所有連線的星號，或是 `<schema>://<idn_hostname>[:<port>]` 格式的字串。</span><span class="sxs-lookup"><span data-stu-id="5e7ee-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="5e7ee-126">如果傳遞至任何 HTTP 應用程式開發介面的 URI 包含 Unicode，將會使用 <xref:System.Uri.DnsSafeHost%2A> 在內部轉換名稱，可能會傳回 punicode 字串 (行為取決於目前的 IDN 組態)。</span><span class="sxs-lookup"><span data-stu-id="5e7ee-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5e7ee-127">組態檔</span><span class="sxs-lookup"><span data-stu-id="5e7ee-127">Configuration Files</span></span>  
 <span data-ttu-id="5e7ee-128">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="5e7ee-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e7ee-129">範例</span><span class="sxs-lookup"><span data-stu-id="5e7ee-129">Example</span></span>  
 <span data-ttu-id="5e7ee-130">下列範例會將應用程式設定為使用與伺服器的四個連接 `www.contoso.com`，以及兩個與其他伺服器的連線。</span><span class="sxs-lookup"><span data-stu-id="5e7ee-130">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5e7ee-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e7ee-131">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="5e7ee-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5e7ee-132">Network Settings Schema</span></span>](index.md)
