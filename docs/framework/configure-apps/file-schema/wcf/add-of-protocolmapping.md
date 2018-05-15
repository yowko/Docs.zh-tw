---
title: '&lt;protocolMapping&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: b9559a6921bdededf760f54f58abadb46612b174
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a><span data-ttu-id="aebc1-102">&lt;protocolMapping&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="aebc1-102">&lt;add&gt; of &lt;protocolMapping&gt;</span></span>
<span data-ttu-id="aebc1-103">代表傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 與 Windows Communication Foundation (WCF) 繫結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="aebc1-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="aebc1-104">在執行階段建立預設的端點時，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 會查看所設定的對應，並且決定要用於特定基礎位址的繫結。</span><span class="sxs-lookup"><span data-stu-id="aebc1-104">When creating default endpoints at runtime, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="aebc1-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="aebc1-105">\<system.serviceModel></span></span>  
<span data-ttu-id="aebc1-106">\<p ></span><span class="sxs-lookup"><span data-stu-id="aebc1-106">\<protocolMapping></span></span>  
<span data-ttu-id="aebc1-107">\<add></span><span class="sxs-lookup"><span data-stu-id="aebc1-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aebc1-108">語法</span><span class="sxs-lookup"><span data-stu-id="aebc1-108">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aebc1-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aebc1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="aebc1-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="aebc1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aebc1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="aebc1-111">Attributes</span></span>  
  
|<span data-ttu-id="aebc1-112">項目</span><span class="sxs-lookup"><span data-stu-id="aebc1-112">Element</span></span>|<span data-ttu-id="aebc1-113">描述</span><span class="sxs-lookup"><span data-stu-id="aebc1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aebc1-114">繫結</span><span class="sxs-lookup"><span data-stu-id="aebc1-114">binding</span></span>|<span data-ttu-id="aebc1-115">指定在建立預設端點期間用於端點之繫結類型的字串。</span><span class="sxs-lookup"><span data-stu-id="aebc1-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="aebc1-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="aebc1-116">bindingConfiguration</span></span>|<span data-ttu-id="aebc1-117">指定要參考之繫結組態區段名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="aebc1-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="aebc1-118">scheme</span><span class="sxs-lookup"><span data-stu-id="aebc1-118">scheme</span></span>|<span data-ttu-id="aebc1-119">要用於預設端點的傳輸通訊協定配置。</span><span class="sxs-lookup"><span data-stu-id="aebc1-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aebc1-120">子項目</span><span class="sxs-lookup"><span data-stu-id="aebc1-120">Child Elements</span></span>  
 <span data-ttu-id="aebc1-121">無。</span><span class="sxs-lookup"><span data-stu-id="aebc1-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aebc1-122">父項目</span><span class="sxs-lookup"><span data-stu-id="aebc1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="aebc1-123">項目</span><span class="sxs-lookup"><span data-stu-id="aebc1-123">Element</span></span>|<span data-ttu-id="aebc1-124">描述</span><span class="sxs-lookup"><span data-stu-id="aebc1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aebc1-125">\<p ></span><span class="sxs-lookup"><span data-stu-id="aebc1-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="aebc1-126">代表組態區段，用於定義傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 和 Windows Communication Foundation (WCF) 繫結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="aebc1-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aebc1-127">範例</span><span class="sxs-lookup"><span data-stu-id="aebc1-127">Example</span></span>  
 <span data-ttu-id="aebc1-128">下列組態範例示範 machine.config 檔案中的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="aebc1-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="aebc1-129">您可以透過修改 machine.config 檔案，在電腦層級覆寫這個預設對應。</span><span class="sxs-lookup"><span data-stu-id="aebc1-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="aebc1-130">或者，如果您只想在應用程式範圍內覆寫該預設對應，也可以覆寫應用程式組態檔中的這個區段，並且變更個別通訊協定配置的對應。</span><span class="sxs-lookup"><span data-stu-id="aebc1-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aebc1-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aebc1-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
