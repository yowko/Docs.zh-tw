---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: be4224ef1a8b17653df8123aaf89e105a496355a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400026"
---
# <a name="protocolmapping"></a><span data-ttu-id="cb59e-101">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="cb59e-101">\<protocolMapping></span></span>
<span data-ttu-id="cb59e-102">代表設定區段，用來定義傳輸通訊協定配置（例如 HTTP、net.tcp、net.pipe 等）和 WCF 系結之間的一組預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="cb59e-102">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="cb59e-103">在執行時間建立預設端點時，Windows Communication Foundation （WCF）會查看設定的對應，並決定要用於特定位址的系結。</span><span class="sxs-lookup"><span data-stu-id="cb59e-103">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
<span data-ttu-id="cb59e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cb59e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cb59e-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cb59e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cb59e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<protocolMapping >**</span><span class="sxs-lookup"><span data-stu-id="cb59e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb59e-107">語法</span><span class="sxs-lookup"><span data-stu-id="cb59e-107">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb59e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cb59e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cb59e-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cb59e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb59e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="cb59e-110">Attributes</span></span>  
 <span data-ttu-id="cb59e-111">無。</span><span class="sxs-lookup"><span data-stu-id="cb59e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cb59e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="cb59e-112">Child Elements</span></span>  
  
|<span data-ttu-id="cb59e-113">項目</span><span class="sxs-lookup"><span data-stu-id="cb59e-113">Element</span></span>|<span data-ttu-id="cb59e-114">描述</span><span class="sxs-lookup"><span data-stu-id="cb59e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb59e-115">\<filters></span><span class="sxs-lookup"><span data-stu-id="cb59e-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="cb59e-116">包含傳輸通訊協定配置（例如 HTTP、net.tcp、net.pipe 等）和 WCF 系結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="cb59e-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb59e-117">父項目</span><span class="sxs-lookup"><span data-stu-id="cb59e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cb59e-118">項目</span><span class="sxs-lookup"><span data-stu-id="cb59e-118">Element</span></span>|<span data-ttu-id="cb59e-119">說明</span><span class="sxs-lookup"><span data-stu-id="cb59e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb59e-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cb59e-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="cb59e-121">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="cb59e-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cb59e-122">範例</span><span class="sxs-lookup"><span data-stu-id="cb59e-122">Example</span></span>  
 <span data-ttu-id="cb59e-123">下列組態範例示範 machine.config 檔案中的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="cb59e-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="cb59e-124">您可以透過修改 machine.config 檔案，在電腦層級覆寫這個預設對應。</span><span class="sxs-lookup"><span data-stu-id="cb59e-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="cb59e-125">或者，如果您只想在應用程式範圍內覆寫該預設對應，也可以覆寫應用程式組態檔中的這個區段，並且變更個別通訊協定配置的對應。</span><span class="sxs-lookup"><span data-stu-id="cb59e-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a><span data-ttu-id="cb59e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb59e-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
