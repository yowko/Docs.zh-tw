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
ms.openlocfilehash: 8ab7a43fbb3e8df5bb0c99b5947f2fafb362399a
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664035"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="1855a-102">\<移除 Connectionmanagement 專案的 > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="1855a-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="1855a-103">從連接管理清單中移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="1855a-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="1855a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1855a-104">\<configuration></span></span>  
<span data-ttu-id="1855a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="1855a-105">\<system.net></span></span>  
<span data-ttu-id="1855a-106">\<connectionManagement></span><span class="sxs-lookup"><span data-stu-id="1855a-106">\<connectionManagement></span></span>  
<span data-ttu-id="1855a-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="1855a-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1855a-108">語法</span><span class="sxs-lookup"><span data-stu-id="1855a-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1855a-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1855a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1855a-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1855a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1855a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1855a-111">Attributes</span></span>  
  
|<span data-ttu-id="1855a-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="1855a-112">**Attribute**</span></span>|<span data-ttu-id="1855a-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="1855a-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="1855a-114">IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="1855a-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1855a-115">子元素</span><span class="sxs-lookup"><span data-stu-id="1855a-115">Child Elements</span></span>  
 <span data-ttu-id="1855a-116">無。</span><span class="sxs-lookup"><span data-stu-id="1855a-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1855a-117">父項目</span><span class="sxs-lookup"><span data-stu-id="1855a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1855a-118">**目**</span><span class="sxs-lookup"><span data-stu-id="1855a-118">**Element**</span></span>|<span data-ttu-id="1855a-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="1855a-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1855a-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="1855a-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="1855a-121">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="1855a-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1855a-122">備註</span><span class="sxs-lookup"><span data-stu-id="1855a-122">Remarks</span></span>  
 <span data-ttu-id="1855a-123">`remove`元素會移除指定之伺服器的連接管理清單專案。</span><span class="sxs-lookup"><span data-stu-id="1855a-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="1855a-124">`address`屬性的值應為有效的 IP 位址或主機名稱。</span><span class="sxs-lookup"><span data-stu-id="1855a-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1855a-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="1855a-125">Configuration Files</span></span>  
 <span data-ttu-id="1855a-126">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="1855a-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1855a-127">範例</span><span class="sxs-lookup"><span data-stu-id="1855a-127">Example</span></span>  
 <span data-ttu-id="1855a-128">下列範例會移除伺服器`www.adventure-works.com`的任何連接管理清單專案, 然後將應用程式設定為使用四個伺服器`www.contoso.com`連線, 以及兩個連接到其他所有伺服器。</span><span class="sxs-lookup"><span data-stu-id="1855a-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1855a-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1855a-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="1855a-130">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1855a-130">Network Settings Schema</span></span>](index.md)
