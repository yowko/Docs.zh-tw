---
title: <add> 的 <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 6197d01665d49a7c97ac9e44251abf15faf80a8f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850374"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="7fb30-102">\<add> 的 \<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="7fb30-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="7fb30-103">代表傳輸通訊協定配置（例如 HTTP、net.tcp、net.pipe 等）和 Windows Communication Foundation （WCF）系結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="7fb30-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="7fb30-104">在執行時間建立預設端點時，WCF 會查看設定的對應，並決定要用於特定位址的系結。</span><span class="sxs-lookup"><span data-stu-id="7fb30-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="7fb30-105">語法</span><span class="sxs-lookup"><span data-stu-id="7fb30-105">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fb30-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7fb30-106">Attributes and Elements</span></span>  
 <span data-ttu-id="7fb30-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7fb30-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fb30-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7fb30-108">Attributes</span></span>  
  
|<span data-ttu-id="7fb30-109">元素</span><span class="sxs-lookup"><span data-stu-id="7fb30-109">Element</span></span>|<span data-ttu-id="7fb30-110">描述</span><span class="sxs-lookup"><span data-stu-id="7fb30-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fb30-111">繫結</span><span class="sxs-lookup"><span data-stu-id="7fb30-111">binding</span></span>|<span data-ttu-id="7fb30-112">指定在建立預設端點期間用於端點之繫結類型的字串。</span><span class="sxs-lookup"><span data-stu-id="7fb30-112">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="7fb30-113">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="7fb30-113">bindingConfiguration</span></span>|<span data-ttu-id="7fb30-114">指定要參考之繫結組態區段名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="7fb30-114">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="7fb30-115">scheme</span><span class="sxs-lookup"><span data-stu-id="7fb30-115">scheme</span></span>|<span data-ttu-id="7fb30-116">要用於預設端點的傳輸通訊協定配置。</span><span class="sxs-lookup"><span data-stu-id="7fb30-116">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fb30-117">子元素</span><span class="sxs-lookup"><span data-stu-id="7fb30-117">Child Elements</span></span>  
 <span data-ttu-id="7fb30-118">無。</span><span class="sxs-lookup"><span data-stu-id="7fb30-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7fb30-119">父項目</span><span class="sxs-lookup"><span data-stu-id="7fb30-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7fb30-120">元素</span><span class="sxs-lookup"><span data-stu-id="7fb30-120">Element</span></span>|<span data-ttu-id="7fb30-121">描述</span><span class="sxs-lookup"><span data-stu-id="7fb30-121">Description</span></span>|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="7fb30-122">代表設定區段，用於定義傳輸通訊協定配置（例如 HTTP、net.tcp、net.pipe 等）和 Windows Communication Foundation （WCF）系結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="7fb30-122">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7fb30-123">範例</span><span class="sxs-lookup"><span data-stu-id="7fb30-123">Example</span></span>  
 <span data-ttu-id="7fb30-124">下列組態範例示範 machine.config 檔案中的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="7fb30-124">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="7fb30-125">您可以透過修改 machine.config 檔案，在電腦層級覆寫這個預設對應。</span><span class="sxs-lookup"><span data-stu-id="7fb30-125">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="7fb30-126">或者，如果您只想在應用程式範圍內覆寫該預設對應，也可以覆寫應用程式組態檔中的這個區段，並且變更個別通訊協定配置的對應。</span><span class="sxs-lookup"><span data-stu-id="7fb30-126">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7fb30-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fb30-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
