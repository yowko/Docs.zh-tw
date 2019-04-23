---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: 8694f83a731363f83cb09de43214eb4b211ef5ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145063"
---
# <a name="comcontract"></a><span data-ttu-id="e7eac-101">\<comContract></span><span class="sxs-lookup"><span data-stu-id="e7eac-101">\<comContract></span></span>
<span data-ttu-id="e7eac-102">指定 COM+ 整合服務合約。</span><span class="sxs-lookup"><span data-stu-id="e7eac-102">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="e7eac-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e7eac-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e7eac-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="e7eac-104">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7eac-105">語法</span><span class="sxs-lookup"><span data-stu-id="e7eac-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7eac-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e7eac-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e7eac-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e7eac-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7eac-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e7eac-108">Attributes</span></span>  
  
|<span data-ttu-id="e7eac-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e7eac-109">Attribute</span></span>|<span data-ttu-id="e7eac-110">描述</span><span class="sxs-lookup"><span data-stu-id="e7eac-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7eac-111">Contract - 合約</span><span class="sxs-lookup"><span data-stu-id="e7eac-111">contract</span></span>|<span data-ttu-id="e7eac-112">包含合約型別的字串。</span><span class="sxs-lookup"><span data-stu-id="e7eac-112">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="e7eac-113">名稱</span><span class="sxs-lookup"><span data-stu-id="e7eac-113">name</span></span>|<span data-ttu-id="e7eac-114">包含合約名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="e7eac-114">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="e7eac-115">namespace</span><span class="sxs-lookup"><span data-stu-id="e7eac-115">namespace</span></span>|<span data-ttu-id="e7eac-116">包含合約命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="e7eac-116">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="e7eac-117">requiresSession</span><span class="sxs-lookup"><span data-stu-id="e7eac-117">requiresSession</span></span>|<span data-ttu-id="e7eac-118">布林值，指定合約是否只能用在工作階段繫結上。</span><span class="sxs-lookup"><span data-stu-id="e7eac-118">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="e7eac-119">當服務初始化時，整合執行階段會確保這個設定與要使用的繫結型別是一致的。</span><span class="sxs-lookup"><span data-stu-id="e7eac-119">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="e7eac-120">如果合約的一或多個繫結有衝突，便會產生例外狀況 (Exception)。</span><span class="sxs-lookup"><span data-stu-id="e7eac-120">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="e7eac-121">如果這個屬性是 `false`，而且正在使用單向通道且存在任何 [out] 參數時，也會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e7eac-121">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7eac-122">子元素</span><span class="sxs-lookup"><span data-stu-id="e7eac-122">Child Elements</span></span>  
  
|<span data-ttu-id="e7eac-123">項目</span><span class="sxs-lookup"><span data-stu-id="e7eac-123">Element</span></span>|<span data-ttu-id="e7eac-124">描述</span><span class="sxs-lookup"><span data-stu-id="e7eac-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7eac-125">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="e7eac-125">persistableTypes</span></span>|<span data-ttu-id="e7eac-126">所有永久性型別。</span><span class="sxs-lookup"><span data-stu-id="e7eac-126">All the persistable types.</span></span>|  
|<span data-ttu-id="e7eac-127">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="e7eac-127">userDefinedTypes</span></span>|<span data-ttu-id="e7eac-128">要包含在服務合約中之使用者定義型別 (UDT) 的集合。</span><span class="sxs-lookup"><span data-stu-id="e7eac-128">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="e7eac-129">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="e7eac-129">exposedMethods</span></span>|<span data-ttu-id="e7eac-130">COM+ 方法的集合，這些方法會在 COM+ 元件上的介面公開為 Web 服務時公開。</span><span class="sxs-lookup"><span data-stu-id="e7eac-130">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7eac-131">父項目</span><span class="sxs-lookup"><span data-stu-id="e7eac-131">Parent Elements</span></span>  
  
|<span data-ttu-id="e7eac-132">項目</span><span class="sxs-lookup"><span data-stu-id="e7eac-132">Element</span></span>|<span data-ttu-id="e7eac-133">描述</span><span class="sxs-lookup"><span data-stu-id="e7eac-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7eac-134">comContracts</span><span class="sxs-lookup"><span data-stu-id="e7eac-134">comContracts</span></span>|<span data-ttu-id="e7eac-135">包含 `comContract` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="e7eac-135">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7eac-136">備註</span><span class="sxs-lookup"><span data-stu-id="e7eac-136">Remarks</span></span>  
 <span data-ttu-id="e7eac-137">COM + 整合服務合約是目前僅限於`http://tempuri.org`命名空間，而合約名稱衍生自支援的 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="e7eac-137">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="e7eac-138">然而，您可以使用 `comContracts` 區段，以及組態檔中的 `comContract` 項目，來指定替代項目。</span><span class="sxs-lookup"><span data-stu-id="e7eac-138">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="e7eac-139">例如，您可以使用下列組態來指定要包含的命名空間、合約名稱、使用者定義型別，以及服務合約的其他設定。</span><span class="sxs-lookup"><span data-stu-id="e7eac-139">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="e7eac-140">當服務初始化時，指定的命名空間和合約名稱就會套用至所產生的服務描述。</span><span class="sxs-lookup"><span data-stu-id="e7eac-140">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7eac-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7eac-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="e7eac-142">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="e7eac-142">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="e7eac-143">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="e7eac-143">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="e7eac-144">如何：設定 COM + 服務設定</span><span class="sxs-lookup"><span data-stu-id="e7eac-144">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
