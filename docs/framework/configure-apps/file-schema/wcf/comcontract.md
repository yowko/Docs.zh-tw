---
title: '&lt;comContract&gt;'
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: 8e0e18c934589e89ff5e10b14ba02f8daee11c66
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146871"
---
# <a name="ltcomcontractgt"></a><span data-ttu-id="5b30e-102">&lt;comContract&gt;</span><span class="sxs-lookup"><span data-stu-id="5b30e-102">&lt;comContract&gt;</span></span>
<span data-ttu-id="5b30e-103">指定 COM+ 整合服務合約。</span><span class="sxs-lookup"><span data-stu-id="5b30e-103">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="5b30e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5b30e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5b30e-105">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="5b30e-105">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b30e-106">語法</span><span class="sxs-lookup"><span data-stu-id="5b30e-106">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b30e-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5b30e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5b30e-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5b30e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b30e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="5b30e-109">Attributes</span></span>  
  
|<span data-ttu-id="5b30e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5b30e-110">Attribute</span></span>|<span data-ttu-id="5b30e-111">描述</span><span class="sxs-lookup"><span data-stu-id="5b30e-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5b30e-112">Contract - 合約</span><span class="sxs-lookup"><span data-stu-id="5b30e-112">contract</span></span>|<span data-ttu-id="5b30e-113">包含合約型別的字串。</span><span class="sxs-lookup"><span data-stu-id="5b30e-113">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="5b30e-114">name</span><span class="sxs-lookup"><span data-stu-id="5b30e-114">name</span></span>|<span data-ttu-id="5b30e-115">包含合約名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="5b30e-115">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="5b30e-116">namespace</span><span class="sxs-lookup"><span data-stu-id="5b30e-116">namespace</span></span>|<span data-ttu-id="5b30e-117">包含合約命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="5b30e-117">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="5b30e-118">requiresSession</span><span class="sxs-lookup"><span data-stu-id="5b30e-118">requiresSession</span></span>|<span data-ttu-id="5b30e-119">布林值，指定合約是否只能用在工作階段繫結上。</span><span class="sxs-lookup"><span data-stu-id="5b30e-119">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="5b30e-120">當服務初始化時，整合執行階段會確保這個設定與要使用的繫結型別是一致的。</span><span class="sxs-lookup"><span data-stu-id="5b30e-120">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="5b30e-121">如果合約的一或多個繫結有衝突，便會產生例外狀況 (Exception)。</span><span class="sxs-lookup"><span data-stu-id="5b30e-121">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="5b30e-122">如果這個屬性是 `false`，而且正在使用單向通道且存在任何 [out] 參數時，也會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5b30e-122">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b30e-123">子元素</span><span class="sxs-lookup"><span data-stu-id="5b30e-123">Child Elements</span></span>  
  
|<span data-ttu-id="5b30e-124">項目</span><span class="sxs-lookup"><span data-stu-id="5b30e-124">Element</span></span>|<span data-ttu-id="5b30e-125">描述</span><span class="sxs-lookup"><span data-stu-id="5b30e-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b30e-126">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="5b30e-126">persistableTypes</span></span>|<span data-ttu-id="5b30e-127">所有永久性型別。</span><span class="sxs-lookup"><span data-stu-id="5b30e-127">All the persistable types.</span></span>|  
|<span data-ttu-id="5b30e-128">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="5b30e-128">userDefinedTypes</span></span>|<span data-ttu-id="5b30e-129">要包含在服務合約中之使用者定義型別 (UDT) 的集合。</span><span class="sxs-lookup"><span data-stu-id="5b30e-129">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="5b30e-130">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="5b30e-130">exposedMethods</span></span>|<span data-ttu-id="5b30e-131">COM+ 方法的集合，這些方法會在 COM+ 元件上的介面公開為 Web 服務時公開。</span><span class="sxs-lookup"><span data-stu-id="5b30e-131">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b30e-132">父項目</span><span class="sxs-lookup"><span data-stu-id="5b30e-132">Parent Elements</span></span>  
  
|<span data-ttu-id="5b30e-133">項目</span><span class="sxs-lookup"><span data-stu-id="5b30e-133">Element</span></span>|<span data-ttu-id="5b30e-134">描述</span><span class="sxs-lookup"><span data-stu-id="5b30e-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b30e-135">comContracts</span><span class="sxs-lookup"><span data-stu-id="5b30e-135">comContracts</span></span>|<span data-ttu-id="5b30e-136">包含 `comContract` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="5b30e-136">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b30e-137">備註</span><span class="sxs-lookup"><span data-stu-id="5b30e-137">Remarks</span></span>  
 <span data-ttu-id="5b30e-138">COM + 整合服務合約是目前僅限於`http://tempuri.org`命名空間，而合約名稱衍生自支援的 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="5b30e-138">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="5b30e-139">然而，您可以使用 `comContracts` 區段，以及組態檔中的 `comContract` 項目，來指定替代項目。</span><span class="sxs-lookup"><span data-stu-id="5b30e-139">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="5b30e-140">例如，您可以使用下列組態來指定要包含的命名空間、合約名稱、使用者定義型別，以及服務合約的其他設定。</span><span class="sxs-lookup"><span data-stu-id="5b30e-140">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="5b30e-141">當服務初始化時，指定的命名空間和合約名稱就會套用至所產生的服務描述。</span><span class="sxs-lookup"><span data-stu-id="5b30e-141">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b30e-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b30e-142">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="5b30e-143">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="5b30e-143">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="5b30e-144">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="5b30e-144">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="5b30e-145">如何：設定 COM + 服務設定</span><span class="sxs-lookup"><span data-stu-id="5b30e-145">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
