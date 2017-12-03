---
title: '&lt;p&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 88eb76a5657bd4a83bebb32ce30f73d32693be9b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="f389b-102">&lt;p&gt;</span><span class="sxs-lookup"><span data-stu-id="f389b-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="f389b-103">代表定義一組預設通訊協定之間的對應傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 和 WCF 繫結組態區段。</span><span class="sxs-lookup"><span data-stu-id="f389b-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="f389b-104">在執行階段建立預設的端點時，[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 會查看所設定的對應，並且決定要用於特定基礎位址的繫結。</span><span class="sxs-lookup"><span data-stu-id="f389b-104">When creating default endpoints at runtime, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="f389b-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f389b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f389b-106">\<p ></span><span class="sxs-lookup"><span data-stu-id="f389b-106">\<protocolMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f389b-107">語法</span><span class="sxs-lookup"><span data-stu-id="f389b-107">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f389b-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f389b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f389b-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f389b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f389b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f389b-110">Attributes</span></span>  
 <span data-ttu-id="f389b-111">無。</span><span class="sxs-lookup"><span data-stu-id="f389b-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f389b-112">子項目</span><span class="sxs-lookup"><span data-stu-id="f389b-112">Child Elements</span></span>  
  
|<span data-ttu-id="f389b-113">項目</span><span class="sxs-lookup"><span data-stu-id="f389b-113">Element</span></span>|<span data-ttu-id="f389b-114">說明</span><span class="sxs-lookup"><span data-stu-id="f389b-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f389b-115">\<篩選條件 ></span><span class="sxs-lookup"><span data-stu-id="f389b-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="f389b-116">包含傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 和 WCF 繫結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="f389b-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f389b-117">父項目</span><span class="sxs-lookup"><span data-stu-id="f389b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f389b-118">項目</span><span class="sxs-lookup"><span data-stu-id="f389b-118">Element</span></span>|<span data-ttu-id="f389b-119">描述</span><span class="sxs-lookup"><span data-stu-id="f389b-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f389b-120">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f389b-120">system.ServiceModel</span></span>|<span data-ttu-id="f389b-121">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="f389b-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f389b-122">範例</span><span class="sxs-lookup"><span data-stu-id="f389b-122">Example</span></span>  
 <span data-ttu-id="f389b-123">下列組態範例示範 machine.config 檔案中的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="f389b-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="f389b-124">您可以透過修改 machine.config 檔案，在電腦層級覆寫這個預設對應。</span><span class="sxs-lookup"><span data-stu-id="f389b-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="f389b-125">或者，如果您只想在應用程式範圍內覆寫該預設對應，也可以覆寫應用程式組態檔中的這個區段，並且變更個別通訊協定配置的對應。</span><span class="sxs-lookup"><span data-stu-id="f389b-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f389b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f389b-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
