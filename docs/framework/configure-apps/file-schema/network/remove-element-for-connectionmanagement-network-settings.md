---
title: connectionManagement 的 <remove> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: cbafd29be6855cbb95d17388791ba152230295cc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697847"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="4d2dc-102">適用于 Connectionmanagement 專案的 @no__t 0remove > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="4d2dc-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="4d2dc-103">從連接管理清單中移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="4d2dc-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
[<span data-ttu-id="4d2dc-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="4d2dc-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="4d2dc-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="4d2dc-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="4d2dc-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="4d2dc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>  
<span data-ttu-id="4d2dc-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="4d2dc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d2dc-108">語法</span><span class="sxs-lookup"><span data-stu-id="4d2dc-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d2dc-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4d2dc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4d2dc-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4d2dc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d2dc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4d2dc-111">Attributes</span></span>  
  
|<span data-ttu-id="4d2dc-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="4d2dc-112">**Attribute**</span></span>|<span data-ttu-id="4d2dc-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="4d2dc-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="4d2dc-114">IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="4d2dc-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d2dc-115">子元素</span><span class="sxs-lookup"><span data-stu-id="4d2dc-115">Child Elements</span></span>  
 <span data-ttu-id="4d2dc-116">無。</span><span class="sxs-lookup"><span data-stu-id="4d2dc-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d2dc-117">父項目</span><span class="sxs-lookup"><span data-stu-id="4d2dc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4d2dc-118">**目**</span><span class="sxs-lookup"><span data-stu-id="4d2dc-118">**Element**</span></span>|<span data-ttu-id="4d2dc-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="4d2dc-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4d2dc-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="4d2dc-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="4d2dc-121">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="4d2dc-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d2dc-122">備註</span><span class="sxs-lookup"><span data-stu-id="4d2dc-122">Remarks</span></span>  
 <span data-ttu-id="4d2dc-123">@No__t-0 元素會移除指定之伺服器的連接管理清單專案。</span><span class="sxs-lookup"><span data-stu-id="4d2dc-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="4d2dc-124">@No__t-0 屬性的值應為有效的 IP 位址或主機名稱。</span><span class="sxs-lookup"><span data-stu-id="4d2dc-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4d2dc-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="4d2dc-125">Configuration Files</span></span>  
 <span data-ttu-id="4d2dc-126">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="4d2dc-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d2dc-127">範例</span><span class="sxs-lookup"><span data-stu-id="4d2dc-127">Example</span></span>  
 <span data-ttu-id="4d2dc-128">下列範例會移除伺服器 `www.adventure-works.com` 的任何連接管理清單專案，然後將應用程式設定為使用伺服器的四個連接 `www.contoso.com`，以及兩個與其他伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="4d2dc-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d2dc-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d2dc-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="4d2dc-130">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="4d2dc-130">Network Settings Schema</span></span>](index.md)
