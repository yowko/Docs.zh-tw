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
# <a name="comcontracts"></a>\<comContracts>
`comContracts` 組態區段包含的項目可讓您指定 COM+ 整合服務合約的各種屬性。  
  
## <a name="specifying-namespace-and-contract"></a>指定命名空間和合約  
 Com + 整合服務合約目前僅限於`http://tempuri.org`命名空間, 而合約名稱是衍生自支援的 COM 介面。 然而，您可以使用組態檔中的 `comContracts` 區段來指定替代項目。  
  
 例如，您可以使用下列組態來指定服務合約的命名空間和合約名稱，以及指定選項來強制工作階段繫結上的使用。  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 當服務初始化時，指定的命名空間和合約名稱就會套用至所產生的服務描述。  
  
 當這個區段是空白時，服務初始化會套用取自支援的 COM 介面 ID 的預設命名空間和合約名稱。  
  
 此外, 您可以使用[ \<exposedMethod >](exposedmethod.md)專案, 指定在 com + 元件上的介面公開為 Web 服務時所公開的 com + 方法。 您也可以使用[ \<persistableTypes >](persistabletypes.md)來指定整合中使用的永久性類型。 最後, 您可以使用[ \<userDefinedType >](userdefinedtype.md)元素來包含要包含在服務合約中的使用者定義類型 (UDT)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod>](exposedmethod.md)
- [\<persistableTypes>](persistabletypes.md)
- [\<userDefinedType>](userdefinedtype.md)
- [\<comContract>](comcontract.md)
- [整合 COM 應用程式](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [如何：設定 COM + 服務設定](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
