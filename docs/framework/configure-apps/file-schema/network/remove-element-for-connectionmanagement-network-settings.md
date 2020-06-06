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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154734"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="4284f-102">connectionManagement 的 \<remove> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="4284f-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="4284f-103">從連接管理清單中移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="4284f-103">Removes an IP address or DNS name from the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="4284f-104">語法</span><span class="sxs-lookup"><span data-stu-id="4284f-104">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4284f-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4284f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4284f-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4284f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4284f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4284f-107">Attributes</span></span>  
  
|<span data-ttu-id="4284f-108">**屬性**</span><span class="sxs-lookup"><span data-stu-id="4284f-108">**Attribute**</span></span>|<span data-ttu-id="4284f-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="4284f-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="4284f-110">IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="4284f-110">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4284f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4284f-111">Child Elements</span></span>  
 <span data-ttu-id="4284f-112">無。</span><span class="sxs-lookup"><span data-stu-id="4284f-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4284f-113">父項目</span><span class="sxs-lookup"><span data-stu-id="4284f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="4284f-114">**元素**</span><span class="sxs-lookup"><span data-stu-id="4284f-114">**Element**</span></span>|<span data-ttu-id="4284f-115">**說明**</span><span class="sxs-lookup"><span data-stu-id="4284f-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4284f-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="4284f-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="4284f-117">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="4284f-117">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4284f-118">備註</span><span class="sxs-lookup"><span data-stu-id="4284f-118">Remarks</span></span>  
 <span data-ttu-id="4284f-119">`remove`元素會移除指定之伺服器的連接管理清單專案。</span><span class="sxs-lookup"><span data-stu-id="4284f-119">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="4284f-120">屬性的值 `address` 應為有效的 IP 位址或主機名稱。</span><span class="sxs-lookup"><span data-stu-id="4284f-120">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4284f-121">組態檔</span><span class="sxs-lookup"><span data-stu-id="4284f-121">Configuration Files</span></span>  
 <span data-ttu-id="4284f-122">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="4284f-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4284f-123">範例</span><span class="sxs-lookup"><span data-stu-id="4284f-123">Example</span></span>  
 <span data-ttu-id="4284f-124">下列範例會移除伺服器的任何連接管理清單專案 `www.adventure-works.com` ，然後將應用程式設定為使用四個伺服器連線 `www.contoso.com` ，以及兩個連接到其他所有伺服器。</span><span class="sxs-lookup"><span data-stu-id="4284f-124">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4284f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4284f-125">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="4284f-126">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="4284f-126">Network Settings Schema</span></span>](index.md)
