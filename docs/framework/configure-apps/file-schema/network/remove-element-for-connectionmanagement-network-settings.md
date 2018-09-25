---
title: '&lt;移除&gt;connectionManagement （網路設定） 的項目'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d249cc412a1638e62b57b4976adc23fdf8f36e80
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085527"
---
# <a name="ltremovegt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="df725-102">&lt;移除&gt;connectionManagement （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="df725-102">&lt;remove&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="df725-103">從連線管理清單中，移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="df725-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="df725-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="df725-104">\<configuration></span></span>  
<span data-ttu-id="df725-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="df725-105">\<system.net></span></span>  
<span data-ttu-id="df725-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="df725-106">\<connectionManagement></span></span>  
<span data-ttu-id="df725-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="df725-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df725-108">語法</span><span class="sxs-lookup"><span data-stu-id="df725-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df725-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="df725-109">Attributes and Elements</span></span>  
 <span data-ttu-id="df725-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="df725-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df725-111">屬性</span><span class="sxs-lookup"><span data-stu-id="df725-111">Attributes</span></span>  
  
|<span data-ttu-id="df725-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="df725-112">**Attribute**</span></span>|<span data-ttu-id="df725-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="df725-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="df725-114">IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="df725-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df725-115">子元素</span><span class="sxs-lookup"><span data-stu-id="df725-115">Child Elements</span></span>  
 <span data-ttu-id="df725-116">無。</span><span class="sxs-lookup"><span data-stu-id="df725-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df725-117">父項目</span><span class="sxs-lookup"><span data-stu-id="df725-117">Parent Elements</span></span>  
  
|<span data-ttu-id="df725-118">**目**</span><span class="sxs-lookup"><span data-stu-id="df725-118">**Element**</span></span>|<span data-ttu-id="df725-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="df725-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="df725-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="df725-120">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="df725-121">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="df725-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df725-122">備註</span><span class="sxs-lookup"><span data-stu-id="df725-122">Remarks</span></span>  
 <span data-ttu-id="df725-123">`remove`項目移除指定的伺服器的連線管理清單項目。</span><span class="sxs-lookup"><span data-stu-id="df725-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="df725-124">值`address`屬性應為有效的 IP 位址或主機名稱。</span><span class="sxs-lookup"><span data-stu-id="df725-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="df725-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="df725-125">Configuration Files</span></span>  
 <span data-ttu-id="df725-126">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="df725-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df725-127">範例</span><span class="sxs-lookup"><span data-stu-id="df725-127">Example</span></span>  
 <span data-ttu-id="df725-128">下列範例會移除伺服器 www.adventure-works.com 任何連線管理清單項目，並設定應用程式使用四個連接至 www.contoso.com 伺服器和兩個連線到所有其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="df725-128">The following example removes any connection management list entries for the server www.adventure-works.com and then configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df725-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df725-129">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="df725-130">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="df725-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
