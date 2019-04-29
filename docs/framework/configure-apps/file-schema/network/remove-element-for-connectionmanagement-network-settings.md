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
ms.openlocfilehash: d9c584fb2faa971e7ce1ca287a94c8c6129820fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705190"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="c5abb-102">\<移除 > connectionManagement （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="c5abb-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="c5abb-103">從連線管理清單中，移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="c5abb-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="c5abb-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c5abb-104">\<configuration></span></span>  
<span data-ttu-id="c5abb-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c5abb-105">\<system.net></span></span>  
<span data-ttu-id="c5abb-106">\<connectionManagement></span><span class="sxs-lookup"><span data-stu-id="c5abb-106">\<connectionManagement></span></span>  
<span data-ttu-id="c5abb-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="c5abb-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5abb-108">語法</span><span class="sxs-lookup"><span data-stu-id="c5abb-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5abb-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c5abb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c5abb-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c5abb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5abb-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c5abb-111">Attributes</span></span>  
  
|<span data-ttu-id="c5abb-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="c5abb-112">**Attribute**</span></span>|<span data-ttu-id="c5abb-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="c5abb-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="c5abb-114">IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="c5abb-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5abb-115">子元素</span><span class="sxs-lookup"><span data-stu-id="c5abb-115">Child Elements</span></span>  
 <span data-ttu-id="c5abb-116">無。</span><span class="sxs-lookup"><span data-stu-id="c5abb-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5abb-117">父項目</span><span class="sxs-lookup"><span data-stu-id="c5abb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c5abb-118">**目**</span><span class="sxs-lookup"><span data-stu-id="c5abb-118">**Element**</span></span>|<span data-ttu-id="c5abb-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="c5abb-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c5abb-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="c5abb-120">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="c5abb-121">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="c5abb-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5abb-122">備註</span><span class="sxs-lookup"><span data-stu-id="c5abb-122">Remarks</span></span>  
 <span data-ttu-id="c5abb-123">`remove`項目移除指定的伺服器的連線管理清單項目。</span><span class="sxs-lookup"><span data-stu-id="c5abb-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="c5abb-124">值`address`屬性應為有效的 IP 位址或主機名稱。</span><span class="sxs-lookup"><span data-stu-id="c5abb-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c5abb-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="c5abb-125">Configuration Files</span></span>  
 <span data-ttu-id="c5abb-126">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="c5abb-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5abb-127">範例</span><span class="sxs-lookup"><span data-stu-id="c5abb-127">Example</span></span>  
 <span data-ttu-id="c5abb-128">下列範例會移除伺服器的任何連線管理清單項目`www.adventure-works.com`，然後設定 應用程式使用伺服器的四個通往`www.contoso.com`和所有其他伺服器的兩個連線。</span><span class="sxs-lookup"><span data-stu-id="c5abb-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5abb-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5abb-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="c5abb-130">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c5abb-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
