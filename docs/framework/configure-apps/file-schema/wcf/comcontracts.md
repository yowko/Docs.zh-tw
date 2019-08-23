---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: d061d48374a8745dc61e1ca156e4fcbbccee5ef7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919481"
---
# <a name="comcontracts"></a><span data-ttu-id="b43bd-101">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="b43bd-101">\<comContracts></span></span>
<span data-ttu-id="b43bd-102">`comContracts` 組態區段包含的項目可讓您指定 COM+ 整合服務合約的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="b43bd-102">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="b43bd-103">指定命名空間和合約</span><span class="sxs-lookup"><span data-stu-id="b43bd-103">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="b43bd-104">Com + 整合服務合約目前僅限於`http://tempuri.org`命名空間, 而合約名稱是衍生自支援的 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="b43bd-104">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="b43bd-105">然而，您可以使用組態檔中的 `comContracts` 區段來指定替代項目。</span><span class="sxs-lookup"><span data-stu-id="b43bd-105">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="b43bd-106">例如，您可以使用下列組態來指定服務合約的命名空間和合約名稱，以及指定選項來強制工作階段繫結上的使用。</span><span class="sxs-lookup"><span data-stu-id="b43bd-106">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="b43bd-107">當服務初始化時，指定的命名空間和合約名稱就會套用至所產生的服務描述。</span><span class="sxs-lookup"><span data-stu-id="b43bd-107">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="b43bd-108">當這個區段是空白時，服務初始化會套用取自支援的 COM 介面 ID 的預設命名空間和合約名稱。</span><span class="sxs-lookup"><span data-stu-id="b43bd-108">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="b43bd-109">此外, 您可以使用[ \<exposedMethod >](exposedmethod.md)專案, 指定在 com + 元件上的介面公開為 Web 服務時所公開的 com + 方法。</span><span class="sxs-lookup"><span data-stu-id="b43bd-109">In addition, you can use the [\<exposedMethod>](exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="b43bd-110">您也可以使用[ \<persistableTypes >](persistabletypes.md)來指定整合中使用的永久性類型。</span><span class="sxs-lookup"><span data-stu-id="b43bd-110">You can also use the [\<persistableTypes>](persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="b43bd-111">最後, 您可以使用[ \<userDefinedType >](userdefinedtype.md)元素來包含要包含在服務合約中的使用者定義類型 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="b43bd-111">Finally, you can use the [\<userDefinedType>](userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b43bd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b43bd-112">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="b43bd-113">\<exposedMethod></span><span class="sxs-lookup"><span data-stu-id="b43bd-113">\<exposedMethod></span></span>](exposedmethod.md)
- [<span data-ttu-id="b43bd-114">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="b43bd-114">\<persistableTypes></span></span>](persistabletypes.md)
- [<span data-ttu-id="b43bd-115">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="b43bd-115">\<userDefinedType></span></span>](userdefinedtype.md)
- [<span data-ttu-id="b43bd-116">\<comContract></span><span class="sxs-lookup"><span data-stu-id="b43bd-116">\<comContract></span></span>](comcontract.md)
- [<span data-ttu-id="b43bd-117">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="b43bd-117">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="b43bd-118">如何：設定 COM + 服務設定</span><span class="sxs-lookup"><span data-stu-id="b43bd-118">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
