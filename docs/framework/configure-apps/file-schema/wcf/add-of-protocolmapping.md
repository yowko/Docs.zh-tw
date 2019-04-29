---
title: <add> 的 <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 85d09c920de2ca1ab4971551ff98ea58c4492f44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704488"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="5d18e-102">\<add> of \<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="5d18e-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="5d18e-103">代表傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 與 Windows Communication Foundation (WCF) 繫結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="5d18e-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="5d18e-104">當在執行階段建立預設端點，WCF 會查看所設定的對應，並決定哪些繫結，以使用特定基礎位址。</span><span class="sxs-lookup"><span data-stu-id="5d18e-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="5d18e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5d18e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5d18e-106">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="5d18e-106">\<protocolMapping></span></span>  
<span data-ttu-id="5d18e-107">\<add></span><span class="sxs-lookup"><span data-stu-id="5d18e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d18e-108">語法</span><span class="sxs-lookup"><span data-stu-id="5d18e-108">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d18e-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5d18e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5d18e-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5d18e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d18e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5d18e-111">Attributes</span></span>  
  
|<span data-ttu-id="5d18e-112">項目</span><span class="sxs-lookup"><span data-stu-id="5d18e-112">Element</span></span>|<span data-ttu-id="5d18e-113">描述</span><span class="sxs-lookup"><span data-stu-id="5d18e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d18e-114">繫結</span><span class="sxs-lookup"><span data-stu-id="5d18e-114">binding</span></span>|<span data-ttu-id="5d18e-115">指定在建立預設端點期間用於端點之繫結類型的字串。</span><span class="sxs-lookup"><span data-stu-id="5d18e-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="5d18e-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="5d18e-116">bindingConfiguration</span></span>|<span data-ttu-id="5d18e-117">指定要參考之繫結組態區段名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="5d18e-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="5d18e-118">scheme</span><span class="sxs-lookup"><span data-stu-id="5d18e-118">scheme</span></span>|<span data-ttu-id="5d18e-119">要用於預設端點的傳輸通訊協定配置。</span><span class="sxs-lookup"><span data-stu-id="5d18e-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d18e-120">子元素</span><span class="sxs-lookup"><span data-stu-id="5d18e-120">Child Elements</span></span>  
 <span data-ttu-id="5d18e-121">無。</span><span class="sxs-lookup"><span data-stu-id="5d18e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d18e-122">父項目</span><span class="sxs-lookup"><span data-stu-id="5d18e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5d18e-123">項目</span><span class="sxs-lookup"><span data-stu-id="5d18e-123">Element</span></span>|<span data-ttu-id="5d18e-124">描述</span><span class="sxs-lookup"><span data-stu-id="5d18e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d18e-125">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="5d18e-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="5d18e-126">表示組態區段，用於定義傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 和 Windows Communication Foundation (WCF) 繫結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="5d18e-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5d18e-127">範例</span><span class="sxs-lookup"><span data-stu-id="5d18e-127">Example</span></span>  
 <span data-ttu-id="5d18e-128">下列組態範例示範 machine.config 檔案中的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="5d18e-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="5d18e-129">您可以透過修改 machine.config 檔案，在電腦層級覆寫這個預設對應。</span><span class="sxs-lookup"><span data-stu-id="5d18e-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="5d18e-130">或者，如果您只想在應用程式範圍內覆寫該預設對應，也可以覆寫應用程式組態檔中的這個區段，並且變更個別通訊協定配置的對應。</span><span class="sxs-lookup"><span data-stu-id="5d18e-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d18e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d18e-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
