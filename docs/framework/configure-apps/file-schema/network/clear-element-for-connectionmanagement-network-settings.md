---
title: "&lt;清除&gt;connectionManagement （網路設定） 的項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 97eab03079ac7881e69ba69d324287d287eb4ecf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="c0982-102">&lt;清除&gt;connectionManagement （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="c0982-102">&lt;clear&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="c0982-103">清除連線管理清單中。</span><span class="sxs-lookup"><span data-stu-id="c0982-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="c0982-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c0982-104">\<configuration></span></span>  
<span data-ttu-id="c0982-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="c0982-105">\<system.net></span></span>  
<span data-ttu-id="c0982-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="c0982-106">\<connectionManagement></span></span>  
<span data-ttu-id="c0982-107">\<清除 ></span><span class="sxs-lookup"><span data-stu-id="c0982-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0982-108">語法</span><span class="sxs-lookup"><span data-stu-id="c0982-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0982-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c0982-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c0982-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c0982-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0982-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c0982-111">Attributes</span></span>  
 <span data-ttu-id="c0982-112">無。</span><span class="sxs-lookup"><span data-stu-id="c0982-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c0982-113">子元素</span><span class="sxs-lookup"><span data-stu-id="c0982-113">Child Elements</span></span>  
 <span data-ttu-id="c0982-114">無。</span><span class="sxs-lookup"><span data-stu-id="c0982-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0982-115">父項目</span><span class="sxs-lookup"><span data-stu-id="c0982-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c0982-116">**目**</span><span class="sxs-lookup"><span data-stu-id="c0982-116">**Element**</span></span>|<span data-ttu-id="c0982-117">**描述**</span><span class="sxs-lookup"><span data-stu-id="c0982-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c0982-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="c0982-118">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="c0982-119">指定連接至網路主機的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="c0982-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0982-120">備註</span><span class="sxs-lookup"><span data-stu-id="c0982-120">Remarks</span></span>  
 <span data-ttu-id="c0982-121">`clear`項目清除從連線管理清單中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="c0982-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c0982-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="c0982-122">Configuration Files</span></span>  
 <span data-ttu-id="c0982-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="c0982-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0982-124">範例</span><span class="sxs-lookup"><span data-stu-id="c0982-124">Example</span></span>  
 <span data-ttu-id="c0982-125">下列範例會清除連線管理清單，並將新 www.contoso.com 伺服器和所有其他網路主機的連接管理項目。</span><span class="sxs-lookup"><span data-stu-id="c0982-125">The following example clears the connection management list and then adds new connection management entries for the server www.contoso.com and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0982-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="c0982-126">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="c0982-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c0982-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
