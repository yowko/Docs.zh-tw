---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: 8694f83a731363f83cb09de43214eb4b211ef5ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704280"
---
# <a name="comcontract"></a>\<comContract>
指定 COM+ 整合服務合約。  
  
 \<system.ServiceModel>  
\<comContracts>  
  
## <a name="syntax"></a>語法  
  
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
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|Contract - 合約|包含合約型別的字串。|  
|名稱|包含合約名稱的字串。|  
|namespace|包含合約命名空間的字串。|  
|requiresSession|布林值，指定合約是否只能用在工作階段繫結上。 當服務初始化時，整合執行階段會確保這個設定與要使用的繫結型別是一致的。 如果合約的一或多個繫結有衝突，便會產生例外狀況 (Exception)。 如果這個屬性是 `false`，而且正在使用單向通道且存在任何 [out] 參數時，也會產生例外狀況。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|persistableTypes|所有永久性型別。|  
|userDefinedTypes|要包含在服務合約中之使用者定義型別 (UDT) 的集合。|  
|exposedMethods|COM+ 方法的集合，這些方法會在 COM+ 元件上的介面公開為 Web 服務時公開。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|comContracts|包含 `comContract` 項目的集合。|  
  
## <a name="remarks"></a>備註  
 COM + 整合服務合約是目前僅限於`http://tempuri.org`命名空間，而合約名稱衍生自支援的 COM 介面。 然而，您可以使用 `comContracts` 區段，以及組態檔中的 `comContract` 項目，來指定替代項目。 例如，您可以使用下列組態來指定要包含的命名空間、合約名稱、使用者定義型別，以及服務合約的其他設定。  
  
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
  
 當服務初始化時，指定的命名空間和合約名稱就會套用至所產生的服務描述。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [整合 COM 應用程式](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [如何：設定 COM + 服務設定](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
