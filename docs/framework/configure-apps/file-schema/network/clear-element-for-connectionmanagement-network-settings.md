---
title: '&lt;清除&gt;connectionManagement （網路設定） 的項目'
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
ms.openlocfilehash: dba05128220b34bed34da4309a4994cbc4e1bd40
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205096"
---
# <a name="ltcleargt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="d5bf7-102">&lt;清除&gt;connectionManagement （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="d5bf7-102">&lt;clear&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="d5bf7-103">清除連接管理清單中。</span><span class="sxs-lookup"><span data-stu-id="d5bf7-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="d5bf7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d5bf7-104">\<configuration></span></span>  
<span data-ttu-id="d5bf7-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d5bf7-105">\<system.net></span></span>  
<span data-ttu-id="d5bf7-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="d5bf7-106">\<connectionManagement></span></span>  
<span data-ttu-id="d5bf7-107">\<清除 ></span><span class="sxs-lookup"><span data-stu-id="d5bf7-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5bf7-108">語法</span><span class="sxs-lookup"><span data-stu-id="d5bf7-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5bf7-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d5bf7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d5bf7-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d5bf7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5bf7-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d5bf7-111">Attributes</span></span>  
 <span data-ttu-id="d5bf7-112">無。</span><span class="sxs-lookup"><span data-stu-id="d5bf7-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d5bf7-113">子元素</span><span class="sxs-lookup"><span data-stu-id="d5bf7-113">Child Elements</span></span>  
 <span data-ttu-id="d5bf7-114">無。</span><span class="sxs-lookup"><span data-stu-id="d5bf7-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5bf7-115">父項目</span><span class="sxs-lookup"><span data-stu-id="d5bf7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d5bf7-116">**目**</span><span class="sxs-lookup"><span data-stu-id="d5bf7-116">**Element**</span></span>|<span data-ttu-id="d5bf7-117">**描述**</span><span class="sxs-lookup"><span data-stu-id="d5bf7-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d5bf7-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="d5bf7-118">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="d5bf7-119">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="d5bf7-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5bf7-120">備註</span><span class="sxs-lookup"><span data-stu-id="d5bf7-120">Remarks</span></span>  
 <span data-ttu-id="d5bf7-121">`clear`項目清除從連線管理清單中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="d5bf7-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d5bf7-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="d5bf7-122">Configuration Files</span></span>  
 <span data-ttu-id="d5bf7-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="d5bf7-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5bf7-124">範例</span><span class="sxs-lookup"><span data-stu-id="d5bf7-124">Example</span></span>  
 <span data-ttu-id="d5bf7-125">下例清除連線管理清單，然後加入 新伺服器的連接管理項目`www.contoso.com`與所有其他網路主機。</span><span class="sxs-lookup"><span data-stu-id="d5bf7-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5bf7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5bf7-126">See Also</span></span>  
- <xref:System.Net.ServicePoint>  
- <xref:System.Net.ServicePointManager>  
- [<span data-ttu-id="d5bf7-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d5bf7-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
