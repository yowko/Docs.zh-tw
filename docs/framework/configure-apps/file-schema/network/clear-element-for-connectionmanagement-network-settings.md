---
title: connectionManagement 的 <clear> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
ms.openlocfilehash: 17b380b12977423669fd413132d69a3082daca41
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698364"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="3be34-102">適用于 Connectionmanagement 專案的 @no__t 0clear > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="3be34-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="3be34-103">清除連接管理清單。</span><span class="sxs-lookup"><span data-stu-id="3be34-103">Clears the connection management list.</span></span>  
  
[<span data-ttu-id="3be34-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="3be34-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="3be34-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3be34-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="3be34-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3be34-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>  
<span data-ttu-id="3be34-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="3be34-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3be34-108">語法</span><span class="sxs-lookup"><span data-stu-id="3be34-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3be34-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3be34-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3be34-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3be34-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3be34-111">屬性</span><span class="sxs-lookup"><span data-stu-id="3be34-111">Attributes</span></span>  
 <span data-ttu-id="3be34-112">無。</span><span class="sxs-lookup"><span data-stu-id="3be34-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3be34-113">子元素</span><span class="sxs-lookup"><span data-stu-id="3be34-113">Child Elements</span></span>  
 <span data-ttu-id="3be34-114">無。</span><span class="sxs-lookup"><span data-stu-id="3be34-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3be34-115">父項目</span><span class="sxs-lookup"><span data-stu-id="3be34-115">Parent Elements</span></span>  
  
|<span data-ttu-id="3be34-116">**目**</span><span class="sxs-lookup"><span data-stu-id="3be34-116">**Element**</span></span>|<span data-ttu-id="3be34-117">**描述**</span><span class="sxs-lookup"><span data-stu-id="3be34-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3be34-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="3be34-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="3be34-119">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="3be34-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3be34-120">備註</span><span class="sxs-lookup"><span data-stu-id="3be34-120">Remarks</span></span>  
 <span data-ttu-id="3be34-121">@No__t-0 元素會清除連接管理清單中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="3be34-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3be34-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="3be34-122">Configuration Files</span></span>  
 <span data-ttu-id="3be34-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="3be34-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3be34-124">範例</span><span class="sxs-lookup"><span data-stu-id="3be34-124">Example</span></span>  
 <span data-ttu-id="3be34-125">下列範例會清除 [連線管理] 清單，然後為伺服器 `www.contoso.com` 和所有其他網路主機新增連接管理專案。</span><span class="sxs-lookup"><span data-stu-id="3be34-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3be34-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3be34-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="3be34-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="3be34-127">Network Settings Schema</span></span>](index.md)
