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
ms.openlocfilehash: 05e4a1bc42dc39c7d2b56e30c98bdeefd31e4416
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149474"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="b1ebf-102">connectionManagement 的 \<add> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="b1ebf-102">\<add> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="b1ebf-103">將 IP 位址或 DNS 名稱加入連線管理清單中。</span><span class="sxs-lookup"><span data-stu-id="b1ebf-103">Adds an IP address or DNS name to the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="b1ebf-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b1ebf-104">Syntax</span></span>  
  
```xml  
<add
  address="address expression"
  maxconnection="integer"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1ebf-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b1ebf-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b1ebf-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b1ebf-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1ebf-107">屬性</span><span class="sxs-lookup"><span data-stu-id="b1ebf-107">Attributes</span></span>  
  
|<span data-ttu-id="b1ebf-108">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="b1ebf-108">**Attribute**</span></span>|<span data-ttu-id="b1ebf-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="b1ebf-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="b1ebf-110">描述 IP 位址或 DNS 名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="b1ebf-110">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="b1ebf-111">允許連接到伺服器的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="b1ebf-111">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="b1ebf-112">如果未提供，預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="b1ebf-112">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1ebf-113">子元素</span><span class="sxs-lookup"><span data-stu-id="b1ebf-113">Child Elements</span></span>  

 <span data-ttu-id="b1ebf-114">無。</span><span class="sxs-lookup"><span data-stu-id="b1ebf-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1ebf-115">父項目</span><span class="sxs-lookup"><span data-stu-id="b1ebf-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b1ebf-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="b1ebf-116">**Element**</span></span>|<span data-ttu-id="b1ebf-117">**說明**</span><span class="sxs-lookup"><span data-stu-id="b1ebf-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b1ebf-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="b1ebf-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="b1ebf-119">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="b1ebf-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1ebf-120">備註</span><span class="sxs-lookup"><span data-stu-id="b1ebf-120">Remarks</span></span>  

 <span data-ttu-id="b1ebf-121">`address` 屬性的值應該是表示所有連線的星號，或是 `<schema>://<idn_hostname>[:<port>]` 格式的字串。</span><span class="sxs-lookup"><span data-stu-id="b1ebf-121">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="b1ebf-122">如果傳遞至任何 HTTP 應用程式開發介面的 URI 包含 Unicode，將會使用 <xref:System.Uri.DnsSafeHost%2A> 在內部轉換名稱，可能會傳回 punicode 字串 (行為取決於目前的 IDN 組態)。</span><span class="sxs-lookup"><span data-stu-id="b1ebf-122">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b1ebf-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="b1ebf-123">Configuration Files</span></span>  

 <span data-ttu-id="b1ebf-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="b1ebf-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1ebf-125">範例</span><span class="sxs-lookup"><span data-stu-id="b1ebf-125">Example</span></span>  

 <span data-ttu-id="b1ebf-126">下列範例會將應用程式設定為使用四個對伺服器的連線 `www.contoso.com` ，以及與所有其他伺服器的兩個連接。</span><span class="sxs-lookup"><span data-stu-id="b1ebf-126">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1ebf-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1ebf-127">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="b1ebf-128">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b1ebf-128">Network Settings Schema</span></span>](index.md)
