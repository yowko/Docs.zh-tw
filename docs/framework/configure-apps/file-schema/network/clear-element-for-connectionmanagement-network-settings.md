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
ms.openlocfilehash: 86a7a0ab402c8c40ec3b824402a1dba984412b68
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659438"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="b5dc6-102">\<清除 Connectionmanagement 專案的 > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="b5dc6-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="b5dc6-103">清除連接管理清單。</span><span class="sxs-lookup"><span data-stu-id="b5dc6-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="b5dc6-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b5dc6-104">\<configuration></span></span>  
<span data-ttu-id="b5dc6-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b5dc6-105">\<system.net></span></span>  
<span data-ttu-id="b5dc6-106">\<connectionManagement></span><span class="sxs-lookup"><span data-stu-id="b5dc6-106">\<connectionManagement></span></span>  
<span data-ttu-id="b5dc6-107">\<清除 ></span><span class="sxs-lookup"><span data-stu-id="b5dc6-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5dc6-108">語法</span><span class="sxs-lookup"><span data-stu-id="b5dc6-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5dc6-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b5dc6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b5dc6-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b5dc6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5dc6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="b5dc6-111">Attributes</span></span>  
 <span data-ttu-id="b5dc6-112">無。</span><span class="sxs-lookup"><span data-stu-id="b5dc6-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b5dc6-113">子元素</span><span class="sxs-lookup"><span data-stu-id="b5dc6-113">Child Elements</span></span>  
 <span data-ttu-id="b5dc6-114">無。</span><span class="sxs-lookup"><span data-stu-id="b5dc6-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5dc6-115">父項目</span><span class="sxs-lookup"><span data-stu-id="b5dc6-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b5dc6-116">**目**</span><span class="sxs-lookup"><span data-stu-id="b5dc6-116">**Element**</span></span>|<span data-ttu-id="b5dc6-117">**描述**</span><span class="sxs-lookup"><span data-stu-id="b5dc6-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b5dc6-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="b5dc6-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="b5dc6-119">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="b5dc6-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5dc6-120">備註</span><span class="sxs-lookup"><span data-stu-id="b5dc6-120">Remarks</span></span>  
 <span data-ttu-id="b5dc6-121">`clear`元素會清除連接管理清單中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="b5dc6-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b5dc6-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="b5dc6-122">Configuration Files</span></span>  
 <span data-ttu-id="b5dc6-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="b5dc6-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5dc6-124">範例</span><span class="sxs-lookup"><span data-stu-id="b5dc6-124">Example</span></span>  
 <span data-ttu-id="b5dc6-125">下列範例會清除連線管理清單, 然後為伺服器`www.contoso.com`和所有其他網路主機新增連接管理專案。</span><span class="sxs-lookup"><span data-stu-id="b5dc6-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5dc6-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5dc6-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="b5dc6-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b5dc6-127">Network Settings Schema</span></span>](index.md)
