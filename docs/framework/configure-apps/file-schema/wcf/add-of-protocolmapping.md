---
title: "&lt;protocolMapping&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a254b8a4de8f66cb0d051d246be2d07e905615a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a><span data-ttu-id="3389d-102">&lt;protocolMapping&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="3389d-102">&lt;add&gt; of &lt;protocolMapping&gt;</span></span>
<span data-ttu-id="3389d-103">代表傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 之間的預設通訊協定對應和[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="3389d-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] binding.</span></span> <span data-ttu-id="3389d-104">在執行階段建立預設的端點時，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 會查看所設定的對應，並且決定要用於特定基礎位址的繫結。</span><span class="sxs-lookup"><span data-stu-id="3389d-104">When creating default endpoints at runtime, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="3389d-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="3389d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3389d-106">\<p ></span><span class="sxs-lookup"><span data-stu-id="3389d-106">\<protocolMapping></span></span>  
<span data-ttu-id="3389d-107">\<add></span><span class="sxs-lookup"><span data-stu-id="3389d-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3389d-108">語法</span><span class="sxs-lookup"><span data-stu-id="3389d-108">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3389d-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3389d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3389d-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3389d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3389d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="3389d-111">Attributes</span></span>  
  
|<span data-ttu-id="3389d-112">元素</span><span class="sxs-lookup"><span data-stu-id="3389d-112">Element</span></span>|<span data-ttu-id="3389d-113">描述</span><span class="sxs-lookup"><span data-stu-id="3389d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3389d-114">繫結</span><span class="sxs-lookup"><span data-stu-id="3389d-114">binding</span></span>|<span data-ttu-id="3389d-115">指定在建立預設端點期間用於端點之繫結類型的字串。</span><span class="sxs-lookup"><span data-stu-id="3389d-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="3389d-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="3389d-116">bindingConfiguration</span></span>|<span data-ttu-id="3389d-117">指定要參考之繫結組態區段名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="3389d-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="3389d-118">scheme</span><span class="sxs-lookup"><span data-stu-id="3389d-118">scheme</span></span>|<span data-ttu-id="3389d-119">要用於預設端點的傳輸通訊協定配置。</span><span class="sxs-lookup"><span data-stu-id="3389d-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3389d-120">子元素</span><span class="sxs-lookup"><span data-stu-id="3389d-120">Child Elements</span></span>  
 <span data-ttu-id="3389d-121">無。</span><span class="sxs-lookup"><span data-stu-id="3389d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3389d-122">父項目</span><span class="sxs-lookup"><span data-stu-id="3389d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3389d-123">項目</span><span class="sxs-lookup"><span data-stu-id="3389d-123">Element</span></span>|<span data-ttu-id="3389d-124">描述</span><span class="sxs-lookup"><span data-stu-id="3389d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3389d-125">\<p ></span><span class="sxs-lookup"><span data-stu-id="3389d-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="3389d-126">代表用於定義傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 之間的預設通訊協定對應的組態區段和[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="3389d-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3389d-127">範例</span><span class="sxs-lookup"><span data-stu-id="3389d-127">Example</span></span>  
 <span data-ttu-id="3389d-128">下列組態範例示範 machine.config 檔案中的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="3389d-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="3389d-129">您可以透過修改 machine.config 檔案，在電腦層級覆寫這個預設對應。</span><span class="sxs-lookup"><span data-stu-id="3389d-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="3389d-130">或者，如果您只想在應用程式範圍內覆寫該預設對應，也可以覆寫應用程式組態檔中的這個區段，並且變更個別通訊協定配置的對應。</span><span class="sxs-lookup"><span data-stu-id="3389d-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3389d-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="3389d-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
