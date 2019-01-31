---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 151929cd99df08b705bee94eb6fd6f10c254a660
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259848"
---
# <a name="exposedmethod"></a><span data-ttu-id="a572c-101">\<exposedMethod></span><span class="sxs-lookup"><span data-stu-id="a572c-101">\<exposedMethod></span></span>
<span data-ttu-id="a572c-102">表示 COM+ 方法，這個方法會在 COM+ 元件上的介面公開為 Web 服務時公開。</span><span class="sxs-lookup"><span data-stu-id="a572c-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="a572c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a572c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a572c-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="a572c-104">\<comContracts></span></span>  
<span data-ttu-id="a572c-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="a572c-105">\<comContract></span></span>  
<span data-ttu-id="a572c-106">\<方法 ></span><span class="sxs-lookup"><span data-stu-id="a572c-106">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a572c-107">語法</span><span class="sxs-lookup"><span data-stu-id="a572c-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a572c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a572c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a572c-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a572c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a572c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a572c-110">Attributes</span></span>  
  
|<span data-ttu-id="a572c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a572c-111">Attribute</span></span>|<span data-ttu-id="a572c-112">描述</span><span class="sxs-lookup"><span data-stu-id="a572c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a572c-113">name</span><span class="sxs-lookup"><span data-stu-id="a572c-113">name</span></span>|<span data-ttu-id="a572c-114">包含 COM+ 方法的字串，這個方法會在 COM+ 元件上的介面公開為 Web 服務時公開。</span><span class="sxs-lookup"><span data-stu-id="a572c-114">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a572c-115">子元素</span><span class="sxs-lookup"><span data-stu-id="a572c-115">Child Elements</span></span>  
 <span data-ttu-id="a572c-116">無。</span><span class="sxs-lookup"><span data-stu-id="a572c-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a572c-117">父項目</span><span class="sxs-lookup"><span data-stu-id="a572c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a572c-118">項目</span><span class="sxs-lookup"><span data-stu-id="a572c-118">Element</span></span>|<span data-ttu-id="a572c-119">描述</span><span class="sxs-lookup"><span data-stu-id="a572c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a572c-120">\<exposedMethods></span><span class="sxs-lookup"><span data-stu-id="a572c-120">\<exposedMethods></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|<span data-ttu-id="a572c-121">集合[ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)項目。</span><span class="sxs-lookup"><span data-stu-id="a572c-121">A collection of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a572c-122">備註</span><span class="sxs-lookup"><span data-stu-id="a572c-122">Remarks</span></span>  
 <span data-ttu-id="a572c-123">COM+ 整合設定工具 (ComSvcConfig.exe) 可用來從 COM 介面加入特定的方法，使這些方法可以出現在所產生的服務合約上。</span><span class="sxs-lookup"><span data-stu-id="a572c-123">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="a572c-124">例如，您可以使用下列命令，從 `IFinances`.Financial 元件上的 `ItemOrders` COM 介面將三個具名方法加入至所產生的服務合約中。</span><span class="sxs-lookup"><span data-stu-id="a572c-124">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="a572c-125">當您也執行 ComSvcConfig.exe 時，它會產生下列服務合約上述方法列為[ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)項目。</span><span class="sxs-lookup"><span data-stu-id="a572c-125">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="a572c-126">在服務初始化階段，執行階段會嘗試反映，並加入只包含在清單中的方法來產生服務合約[ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)項目。</span><span class="sxs-lookup"><span data-stu-id="a572c-126">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span> <span data-ttu-id="a572c-127">這時會針對每個未包含在服務合約中的介面方法加以追蹤。</span><span class="sxs-lookup"><span data-stu-id="a572c-127">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a572c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a572c-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="a572c-129">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="a572c-129">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="a572c-130">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="a572c-130">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="a572c-131">如何：設定 COM + 服務設定</span><span class="sxs-lookup"><span data-stu-id="a572c-131">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
