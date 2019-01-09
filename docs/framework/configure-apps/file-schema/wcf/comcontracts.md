---
title: '&lt;comContracts&gt;'
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 26f17a331d69c38d720fcafe65c76f50c67def09
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150782"
---
# <a name="ltcomcontractsgt"></a>&lt;comContracts&gt;
`comContracts` 組態區段包含的項目可讓您指定 COM+ 整合服務合約的各種屬性。  
  
## <a name="specifying-namespace-and-contract"></a>指定命名空間和合約  
 COM + 整合服務合約是目前僅限於`http://tempuri.org`命名空間，而合約名稱衍生自支援的 COM 介面。 然而，您可以使用組態檔中的 `comContracts` 區段來指定替代項目。  
  
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
  
 此外，您可以使用[ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)項目來指定 COM + 方法的 COM + 元件上的介面公開為 Web 服務時公開。 您也可以使用[ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)來指定整合中使用的永久性型別。 最後，您可以使用[ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)包含使用者定義型別 (UDT) 是包含服務合約中的項目。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [\<comContract>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [整合 COM 應用程式](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [如何：設定 COM + 服務設定](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
