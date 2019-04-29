---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: e26044340bda84fe38b7e286edf833affa94b86c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785485"
---
# <a name="protocolmapping"></a><span data-ttu-id="1d30c-101">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="1d30c-101">\<protocolMapping></span></span>
<span data-ttu-id="1d30c-102">表示用於定義一組預設通訊協定之間的對應傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 和 WCF 繫結組態區段。</span><span class="sxs-lookup"><span data-stu-id="1d30c-102">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="1d30c-103">當在執行階段建立預設端點，Windows Communication Foundation (WCF) 會查看所設定的對應，並決定哪些繫結，以使用特定基礎位址。</span><span class="sxs-lookup"><span data-stu-id="1d30c-103">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[<span data-ttu-id="1d30c-104">**\<system.serviceModel>**</span><span class="sxs-lookup"><span data-stu-id="1d30c-104">**\<system.serviceModel>**</span></span>](system-servicemodel.md)  
<span data-ttu-id="1d30c-105">&nbsp;&nbsp;**\<protocolMapping>**</span><span class="sxs-lookup"><span data-stu-id="1d30c-105">&nbsp;&nbsp;**\<protocolMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d30c-106">語法</span><span class="sxs-lookup"><span data-stu-id="1d30c-106">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d30c-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1d30c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1d30c-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1d30c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d30c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="1d30c-109">Attributes</span></span>  
 <span data-ttu-id="1d30c-110">無。</span><span class="sxs-lookup"><span data-stu-id="1d30c-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1d30c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1d30c-111">Child Elements</span></span>  
  
|<span data-ttu-id="1d30c-112">項目</span><span class="sxs-lookup"><span data-stu-id="1d30c-112">Element</span></span>|<span data-ttu-id="1d30c-113">描述</span><span class="sxs-lookup"><span data-stu-id="1d30c-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d30c-114">\<filters></span><span class="sxs-lookup"><span data-stu-id="1d30c-114">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="1d30c-115">包含傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 與 WCF 繫結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="1d30c-115">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d30c-116">父項目</span><span class="sxs-lookup"><span data-stu-id="1d30c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1d30c-117">項目</span><span class="sxs-lookup"><span data-stu-id="1d30c-117">Element</span></span>|<span data-ttu-id="1d30c-118">描述</span><span class="sxs-lookup"><span data-stu-id="1d30c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d30c-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1d30c-119">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="1d30c-120">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="1d30c-120">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1d30c-121">範例</span><span class="sxs-lookup"><span data-stu-id="1d30c-121">Example</span></span>  
 <span data-ttu-id="1d30c-122">下列組態範例示範 machine.config 檔案中的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="1d30c-122">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="1d30c-123">您可以透過修改 machine.config 檔案，在電腦層級覆寫這個預設對應。</span><span class="sxs-lookup"><span data-stu-id="1d30c-123">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="1d30c-124">或者，如果您只想在應用程式範圍內覆寫該預設對應，也可以覆寫應用程式組態檔中的這個區段，並且變更個別通訊協定配置的對應。</span><span class="sxs-lookup"><span data-stu-id="1d30c-124">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d30c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d30c-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
