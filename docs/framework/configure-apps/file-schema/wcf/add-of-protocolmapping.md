---
title: <add> 的 <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 6197d01665d49a7c97ac9e44251abf15faf80a8f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850374"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="e9aea-102">\<新增 protocolMapping > \<的 ></span><span class="sxs-lookup"><span data-stu-id="e9aea-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="e9aea-103">代表傳輸通訊協定配置（例如 HTTP、net.tcp、net.pipe 等）和 Windows Communication Foundation （WCF）系結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="e9aea-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="e9aea-104">在執行時間建立預設端點時，WCF 會查看設定的對應，並決定要用於特定位址的系結。</span><span class="sxs-lookup"><span data-stu-id="e9aea-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
<span data-ttu-id="e9aea-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e9aea-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e9aea-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e9aea-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e9aea-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<protocolMapping >** ](protocolmapping.md)</span><span class="sxs-lookup"><span data-stu-id="e9aea-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)</span></span>\
<span data-ttu-id="e9aea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="e9aea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9aea-109">語法</span><span class="sxs-lookup"><span data-stu-id="e9aea-109">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9aea-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e9aea-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e9aea-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e9aea-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9aea-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e9aea-112">Attributes</span></span>  
  
|<span data-ttu-id="e9aea-113">項目</span><span class="sxs-lookup"><span data-stu-id="e9aea-113">Element</span></span>|<span data-ttu-id="e9aea-114">描述</span><span class="sxs-lookup"><span data-stu-id="e9aea-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9aea-115">繫結</span><span class="sxs-lookup"><span data-stu-id="e9aea-115">binding</span></span>|<span data-ttu-id="e9aea-116">指定在建立預設端點期間用於端點之繫結類型的字串。</span><span class="sxs-lookup"><span data-stu-id="e9aea-116">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="e9aea-117">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="e9aea-117">bindingConfiguration</span></span>|<span data-ttu-id="e9aea-118">指定要參考之繫結組態區段名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="e9aea-118">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="e9aea-119">scheme</span><span class="sxs-lookup"><span data-stu-id="e9aea-119">scheme</span></span>|<span data-ttu-id="e9aea-120">要用於預設端點的傳輸通訊協定配置。</span><span class="sxs-lookup"><span data-stu-id="e9aea-120">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9aea-121">子元素</span><span class="sxs-lookup"><span data-stu-id="e9aea-121">Child Elements</span></span>  
 <span data-ttu-id="e9aea-122">無。</span><span class="sxs-lookup"><span data-stu-id="e9aea-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9aea-123">父項目</span><span class="sxs-lookup"><span data-stu-id="e9aea-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e9aea-124">項目</span><span class="sxs-lookup"><span data-stu-id="e9aea-124">Element</span></span>|<span data-ttu-id="e9aea-125">描述</span><span class="sxs-lookup"><span data-stu-id="e9aea-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9aea-126">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="e9aea-126">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="e9aea-127">代表設定區段，用於定義傳輸通訊協定配置（例如 HTTP、net.tcp、net.pipe 等）和 Windows Communication Foundation （WCF）系結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="e9aea-127">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e9aea-128">範例</span><span class="sxs-lookup"><span data-stu-id="e9aea-128">Example</span></span>  
 <span data-ttu-id="e9aea-129">下列組態範例示範 machine.config 檔案中的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="e9aea-129">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="e9aea-130">您可以透過修改 machine.config 檔案，在電腦層級覆寫這個預設對應。</span><span class="sxs-lookup"><span data-stu-id="e9aea-130">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="e9aea-131">或者，如果您只想在應用程式範圍內覆寫該預設對應，也可以覆寫應用程式組態檔中的這個區段，並且變更個別通訊協定配置的對應。</span><span class="sxs-lookup"><span data-stu-id="e9aea-131">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e9aea-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9aea-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
