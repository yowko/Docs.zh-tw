---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: dcc32f5aa055942408a3f01d37b5aa27ac0f51ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173766"
---
# \<service>

<span data-ttu-id="f3bbd-101">`service` 項目包含 Windows Communication Foundation (WCF) 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-101">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="f3bbd-102">它也包含公開服務的端點。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-102">It also contains endpoints that expose the service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<service>**  
  
## <a name="syntax"></a><span data-ttu-id="f3bbd-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3bbd-103">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3bbd-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f3bbd-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f3bbd-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3bbd-106">屬性</span><span class="sxs-lookup"><span data-stu-id="f3bbd-106">Attributes</span></span>  
  
|<span data-ttu-id="f3bbd-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f3bbd-107">Attribute</span></span>|<span data-ttu-id="f3bbd-108">描述</span><span class="sxs-lookup"><span data-stu-id="f3bbd-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3bbd-109">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="f3bbd-109">behaviorConfiguration</span></span>|<span data-ttu-id="f3bbd-110">字串，其中包含要用於產生服務實體之行為的行為名稱。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-110">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="f3bbd-111">行為名稱必須在定義服務之處的範圍內。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-111">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="f3bbd-112">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-112">The default value is an empty string.</span></span>|  
|<span data-ttu-id="f3bbd-113">NAME</span><span class="sxs-lookup"><span data-stu-id="f3bbd-113">name</span></span>|<span data-ttu-id="f3bbd-114">必要的字串屬性，其中指定要具現化的服務型別。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-114">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="f3bbd-115">這個設定必須等同於有效的型別。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-115">This setting must equate to a valid type.</span></span> <span data-ttu-id="f3bbd-116">格式應該為 `Namespace.Class.`。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-116">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3bbd-117">子元素</span><span class="sxs-lookup"><span data-stu-id="f3bbd-117">Child Elements</span></span>  
  
|<span data-ttu-id="f3bbd-118">項目</span><span class="sxs-lookup"><span data-stu-id="f3bbd-118">Element</span></span>|<span data-ttu-id="f3bbd-119">描述</span><span class="sxs-lookup"><span data-stu-id="f3bbd-119">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="f3bbd-120">公開此服務之 `endpoint` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-120">A collection of `endpoint` elements that expose this service.</span></span>|  
|[\<host>](host.md)|<span data-ttu-id="f3bbd-121">指定這個服務執行個體的主機。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-121">Specifies the host of this service instance.</span></span> <span data-ttu-id="f3bbd-122">此項目的型別為 <xref:System.ServiceModel.Configuration.HostElement>。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-122">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3bbd-123">父項目</span><span class="sxs-lookup"><span data-stu-id="f3bbd-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f3bbd-124">項目</span><span class="sxs-lookup"><span data-stu-id="f3bbd-124">Element</span></span>|<span data-ttu-id="f3bbd-125">描述</span><span class="sxs-lookup"><span data-stu-id="f3bbd-125">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services.md)|<span data-ttu-id="f3bbd-126">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-126">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3bbd-127">備註</span><span class="sxs-lookup"><span data-stu-id="f3bbd-127">Remarks</span></span>  

 <span data-ttu-id="f3bbd-128">服務定義於組態檔的 `services` 區段中。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-128">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="f3bbd-129">組件可包含任何數目的服務。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-129">An assembly can contain any number of services.</span></span> <span data-ttu-id="f3bbd-130">各服務都有自己的 `service` 組態區段。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-130">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="f3bbd-131">這個區段及其內容會定義特定服務的服務合約、行為和端點。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-131">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="f3bbd-132">`behaviorConfiguration` 項目也是選擇性。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-132">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="f3bbd-133">它會定義服務使用的行為。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-133">It identifies the behavior the service uses.</span></span> <span data-ttu-id="f3bbd-134">在這個屬性中指定的行為必須連結至相同組態檔案範圍內的行為。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-134">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="f3bbd-135">每一個服務會公開一或多個端點，每個端點擁有自己的位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-135">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="f3bbd-136">在組態檔中使用的所有繫結都必須定義在檔案的範圍內。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-136">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="f3bbd-137">繫結會透過 `name` 和 `bindingConfiguration` 屬性的組合，來連結至端點。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-137">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="f3bbd-138">`name` 屬性描述繫結定義所在的區段。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-138">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="f3bbd-139">`bindingConfiguration` 屬性定義要使用繫結區段中的哪一個組態。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-139">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="f3bbd-140">繫結區段可定義數個組態。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-140">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3bbd-141">範例</span><span class="sxs-lookup"><span data-stu-id="f3bbd-141">Example</span></span>  

 <span data-ttu-id="f3bbd-142">這是服務組態的範例。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-142">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"
         name="HelloWorld">
  <endpoint address="/HelloWorld2/"
            name="test"
            bindingNamespace="http://www.cohowinery.com/"
            binding="basicHttpBinding"
            contract="IHelloWorld" />
</service>
```  
  
## <a name="see-also"></a><span data-ttu-id="f3bbd-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3bbd-143">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="f3bbd-144">設定服務</span><span class="sxs-lookup"><span data-stu-id="f3bbd-144">Configuring Services</span></span>](../../../wcf/configuring-services.md)
