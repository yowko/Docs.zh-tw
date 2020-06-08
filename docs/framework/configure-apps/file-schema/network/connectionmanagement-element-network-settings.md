---
title: <connectionManagement> 項目 (網路設定)
description: <connectionManagement>網路設定元素會指定 .NET Framework 的網路主機連線數目上限。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 4ceec06fb0e21bfae67038efe0ce758d3d5b708f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504611"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="0e088-103">\<connectionManagement> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="0e088-103">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="0e088-104">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="0e088-104">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="0e088-105">語法</span><span class="sxs-lookup"><span data-stu-id="0e088-105">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e088-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0e088-106">Attributes and Elements</span></span>  
 <span data-ttu-id="0e088-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0e088-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e088-108">屬性</span><span class="sxs-lookup"><span data-stu-id="0e088-108">Attributes</span></span>  
 <span data-ttu-id="0e088-109">無。</span><span class="sxs-lookup"><span data-stu-id="0e088-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0e088-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0e088-110">Child Elements</span></span>  
  
|<span data-ttu-id="0e088-111">**元素**</span><span class="sxs-lookup"><span data-stu-id="0e088-111">**Element**</span></span>|<span data-ttu-id="0e088-112">**描述**</span><span class="sxs-lookup"><span data-stu-id="0e088-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0e088-113">add</span><span class="sxs-lookup"><span data-stu-id="0e088-113">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="0e088-114">將 IP 位址或 DNS 名稱加入連線管理清單中。</span><span class="sxs-lookup"><span data-stu-id="0e088-114">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="0e088-115">明確</span><span class="sxs-lookup"><span data-stu-id="0e088-115">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="0e088-116">清除連接管理清單。</span><span class="sxs-lookup"><span data-stu-id="0e088-116">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="0e088-117">remove</span><span class="sxs-lookup"><span data-stu-id="0e088-117">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="0e088-118">從連接管理清單中移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="0e088-118">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e088-119">父項目</span><span class="sxs-lookup"><span data-stu-id="0e088-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0e088-120">**元素**</span><span class="sxs-lookup"><span data-stu-id="0e088-120">**Element**</span></span>|<span data-ttu-id="0e088-121">**描述**</span><span class="sxs-lookup"><span data-stu-id="0e088-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0e088-122">system.net</span><span class="sxs-lookup"><span data-stu-id="0e088-122">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="0e088-123">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="0e088-123">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e088-124">備註</span><span class="sxs-lookup"><span data-stu-id="0e088-124">Remarks</span></span>  
 <span data-ttu-id="0e088-125">`connectionManagement`元素會定義伺服器或伺服器群組的最大連接數目。</span><span class="sxs-lookup"><span data-stu-id="0e088-125">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0e088-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="0e088-126">Configuration Files</span></span>  
 <span data-ttu-id="0e088-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="0e088-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e088-128">範例</span><span class="sxs-lookup"><span data-stu-id="0e088-128">Example</span></span>  
 <span data-ttu-id="0e088-129">下列範例會將應用程式設定為使用伺服器的四個連接 `www.contoso.com` ，以及兩個連接到其他所有伺服器。</span><span class="sxs-lookup"><span data-stu-id="0e088-129">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0e088-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e088-130">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="0e088-131">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0e088-131">Network Settings Schema</span></span>](index.md)
