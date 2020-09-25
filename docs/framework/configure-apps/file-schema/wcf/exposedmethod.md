---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 2947f0de6a88f39463e58a3b39bda52588fe4baa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203900"
---
# \<exposedMethod>

<span data-ttu-id="00698-101">表示 COM+ 方法，這個方法會在 COM+ 元件上的介面公開為 Web 服務時公開。</span><span class="sxs-lookup"><span data-stu-id="00698-101">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**  
  
## <a name="syntax"></a><span data-ttu-id="00698-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="00698-102">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00698-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="00698-103">Attributes and Elements</span></span>  

 <span data-ttu-id="00698-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="00698-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00698-105">屬性</span><span class="sxs-lookup"><span data-stu-id="00698-105">Attributes</span></span>  
  
|<span data-ttu-id="00698-106">屬性</span><span class="sxs-lookup"><span data-stu-id="00698-106">Attribute</span></span>|<span data-ttu-id="00698-107">描述</span><span class="sxs-lookup"><span data-stu-id="00698-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00698-108">NAME</span><span class="sxs-lookup"><span data-stu-id="00698-108">name</span></span>|<span data-ttu-id="00698-109">包含 COM+ 方法的字串，這個方法會在 COM+ 元件上的介面公開為 Web 服務時公開。</span><span class="sxs-lookup"><span data-stu-id="00698-109">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00698-110">子元素</span><span class="sxs-lookup"><span data-stu-id="00698-110">Child Elements</span></span>  

 <span data-ttu-id="00698-111">無。</span><span class="sxs-lookup"><span data-stu-id="00698-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00698-112">父項目</span><span class="sxs-lookup"><span data-stu-id="00698-112">Parent Elements</span></span>  
  
|<span data-ttu-id="00698-113">項目</span><span class="sxs-lookup"><span data-stu-id="00698-113">Element</span></span>|<span data-ttu-id="00698-114">描述</span><span class="sxs-lookup"><span data-stu-id="00698-114">Description</span></span>|  
|-------------|-----------------|  
|[\<exposedMethods>](exposedmethods.md)|<span data-ttu-id="00698-115">專案的集合 [\<exposedMethod>](exposedmethod.md) 。</span><span class="sxs-lookup"><span data-stu-id="00698-115">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00698-116">備註</span><span class="sxs-lookup"><span data-stu-id="00698-116">Remarks</span></span>  

 <span data-ttu-id="00698-117">COM+ 整合設定工具 (ComSvcConfig.exe) 可用來從 COM 介面加入特定的方法，使這些方法可以出現在所產生的服務合約上。</span><span class="sxs-lookup"><span data-stu-id="00698-117">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="00698-118">例如，您可以使用下列命令，從 `IFinances`.Financial 元件上的 `ItemOrders` COM 介面將三個具名方法加入至所產生的服務合約中。</span><span class="sxs-lookup"><span data-stu-id="00698-118">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="00698-119">當您也執行 ComSvcConfig.exe 時，它會產生下列將上述方法列為專案的服務合約 [\<exposedMethod>](exposedmethod.md) 。</span><span class="sxs-lookup"><span data-stu-id="00698-119">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="00698-120">在服務初始化階段，執行時間會藉由反映並只加入專案清單中包含的方法，嘗試產生服務合約 [\<exposedMethod>](exposedmethod.md) 。</span><span class="sxs-lookup"><span data-stu-id="00698-120">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="00698-121">這時會針對每個未包含在服務合約中的介面方法加以追蹤。</span><span class="sxs-lookup"><span data-stu-id="00698-121">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00698-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00698-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="00698-123">與 COM + 應用程式整合</span><span class="sxs-lookup"><span data-stu-id="00698-123">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="00698-124">作法：設定 COM+ 服務設定</span><span class="sxs-lookup"><span data-stu-id="00698-124">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
