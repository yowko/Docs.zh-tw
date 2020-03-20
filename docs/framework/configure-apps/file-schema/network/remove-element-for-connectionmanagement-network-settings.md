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
ms.openlocfilehash: 39ce85c3c15a2d4bdfce801a35e9ca088bd5091b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154734"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="eabbc-102">\<刪除連接管理的>元素（網路設置）</span><span class="sxs-lookup"><span data-stu-id="eabbc-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="eabbc-103">從連接管理清單中刪除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="eabbc-103">Removes an IP address or DNS name from the connection management list.</span></span>  

<span data-ttu-id="eabbc-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eabbc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eabbc-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="eabbc-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="eabbc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<連接管理>**](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="eabbc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="eabbc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<刪除>**</span><span class="sxs-lookup"><span data-stu-id="eabbc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="eabbc-108">語法</span><span class="sxs-lookup"><span data-stu-id="eabbc-108">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eabbc-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eabbc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eabbc-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="eabbc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eabbc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="eabbc-111">Attributes</span></span>  
  
|<span data-ttu-id="eabbc-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="eabbc-112">**Attribute**</span></span>|<span data-ttu-id="eabbc-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="eabbc-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="eabbc-114">IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="eabbc-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eabbc-115">子元素</span><span class="sxs-lookup"><span data-stu-id="eabbc-115">Child Elements</span></span>  
 <span data-ttu-id="eabbc-116">無。</span><span class="sxs-lookup"><span data-stu-id="eabbc-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eabbc-117">父項目</span><span class="sxs-lookup"><span data-stu-id="eabbc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="eabbc-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="eabbc-118">**Element**</span></span>|<span data-ttu-id="eabbc-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="eabbc-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="eabbc-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="eabbc-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="eabbc-121">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="eabbc-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eabbc-122">備註</span><span class="sxs-lookup"><span data-stu-id="eabbc-122">Remarks</span></span>  
 <span data-ttu-id="eabbc-123">該`remove`元素將刪除指定伺服器的連接管理清單條目。</span><span class="sxs-lookup"><span data-stu-id="eabbc-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="eabbc-124">`address`屬性的值應為有效的 IP 位址或主機名稱。</span><span class="sxs-lookup"><span data-stu-id="eabbc-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="eabbc-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="eabbc-125">Configuration Files</span></span>  
 <span data-ttu-id="eabbc-126">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="eabbc-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eabbc-127">範例</span><span class="sxs-lookup"><span data-stu-id="eabbc-127">Example</span></span>  
 <span data-ttu-id="eabbc-128">下面的示例刪除伺服器`www.adventure-works.com`的任何連接管理清單條目，然後將應用程式佈建為使用到伺服器`www.contoso.com`的四個連接和到所有其他伺服器的兩個連接。</span><span class="sxs-lookup"><span data-stu-id="eabbc-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eabbc-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eabbc-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="eabbc-130">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="eabbc-130">Network Settings Schema</span></span>](index.md)
