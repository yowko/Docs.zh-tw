---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: 0a79aa18c74ddb8ec47f02620d16d391b4a36b68
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162292"
---
# \<protocolMapping>

<span data-ttu-id="624e8-101">代表組態區段，該區段用於定義傳輸通訊協定配置 (例如 http、net.tcp、net.pipe 等) 和 WCF 繫結之間的一組預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="624e8-101">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="624e8-102">當您在執行時間建立預設端點時，Windows Communication Foundation (WCF) 會查看所設定的對應，並決定要用於特定位址的系結。</span><span class="sxs-lookup"><span data-stu-id="624e8-102">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**  
  
## <a name="syntax"></a><span data-ttu-id="624e8-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="624e8-103">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="624e8-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="624e8-104">Attributes and Elements</span></span>  

 <span data-ttu-id="624e8-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="624e8-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="624e8-106">屬性</span><span class="sxs-lookup"><span data-stu-id="624e8-106">Attributes</span></span>  

 <span data-ttu-id="624e8-107">無。</span><span class="sxs-lookup"><span data-stu-id="624e8-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="624e8-108">子元素</span><span class="sxs-lookup"><span data-stu-id="624e8-108">Child Elements</span></span>  
  
|<span data-ttu-id="624e8-109">項目</span><span class="sxs-lookup"><span data-stu-id="624e8-109">Element</span></span>|<span data-ttu-id="624e8-110">描述</span><span class="sxs-lookup"><span data-stu-id="624e8-110">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="624e8-111">包含傳輸通訊協定配置 (例如 http、net.tcp、net.pipe 等) 與 WCF 繫結之間的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="624e8-111">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="624e8-112">父項目</span><span class="sxs-lookup"><span data-stu-id="624e8-112">Parent Elements</span></span>  
  
|<span data-ttu-id="624e8-113">項目</span><span class="sxs-lookup"><span data-stu-id="624e8-113">Element</span></span>|<span data-ttu-id="624e8-114">描述</span><span class="sxs-lookup"><span data-stu-id="624e8-114">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="624e8-115">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="624e8-115">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="624e8-116">範例</span><span class="sxs-lookup"><span data-stu-id="624e8-116">Example</span></span>  

 <span data-ttu-id="624e8-117">下列組態範例示範 machine.config 檔案中的預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="624e8-117">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="624e8-118">您可以透過修改 machine.config 檔案，在電腦層級覆寫這個預設對應。</span><span class="sxs-lookup"><span data-stu-id="624e8-118">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="624e8-119">或者，如果您只想在應用程式範圍內覆寫該預設對應，也可以覆寫應用程式組態檔中的這個區段，並且變更個別通訊協定配置的對應。</span><span class="sxs-lookup"><span data-stu-id="624e8-119">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="624e8-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="624e8-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
