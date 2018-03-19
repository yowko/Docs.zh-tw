---
title: '&lt;comContracts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69fbce3f312833c374a4c2615a15359d9c2db3a7
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="ltcomcontractsgt"></a><span data-ttu-id="9e0ed-102">&lt;comContracts&gt;</span><span class="sxs-lookup"><span data-stu-id="9e0ed-102">&lt;comContracts&gt;</span></span>
<span data-ttu-id="9e0ed-103">`comContracts` 組態區段包含的項目可讓您指定 COM+ 整合服務合約的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="9e0ed-103">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="9e0ed-104">指定命名空間和合約</span><span class="sxs-lookup"><span data-stu-id="9e0ed-104">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="9e0ed-105">COM + 整合服務合約會目前限制為 「http://tempuri.org"命名空間，而合約名稱衍生自支援的 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="9e0ed-105">COM+ integration service contracts are currently restricted to the "http://tempuri.org" namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="9e0ed-106">然而，您可以使用組態檔中的 `comContracts` 區段來指定替代項目。</span><span class="sxs-lookup"><span data-stu-id="9e0ed-106">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="9e0ed-107">例如，您可以使用下列組態來指定服務合約的命名空間和合約名稱，以及指定選項來強制工作階段繫結上的使用。</span><span class="sxs-lookup"><span data-stu-id="9e0ed-107">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="9e0ed-108">當服務初始化時，指定的命名空間和合約名稱就會套用至所產生的服務描述。</span><span class="sxs-lookup"><span data-stu-id="9e0ed-108">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="9e0ed-109">當這個區段是空白時，服務初始化會套用取自支援的 COM 介面 ID 的預設命名空間和合約名稱。</span><span class="sxs-lookup"><span data-stu-id="9e0ed-109">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="9e0ed-110">此外，您可以使用[ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)項目來指定 COM + COM + 元件上的介面公開為 Web 服務時公開的方法。</span><span class="sxs-lookup"><span data-stu-id="9e0ed-110">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="9e0ed-111">您也可以使用[ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)來指定用於整合的永久性類型。</span><span class="sxs-lookup"><span data-stu-id="9e0ed-111">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="9e0ed-112">最後，您可以使用[ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)包含使用者定義型別 (UDT) 包含服務合約中的項目。</span><span class="sxs-lookup"><span data-stu-id="9e0ed-112">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0ed-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e0ed-113">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="9e0ed-114">\<exposedMethod></span><span class="sxs-lookup"><span data-stu-id="9e0ed-114">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [<span data-ttu-id="9e0ed-115">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="9e0ed-115">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [<span data-ttu-id="9e0ed-116">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="9e0ed-116">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [<span data-ttu-id="9e0ed-117">\<comContract></span><span class="sxs-lookup"><span data-stu-id="9e0ed-117">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [<span data-ttu-id="9e0ed-118">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="9e0ed-118">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="9e0ed-119">如何：設定 COM+ 服務設定</span><span class="sxs-lookup"><span data-stu-id="9e0ed-119">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
