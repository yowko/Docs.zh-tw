---
title: <endpoint> 項目
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: fb9d3bf9b5f1a742abcc70d78af026c179ec4c4d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855388"
---
# <a name="endpoint-element"></a>\<端點 > 元素
指定服務端點的繫結、合約和位址屬性，以用於公開服務。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<服務 >** ](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<服務 >** ](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<端點 >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|位址|包含端點位址的字串。 位址可以指定為絕對或相對位址。 如果提供相對位址，主機必須為繫結中使用的傳輸配置提供適當的基底位址。 如果沒有設定位址，會將基底位址假設為該端點的位址。<br /><br /> 預設值是空字串。|  
|behaviorConfiguration|字串，其中包含端點中所使用行為的名稱。|  
|繫結|必要的字串屬性，其中指定要使用的繫結型別。 此型別必須要有註冊的組態區段，才能加以參考。 型別是以區段名稱進行註冊，而非以繫結的型別名稱進行註冊。|  
|bindingConfiguration|字串，指定在產生端點時所使用繫結的繫結名稱。 繫結名稱必須在定義端點之處的範圍內。 預設值是空字串。<br /><br /> 這個屬性用於搭配 `binding` 使用，以參考組態檔中特定的繫結組態。 如果您要嘗試使用自訂繫結，請設定這個屬性。 否則，會擲回例外狀況。|  
|bindingName|字串，指定透過 WSDL 匯出定義之繫結的唯一限定名稱。 預設值是空字串。|  
|bindingNamespace|字串，指定透過 WSDL 匯出定義之繫結的命名空間限定名稱。 預設值是空字串。|  
|合約|指示這個端點要公開 (Expose) 之合約的字串。 組件必須實作合約類型。 如果服務實作實作單一合約類型，便可省略這個屬性。 預設值是空字串。|  
|endpointConfiguration|字串，這個字串會指定 `kind` 屬性所設定的標準端點名稱，該屬性會參考這個標準端點的其他組態資訊。 必須在 `<standardEndpoints>` 區段中定義相同的名稱。|  
|isSystemEndpoint|布林值，用於指定端點是否為基礎結構端點。|  
|kind|字串，這個字串會指定所套用之標準端點的型別。 型別必須要在 `<extensions>` 區段或 machine.config 中註冊。如果未指定任何內容，則會建立一般服務端點。|  
|listenUriMode|指定傳輸如何處理提供給服務接聽的 `ListenUri`。 有效值為<br /><br /> -Explicit<br />-唯一<br /><br /> 預設值為 Explicit。|  
|listenUri|字串，指定服務端點接聽的 URI。 預設值是空字串。|  
|NAME|選擇性屬性。 指定服務端點名稱的字串。 預設值是繫結名稱和合約描述名稱的串連。 服務可能會有多個端點，因此端點的 `name` 屬性會與服務的名稱有所區別。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<headers>](headers.md)|位址標頭的集合。|  
|[\<identity>](identity.md)|身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<service>](service.md)|組態區段，它會定義用戶端可以連線的端點清單。|  
  
## <a name="example"></a>範例  
 這是服務端點組態的範例。  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [終點位址、系結和合約](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [如何：在設定中建立服務端點](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
