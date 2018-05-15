---
title: '&lt;p&gt;'
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: 4afdaaa62c1ac3241eb7382d0995bed51bde73e2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="09e53-102">&lt;p&gt;</span><span class="sxs-lookup"><span data-stu-id="09e53-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="09e53-103">代表定義一組預設通訊協定之間的對應傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 和 WCF 繫結組態區段。</span><span class="sxs-lookup"><span data-stu-id="09e53-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="09e53-104">在執行階段建立預設端點，Windows Communication Foundation (WCF) 會查看所設定的對應，並決定哪些繫結至用於特定基礎位址。</span><span class="sxs-lookup"><span data-stu-id="09e53-104">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="09e53-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="09e53-105">\<system.serviceModel></span></span>  
<span data-ttu-id="09e53-106">\<p ></span><span class="sxs-lookup"><span data-stu-id="09e53-106">\<protocolMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09e53-107">語法</span><span class="sxs-lookup"><span data-stu-id="09e53-107">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="09e53-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="09e53-108">Attributes and Elements</span></span>  
 <span data-ttu-id="09e53-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="09e53-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09e53-110">屬性</span><span class="sxs-lookup"><span data-stu-id="09e53-110">Attributes</span></span>  
 <span data-ttu-id="09e53-111">無。</span><span class="sxs-lookup"><span data-stu-id="09e53-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="09e53-112">子項目</span><span class="sxs-lookup"><span data-stu-id="09e53-112">Child Elements</span></span>  
  
|<span data-ttu-id="09e53-113">項目</span><span class="sxs-lookup"><span data-stu-id="09e53-113">Element</span></span>|<span data-ttu-id="09e53-114">描述</span><span class="sxs-lookup"><span data-stu-id="09e53-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09e53-115">\<篩選條件 ></span><span class="sxs-lookup"><span data-stu-id="09e53-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="09e53-116">包含傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 和 WCF 繫結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="09e53-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="09e53-117">父項目</span><span class="sxs-lookup"><span data-stu-id="09e53-117">Parent Elements</span></span>  
  
|<span data-ttu-id="09e53-118">項目</span><span class="sxs-lookup"><span data-stu-id="09e53-118">Element</span></span>|<span data-ttu-id="09e53-119">描述</span><span class="sxs-lookup"><span data-stu-id="09e53-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09e53-120">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="09e53-120">system.ServiceModel</span></span>|<span data-ttu-id="09e53-121">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="09e53-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="09e53-122">範例</span><span class="sxs-lookup"><span data-stu-id="09e53-122">Example</span></span>  
 <span data-ttu-id="09e53-123">下列組態範例示範 machine.config 檔案中的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="09e53-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="09e53-124">您可以透過修改 machine.config 檔案，在電腦層級覆寫這個預設對應。</span><span class="sxs-lookup"><span data-stu-id="09e53-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="09e53-125">或者，如果您只想在應用程式範圍內覆寫該預設對應，也可以覆寫應用程式組態檔中的這個區段，並且變更個別通訊協定配置的對應。</span><span class="sxs-lookup"><span data-stu-id="09e53-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="09e53-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09e53-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
