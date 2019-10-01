---
title: <connectionManagement> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: d377a77a4a1b4c57e9edd4fbfa364387f1bae479
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699422"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="a2af3-102">@no__t 0connectionManagement > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="a2af3-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="a2af3-103">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="a2af3-103">Specifies the maximum number of connections to a network host.</span></span>  
  
[<span data-ttu-id="a2af3-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="a2af3-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a2af3-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a2af3-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="a2af3-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<connectionManagement >**</span><span class="sxs-lookup"><span data-stu-id="a2af3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2af3-107">語法</span><span class="sxs-lookup"><span data-stu-id="a2af3-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2af3-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a2af3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a2af3-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a2af3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2af3-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a2af3-110">Attributes</span></span>  
 <span data-ttu-id="a2af3-111">無。</span><span class="sxs-lookup"><span data-stu-id="a2af3-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a2af3-112">子元素</span><span class="sxs-lookup"><span data-stu-id="a2af3-112">Child Elements</span></span>  
  
|<span data-ttu-id="a2af3-113">**目**</span><span class="sxs-lookup"><span data-stu-id="a2af3-113">**Element**</span></span>|<span data-ttu-id="a2af3-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="a2af3-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a2af3-115">add</span><span class="sxs-lookup"><span data-stu-id="a2af3-115">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="a2af3-116">將 IP 位址或 DNS 名稱加入連線管理清單中。</span><span class="sxs-lookup"><span data-stu-id="a2af3-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="a2af3-117">clear</span><span class="sxs-lookup"><span data-stu-id="a2af3-117">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="a2af3-118">清除連接管理清單。</span><span class="sxs-lookup"><span data-stu-id="a2af3-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="a2af3-119">remove</span><span class="sxs-lookup"><span data-stu-id="a2af3-119">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="a2af3-120">從連接管理清單中移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="a2af3-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a2af3-121">父項目</span><span class="sxs-lookup"><span data-stu-id="a2af3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a2af3-122">**目**</span><span class="sxs-lookup"><span data-stu-id="a2af3-122">**Element**</span></span>|<span data-ttu-id="a2af3-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="a2af3-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a2af3-124">system.net</span><span class="sxs-lookup"><span data-stu-id="a2af3-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="a2af3-125">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="a2af3-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2af3-126">備註</span><span class="sxs-lookup"><span data-stu-id="a2af3-126">Remarks</span></span>  
 <span data-ttu-id="a2af3-127">@No__t-0 元素會定義伺服器或伺服器群組的最大連接數目。</span><span class="sxs-lookup"><span data-stu-id="a2af3-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a2af3-128">組態檔</span><span class="sxs-lookup"><span data-stu-id="a2af3-128">Configuration Files</span></span>  
 <span data-ttu-id="a2af3-129">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="a2af3-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2af3-130">範例</span><span class="sxs-lookup"><span data-stu-id="a2af3-130">Example</span></span>  
 <span data-ttu-id="a2af3-131">下列範例會將應用程式設定為使用與伺服器的四個連接 `www.contoso.com`，以及兩個與其他伺服器的連線。</span><span class="sxs-lookup"><span data-stu-id="a2af3-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2af3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2af3-132">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="a2af3-133">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a2af3-133">Network Settings Schema</span></span>](index.md)
