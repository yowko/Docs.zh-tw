---
title: <add> 的 <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: df69b5f8a79489b722c1074f118b9c6f6e8e363d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926662"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="61392-102">\<新增 protocolMapping > \<的 ></span><span class="sxs-lookup"><span data-stu-id="61392-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="61392-103">代表傳輸通訊協定配置 (例如 HTTP、net.tcp、net.pipe 等) 和 Windows Communication Foundation (WCF) 系結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="61392-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="61392-104">在執行時間建立預設端點時, WCF 會查看設定的對應, 並決定要用於特定位址的系結。</span><span class="sxs-lookup"><span data-stu-id="61392-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="61392-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="61392-105">\<system.serviceModel></span></span>  
<span data-ttu-id="61392-106">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="61392-106">\<protocolMapping></span></span>  
<span data-ttu-id="61392-107">\<add></span><span class="sxs-lookup"><span data-stu-id="61392-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61392-108">語法</span><span class="sxs-lookup"><span data-stu-id="61392-108">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61392-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="61392-109">Attributes and Elements</span></span>  
 <span data-ttu-id="61392-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="61392-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61392-111">屬性</span><span class="sxs-lookup"><span data-stu-id="61392-111">Attributes</span></span>  
  
|<span data-ttu-id="61392-112">項目</span><span class="sxs-lookup"><span data-stu-id="61392-112">Element</span></span>|<span data-ttu-id="61392-113">描述</span><span class="sxs-lookup"><span data-stu-id="61392-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61392-114">繫結</span><span class="sxs-lookup"><span data-stu-id="61392-114">binding</span></span>|<span data-ttu-id="61392-115">指定在建立預設端點期間用於端點之繫結類型的字串。</span><span class="sxs-lookup"><span data-stu-id="61392-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="61392-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="61392-116">bindingConfiguration</span></span>|<span data-ttu-id="61392-117">指定要參考之繫結組態區段名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="61392-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="61392-118">scheme</span><span class="sxs-lookup"><span data-stu-id="61392-118">scheme</span></span>|<span data-ttu-id="61392-119">要用於預設端點的傳輸通訊協定配置。</span><span class="sxs-lookup"><span data-stu-id="61392-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61392-120">子元素</span><span class="sxs-lookup"><span data-stu-id="61392-120">Child Elements</span></span>  
 <span data-ttu-id="61392-121">無。</span><span class="sxs-lookup"><span data-stu-id="61392-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61392-122">父項目</span><span class="sxs-lookup"><span data-stu-id="61392-122">Parent Elements</span></span>  
  
|<span data-ttu-id="61392-123">項目</span><span class="sxs-lookup"><span data-stu-id="61392-123">Element</span></span>|<span data-ttu-id="61392-124">描述</span><span class="sxs-lookup"><span data-stu-id="61392-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61392-125">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="61392-125">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="61392-126">代表設定區段, 用於定義傳輸通訊協定配置 (例如 HTTP、net.tcp、net.pipe 等) 和 Windows Communication Foundation (WCF) 系結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="61392-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="61392-127">範例</span><span class="sxs-lookup"><span data-stu-id="61392-127">Example</span></span>  
 <span data-ttu-id="61392-128">下列組態範例示範 machine.config 檔案中的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="61392-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="61392-129">您可以透過修改 machine.config 檔案，在電腦層級覆寫這個預設對應。</span><span class="sxs-lookup"><span data-stu-id="61392-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="61392-130">或者，如果您只想在應用程式範圍內覆寫該預設對應，也可以覆寫應用程式組態檔中的這個區段，並且變更個別通訊協定配置的對應。</span><span class="sxs-lookup"><span data-stu-id="61392-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="61392-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61392-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
