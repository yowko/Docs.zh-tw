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
ms.openlocfilehash: 446bec116118ee8b604ef3664a6eb0452e6d5a38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184101"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="a1e11-102">connectionManagement 的 \<clear> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="a1e11-102">\<clear> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="a1e11-103">清除連接管理清單。</span><span class="sxs-lookup"><span data-stu-id="a1e11-103">Clears the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="a1e11-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a1e11-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1e11-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a1e11-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a1e11-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a1e11-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1e11-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a1e11-107">Attributes</span></span>  

 <span data-ttu-id="a1e11-108">無。</span><span class="sxs-lookup"><span data-stu-id="a1e11-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a1e11-109">子元素</span><span class="sxs-lookup"><span data-stu-id="a1e11-109">Child Elements</span></span>  

 <span data-ttu-id="a1e11-110">無。</span><span class="sxs-lookup"><span data-stu-id="a1e11-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1e11-111">父項目</span><span class="sxs-lookup"><span data-stu-id="a1e11-111">Parent Elements</span></span>  
  
|<span data-ttu-id="a1e11-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="a1e11-112">**Element**</span></span>|<span data-ttu-id="a1e11-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="a1e11-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a1e11-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="a1e11-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="a1e11-115">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="a1e11-115">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1e11-116">備註</span><span class="sxs-lookup"><span data-stu-id="a1e11-116">Remarks</span></span>  

 <span data-ttu-id="a1e11-117">`clear`元素會從連接管理清單中清除所有的專案。</span><span class="sxs-lookup"><span data-stu-id="a1e11-117">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a1e11-118">組態檔</span><span class="sxs-lookup"><span data-stu-id="a1e11-118">Configuration Files</span></span>  

 <span data-ttu-id="a1e11-119">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="a1e11-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1e11-120">範例</span><span class="sxs-lookup"><span data-stu-id="a1e11-120">Example</span></span>  

 <span data-ttu-id="a1e11-121">下列範例會清除連線管理清單，然後為伺服器 `www.contoso.com` 和所有其他網路主機新增連接管理專案。</span><span class="sxs-lookup"><span data-stu-id="a1e11-121">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a1e11-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1e11-122">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="a1e11-123">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a1e11-123">Network Settings Schema</span></span>](index.md)
