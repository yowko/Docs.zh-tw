---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 69f3c70514fc2bcab1b4ef6a45036de98d1af7b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936517"
---
# <a name="service"></a><span data-ttu-id="9e974-101">\<service></span><span class="sxs-lookup"><span data-stu-id="9e974-101">\<service></span></span>
<span data-ttu-id="9e974-102">`service` 項目包含 Windows Communication Foundation (WCF) 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="9e974-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="9e974-103">它也包含公開服務的端點。</span><span class="sxs-lookup"><span data-stu-id="9e974-103">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="9e974-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9e974-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9e974-105">\<services></span><span class="sxs-lookup"><span data-stu-id="9e974-105">\<services></span></span>  
<span data-ttu-id="9e974-106">\<service></span><span class="sxs-lookup"><span data-stu-id="9e974-106">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e974-107">語法</span><span class="sxs-lookup"><span data-stu-id="9e974-107">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e974-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9e974-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9e974-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9e974-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e974-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9e974-110">Attributes</span></span>  
  
|<span data-ttu-id="9e974-111">屬性</span><span class="sxs-lookup"><span data-stu-id="9e974-111">Attribute</span></span>|<span data-ttu-id="9e974-112">描述</span><span class="sxs-lookup"><span data-stu-id="9e974-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e974-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="9e974-113">behaviorConfiguration</span></span>|<span data-ttu-id="9e974-114">字串，其中包含要用於產生服務實體之行為的行為名稱。</span><span class="sxs-lookup"><span data-stu-id="9e974-114">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="9e974-115">行為名稱必須在定義服務之處的範圍內。</span><span class="sxs-lookup"><span data-stu-id="9e974-115">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="9e974-116">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="9e974-116">The default value is an empty string.</span></span>|  
|<span data-ttu-id="9e974-117">NAME</span><span class="sxs-lookup"><span data-stu-id="9e974-117">name</span></span>|<span data-ttu-id="9e974-118">必要的字串屬性，其中指定要具現化的服務型別。</span><span class="sxs-lookup"><span data-stu-id="9e974-118">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="9e974-119">這個設定必須等同於有效的型別。</span><span class="sxs-lookup"><span data-stu-id="9e974-119">This setting must equate to a valid type.</span></span> <span data-ttu-id="9e974-120">格式應該為 `Namespace.Class.`。</span><span class="sxs-lookup"><span data-stu-id="9e974-120">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e974-121">子元素</span><span class="sxs-lookup"><span data-stu-id="9e974-121">Child Elements</span></span>  
  
|<span data-ttu-id="9e974-122">項目</span><span class="sxs-lookup"><span data-stu-id="9e974-122">Element</span></span>|<span data-ttu-id="9e974-123">說明</span><span class="sxs-lookup"><span data-stu-id="9e974-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e974-124">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="9e974-124">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="9e974-125">公開此服務之 `endpoint` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="9e974-125">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="9e974-126">\<host></span><span class="sxs-lookup"><span data-stu-id="9e974-126">\<host></span></span>](host.md)|<span data-ttu-id="9e974-127">指定這個服務執行個體的主機。</span><span class="sxs-lookup"><span data-stu-id="9e974-127">Specifies the host of this service instance.</span></span> <span data-ttu-id="9e974-128">此項目的型別為 <xref:System.ServiceModel.Configuration.HostElement>。</span><span class="sxs-lookup"><span data-stu-id="9e974-128">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9e974-129">父項目</span><span class="sxs-lookup"><span data-stu-id="9e974-129">Parent Elements</span></span>  
  
|<span data-ttu-id="9e974-130">項目</span><span class="sxs-lookup"><span data-stu-id="9e974-130">Element</span></span>|<span data-ttu-id="9e974-131">描述</span><span class="sxs-lookup"><span data-stu-id="9e974-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e974-132">\<services></span><span class="sxs-lookup"><span data-stu-id="9e974-132">\<services></span></span>](services.md)|<span data-ttu-id="9e974-133">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="9e974-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e974-134">備註</span><span class="sxs-lookup"><span data-stu-id="9e974-134">Remarks</span></span>  
 <span data-ttu-id="9e974-135">服務定義於組態檔的 `services` 區段中。</span><span class="sxs-lookup"><span data-stu-id="9e974-135">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="9e974-136">組件可包含任何數目的服務。</span><span class="sxs-lookup"><span data-stu-id="9e974-136">An assembly can contain any number of services.</span></span> <span data-ttu-id="9e974-137">各服務都有自己的 `service` 組態區段。</span><span class="sxs-lookup"><span data-stu-id="9e974-137">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="9e974-138">這個區段及其內容會定義特定服務的服務合約、行為和端點。</span><span class="sxs-lookup"><span data-stu-id="9e974-138">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="9e974-139">`behaviorConfiguration` 項目也是選擇性。</span><span class="sxs-lookup"><span data-stu-id="9e974-139">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="9e974-140">它會定義服務使用的行為。</span><span class="sxs-lookup"><span data-stu-id="9e974-140">It identifies the behavior the service uses.</span></span> <span data-ttu-id="9e974-141">在這個屬性中指定的行為必須連結至相同組態檔案範圍內的行為。</span><span class="sxs-lookup"><span data-stu-id="9e974-141">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="9e974-142">每一個服務會公開一或多個端點，每個端點擁有自己的位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="9e974-142">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="9e974-143">在組態檔中使用的所有繫結都必須定義在檔案的範圍內。</span><span class="sxs-lookup"><span data-stu-id="9e974-143">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="9e974-144">繫結會透過 `name` 和 `bindingConfiguration` 屬性的組合，來連結至端點。</span><span class="sxs-lookup"><span data-stu-id="9e974-144">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="9e974-145">`name` 屬性描述繫結定義所在的區段。</span><span class="sxs-lookup"><span data-stu-id="9e974-145">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="9e974-146">`bindingConfiguration` 屬性定義要使用繫結區段中的哪一個組態。</span><span class="sxs-lookup"><span data-stu-id="9e974-146">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="9e974-147">繫結區段可定義數個組態。</span><span class="sxs-lookup"><span data-stu-id="9e974-147">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e974-148">範例</span><span class="sxs-lookup"><span data-stu-id="9e974-148">Example</span></span>  
 <span data-ttu-id="9e974-149">這是服務組態的範例。</span><span class="sxs-lookup"><span data-stu-id="9e974-149">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9e974-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e974-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="9e974-151">設定服務</span><span class="sxs-lookup"><span data-stu-id="9e974-151">Configuring Services</span></span>](../../../wcf/configuring-services.md)
