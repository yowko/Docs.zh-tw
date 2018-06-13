---
title: '&lt;服務&gt;'
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 6e83e988920d24c6fe7615e40334919caf21652e
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2018
ms.locfileid: "34059026"
---
# <a name="ltservicegt"></a><span data-ttu-id="452b6-102">&lt;服務&gt;</span><span class="sxs-lookup"><span data-stu-id="452b6-102">&lt;service&gt;</span></span>
<span data-ttu-id="452b6-103">`service` 項目包含 Windows Communication Foundation (WCF) 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="452b6-103">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="452b6-104">它也包含公開服務的端點。</span><span class="sxs-lookup"><span data-stu-id="452b6-104">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="452b6-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="452b6-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="452b6-106">\<services></span><span class="sxs-lookup"><span data-stu-id="452b6-106">\<services></span></span>  
<span data-ttu-id="452b6-107">\<服務 ></span><span class="sxs-lookup"><span data-stu-id="452b6-107">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="452b6-108">語法</span><span class="sxs-lookup"><span data-stu-id="452b6-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration=String"  
        name="String">  
</service>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="452b6-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="452b6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="452b6-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="452b6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="452b6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="452b6-111">Attributes</span></span>  
  
|<span data-ttu-id="452b6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="452b6-112">Attribute</span></span>|<span data-ttu-id="452b6-113">描述</span><span class="sxs-lookup"><span data-stu-id="452b6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="452b6-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="452b6-114">behaviorConfiguration</span></span>|<span data-ttu-id="452b6-115">字串，其中包含要用於產生服務實體之行為的行為名稱。</span><span class="sxs-lookup"><span data-stu-id="452b6-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="452b6-116">行為名稱必須在定義服務之處的範圍內。</span><span class="sxs-lookup"><span data-stu-id="452b6-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="452b6-117">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="452b6-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="452b6-118">name</span><span class="sxs-lookup"><span data-stu-id="452b6-118">name</span></span>|<span data-ttu-id="452b6-119">必要的字串屬性，其中指定要具現化的服務型別。</span><span class="sxs-lookup"><span data-stu-id="452b6-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="452b6-120">這個設定必須等同於有效的型別。</span><span class="sxs-lookup"><span data-stu-id="452b6-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="452b6-121">格式應該為 `Namespace.Class.`。</span><span class="sxs-lookup"><span data-stu-id="452b6-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="452b6-122">子項目</span><span class="sxs-lookup"><span data-stu-id="452b6-122">Child Elements</span></span>  
  
|<span data-ttu-id="452b6-123">項目</span><span class="sxs-lookup"><span data-stu-id="452b6-123">Element</span></span>|<span data-ttu-id="452b6-124">描述</span><span class="sxs-lookup"><span data-stu-id="452b6-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="452b6-125">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="452b6-125">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="452b6-126">公開此服務之 `endpoint` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="452b6-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="452b6-127">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="452b6-127">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="452b6-128">指定這個服務執行個體的主機。</span><span class="sxs-lookup"><span data-stu-id="452b6-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="452b6-129">此項目的型別為 <xref:System.ServiceModel.Configuration.HostElement>。</span><span class="sxs-lookup"><span data-stu-id="452b6-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="452b6-130">父項目</span><span class="sxs-lookup"><span data-stu-id="452b6-130">Parent Elements</span></span>  
  
|<span data-ttu-id="452b6-131">項目</span><span class="sxs-lookup"><span data-stu-id="452b6-131">Element</span></span>|<span data-ttu-id="452b6-132">描述</span><span class="sxs-lookup"><span data-stu-id="452b6-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="452b6-133">\<services></span><span class="sxs-lookup"><span data-stu-id="452b6-133">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="452b6-134">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="452b6-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="452b6-135">備註</span><span class="sxs-lookup"><span data-stu-id="452b6-135">Remarks</span></span>  
 <span data-ttu-id="452b6-136">服務定義於組態檔的 `services` 區段中。</span><span class="sxs-lookup"><span data-stu-id="452b6-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="452b6-137">組件可包含任何數目的服務。</span><span class="sxs-lookup"><span data-stu-id="452b6-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="452b6-138">各服務都有自己的 `service` 組態區段。</span><span class="sxs-lookup"><span data-stu-id="452b6-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="452b6-139">這個區段及其內容會定義特定服務的服務合約、行為和端點。</span><span class="sxs-lookup"><span data-stu-id="452b6-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="452b6-140">`behaviorConfiguration` 項目也是選擇性。</span><span class="sxs-lookup"><span data-stu-id="452b6-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="452b6-141">它會定義服務使用的行為。</span><span class="sxs-lookup"><span data-stu-id="452b6-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="452b6-142">在這個屬性中指定的行為必須連結至相同組態檔案範圍內的行為。</span><span class="sxs-lookup"><span data-stu-id="452b6-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="452b6-143">每一個服務會公開一或多個端點，每個端點擁有自己的位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="452b6-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="452b6-144">在組態檔中使用的所有繫結都必須定義在檔案的範圍內。</span><span class="sxs-lookup"><span data-stu-id="452b6-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="452b6-145">繫結會透過 `name` 和 `bindingConfiguration` 屬性的組合，來連結至端點。</span><span class="sxs-lookup"><span data-stu-id="452b6-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="452b6-146">`name` 屬性描述繫結定義所在的區段。</span><span class="sxs-lookup"><span data-stu-id="452b6-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="452b6-147">`bindingConfiguration` 屬性定義要使用繫結區段中的哪一個組態。</span><span class="sxs-lookup"><span data-stu-id="452b6-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="452b6-148">繫結區段可定義數個組態。</span><span class="sxs-lookup"><span data-stu-id="452b6-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="452b6-149">範例</span><span class="sxs-lookup"><span data-stu-id="452b6-149">Example</span></span>  
 <span data-ttu-id="452b6-150">這是服務組態的範例。</span><span class="sxs-lookup"><span data-stu-id="452b6-150">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"   
     name="HelloWorld">  
     <endpoint   
        address="/HelloWorld2/"  
        name="test"  
        bindingNamespace="http://www.cohowinery.com/"  
        binding="basicHttpBinding"  
        contract="IHelloWorld" />  
</service>  
```  
  
## <a name="see-also"></a><span data-ttu-id="452b6-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="452b6-151">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceElement>  
 [<span data-ttu-id="452b6-152">設定服務</span><span class="sxs-lookup"><span data-stu-id="452b6-152">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
