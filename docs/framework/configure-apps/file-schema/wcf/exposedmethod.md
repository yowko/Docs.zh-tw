---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 46f2872fb289c2793c356ea179deb3ce52e6d65e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855304"
---
# <a name="exposedmethod"></a><span data-ttu-id="9b5bc-101">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="9b5bc-101">\<exposedMethod></span></span>
<span data-ttu-id="9b5bc-102">表示 COM+ 方法，這個方法會在 COM+ 元件上的介面公開為 Web 服務時公開。</span><span class="sxs-lookup"><span data-stu-id="9b5bc-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
<span data-ttu-id="9b5bc-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9b5bc-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9b5bc-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9b5bc-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9b5bc-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContracts >** ](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="9b5bc-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="9b5bc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="9b5bc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="9b5bc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<exposedMethods >** ](exposedmethods.md)</span><span class="sxs-lookup"><span data-stu-id="9b5bc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)</span></span>\
<span data-ttu-id="9b5bc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<exposedMethod >**</span><span class="sxs-lookup"><span data-stu-id="9b5bc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b5bc-109">語法</span><span class="sxs-lookup"><span data-stu-id="9b5bc-109">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b5bc-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9b5bc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9b5bc-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9b5bc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b5bc-112">屬性</span><span class="sxs-lookup"><span data-stu-id="9b5bc-112">Attributes</span></span>  
  
|<span data-ttu-id="9b5bc-113">屬性</span><span class="sxs-lookup"><span data-stu-id="9b5bc-113">Attribute</span></span>|<span data-ttu-id="9b5bc-114">描述</span><span class="sxs-lookup"><span data-stu-id="9b5bc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9b5bc-115">NAME</span><span class="sxs-lookup"><span data-stu-id="9b5bc-115">name</span></span>|<span data-ttu-id="9b5bc-116">包含 COM+ 方法的字串，這個方法會在 COM+ 元件上的介面公開為 Web 服務時公開。</span><span class="sxs-lookup"><span data-stu-id="9b5bc-116">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b5bc-117">子元素</span><span class="sxs-lookup"><span data-stu-id="9b5bc-117">Child Elements</span></span>  
 <span data-ttu-id="9b5bc-118">無。</span><span class="sxs-lookup"><span data-stu-id="9b5bc-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b5bc-119">父項目</span><span class="sxs-lookup"><span data-stu-id="9b5bc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9b5bc-120">項目</span><span class="sxs-lookup"><span data-stu-id="9b5bc-120">Element</span></span>|<span data-ttu-id="9b5bc-121">描述</span><span class="sxs-lookup"><span data-stu-id="9b5bc-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b5bc-122">\<exposedMethods></span><span class="sxs-lookup"><span data-stu-id="9b5bc-122">\<exposedMethods></span></span>](exposedmethods.md)|<span data-ttu-id="9b5bc-123">[ \<ExposedMethod >](exposedmethod.md)元素的集合。</span><span class="sxs-lookup"><span data-stu-id="9b5bc-123">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b5bc-124">備註</span><span class="sxs-lookup"><span data-stu-id="9b5bc-124">Remarks</span></span>  
 <span data-ttu-id="9b5bc-125">COM+ 整合設定工具 (ComSvcConfig.exe) 可用來從 COM 介面加入特定的方法，使這些方法可以出現在所產生的服務合約上。</span><span class="sxs-lookup"><span data-stu-id="9b5bc-125">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="9b5bc-126">例如，您可以使用下列命令，從 `IFinances`.Financial 元件上的 `ItemOrders` COM 介面將三個具名方法加入至所產生的服務合約中。</span><span class="sxs-lookup"><span data-stu-id="9b5bc-126">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="9b5bc-127">當您同時執行 ComSvcConfig 時，它會產生下列服務合約，並將先前所述的方法列示為[ \<exposedMethod >](exposedmethod.md)元素。</span><span class="sxs-lookup"><span data-stu-id="9b5bc-127">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="9b5bc-128">在服務初始化期間，執行時間會藉由反映並僅新增[ \<exposedMethod >](exposedmethod.md)專案清單中包含的方法，嘗試產生服務合約。</span><span class="sxs-lookup"><span data-stu-id="9b5bc-128">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="9b5bc-129">這時會針對每個未包含在服務合約中的介面方法加以追蹤。</span><span class="sxs-lookup"><span data-stu-id="9b5bc-129">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b5bc-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b5bc-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="9b5bc-131">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="9b5bc-131">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="9b5bc-132">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="9b5bc-132">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="9b5bc-133">如何：設定 COM + 服務設定</span><span class="sxs-lookup"><span data-stu-id="9b5bc-133">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
