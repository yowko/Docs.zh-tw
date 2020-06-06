---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: c421273d1d08db047a51f1f1e4f9d6c908f12986
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "84201789"
---
# \<serviceMetadata>
指定服務中繼資料和相關資訊的發行。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceMetadata>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<serviceMetadata externalMetadataLocation="String"
                 httpGetBinding="String"
                 httpGetBindingConfiguration="String"
                 httpGetEnabled="Boolean"
                 httpGetUrl="String"
                 httpsGetBinding="String"
                 httpsGetBindingConfiguration="String"
                 httpsGetEnabled="Boolean"
                 httpsGetUrl="String"
                 policyVersion="Policy12/Policy15" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|externalMetadataLocation|包含 WSDL 檔案位置的 URI，此位置會傳回給使用者，以回應 WSDL 和 MEX 要求，而非自動產生的 WSDL。 如果未設定這個屬性，則會傳回預設 WSDL。 預設值是空字串。|  
|httpGetBinding|字串，這個字串會指定透過 HTTP GET 擷取中繼資料所要使用之繫結的型別。 這個設定是選擇性的。 如果未指定這個設定，則會使用預設的繫結。<br /><br /> 只有當繫結的內部繫結項目支援 <xref:System.ServiceModel.Channels.IReplyChannel> 時，這些繫結才會受到支援。 此外，該繫結的 <xref:System.ServiceModel.Channels.MessageVersion> 屬性 (Property) 必須是 <xref:System.ServiceModel.Channels.MessageVersion.None%2A>。|  
|httpGetBindingConfiguration|字串，這個字串會設定在 `httpGetBinding` 屬性中指定之繫結的名稱，該屬性會參考這個繫結中的其他組態資訊。 必須在 `<bindings>` 區段中定義相同的名稱。|  
|httpGetEnabled|布林值，指定是否發行服務中繼資料以使用 HTTP/Get 要求進行擷取。 預設值為 `false`。<br /><br /> 如果未指定 httpGetUrl 屬性，則中繼資料的發行位址會是服務位址加上 "?wsdl"。 例如，如果服務位址為 `http://localhost:8080/CalculatorService` ，則 HTTP/Get 中繼資料位址為 `http://localhost:8080/CalculatorService?wsdl` 。<br /><br /> 如果此屬性為 `false` ，或服務的位址不是以 HTTP 或 HTTPS 為基礎，則會忽略 "？ wsdl"。|  
|httpGetUrl|布林值，指定中繼資料的發行位址以使用 HTTP/Get 要求進行擷取。 如果已指定相對 URI，則視為相對於服務的基底位址。|  
|httpsGetBinding|字串，這個字串會指定透過 HTTPS GET 擷取中繼資料所要使用之繫結的型別。 這個設定是選擇性的。 如果未指定這個設定，則會使用預設的繫結。<br /><br /> 只有當繫結的內部繫結項目支援 <xref:System.ServiceModel.Channels.IReplyChannel> 時，這些繫結才會受到支援。 此外，該繫結的 <xref:System.ServiceModel.Channels.MessageVersion> 屬性 (Property) 必須是 <xref:System.ServiceModel.Channels.MessageVersion.None%2A>。|  
|httpsGetBindingConfiguration|字串，這個字串會設定在 `httpsGetBinding` 屬性中指定之繫結的名稱，該屬性會參考這個繫結中的其他組態資訊。 必須在 `<bindings>` 區段中定義相同的名稱。|  
|httpsGetEnabled|布林值，指定是否發行服務中繼資料以使用 HTTPS/Get 要求進行擷取。 預設值為 `false`。<br /><br /> 如果未指定 httpsGetUrl 屬性，則中繼資料的發行位址會是服務位址加上 "?wsdl"。 例如，如果服務位址是 " https://localhost:8080/CalculatorService "，則 HTTP/Get 中繼資料位址會是 " https://localhost:8080/CalculatorService?wsdl "。<br /><br /> 如果此屬性為 `false` ，或服務的位址不是以 HTTP 或 HTTPS 為基礎，則會忽略 "？ wsdl"。|  
|httpsGetUrl|URI，指定中繼資料的發行位址以使用 HTTPS/Get 要求進行擷取。|  
|policyVersion|字串，指定所要使用的 WS-Policy 規格版本。 此屬性的型別為 <xref:System.ServiceModel.Description.PolicyVersion>。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|指定行為項目。|  
  
## <a name="remarks"></a>備註  
 這個組態項目可讓您控制服務的中繼資料發行功能。 為避免不慎洩漏可能的敏感性服務中繼資料，Windows Communication Foundation （WCF）服務的預設設定會停用中繼資料發行。 這個行為依預設為安全行為，但也表示您無法使用中繼資料匯入工具 (例如 Svcutil.exe) 來產生呼叫服務所需的用戶端程式碼，除非組態中已明確啟用服務的中繼發行行為。 使用這個組態項目，您就可以為服務啟用此發行行為。  
  
 如需設定此行為的詳細範例，請參閱[中繼資料發行行為](../../../wcf/samples/metadata-publishing-behavior.md)。  
  
 選用的 `httpGetBinding` 和 `httpsGetBinding` 屬性可讓您設定透過 HTTP GET (或 HTTPS GET) 擷取中繼資料時所使用的繫結。 如果未指定這些繫結，則會依適當情形，使用預設的繫結 (使用 HTTP 時為 `HttpTransportBindingElement`，使用 HTTPS 時則為 `HttpsTransportBindingElement`) 擷取中繼資料。 請注意，這些屬性 (Attribute) 無法搭配內建的 WCF 繫結使用。 只有當繫結的內部繫結項目支援 <xref:System.ServiceModel.Channels.IReplyChannel> 時，這些繫結才會受到支援。 此外，該繫結的 <xref:System.ServiceModel.Channels.MessageVersion> 屬性 (Property) 必須是 <xref:System.ServiceModel.Channels.MessageVersion.None%2A>。  
  
 若要降低將服務暴露給惡意使用者的機會，可以使用 SSL over HTTP (HTTPS) 機制來進行安全的傳輸。 若要這麼做，您必須先將適當的 X.509 憑證，繫結至裝載服務之電腦上的特定連接埠  （如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)）。其次，將這個專案加入至服務設定，並將 `httpsGetEnabled` 屬性設為 `true` 。 最後，將 `httpsGetUrl` 屬性設定為服務中繼資料端點的 URL，如下列範例所示。  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="NewBehavior">
      <serviceMetadata httpsGetEnabled="true"
                       httpsGetUrl="https://myComputerName/myEndpoint" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="example"></a>範例  
 下列範例會使用專案來設定服務，以公開中繼資料 \<serviceMetadata> 。 它也設定了一個端點，將 `IMetadataExchange` 合約公開做為 WS-MetadataExchange (MEX) 通訊協定的實作。 此範例使用 `mexHttpBinding`，這個方便的標準繫結，相當於將安全性模式設定為 `wsHttpBinding` 的 `None`。 端點中會使用「mex」的相對位址，當針對服務基底位址進行解析時，會產生的端點位址 `http://localhost/servicemodelsamples/service.svc/mex` 。  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <!-- The serviceMetadata behavior publishes metadata through the IMetadataExchange contract. When this behavior is
               present, you can expose this contract through an endpoint as shown above. Setting httpGetEnabled to true publishes
               the service's WSDL at the <baseaddress>?wsdl eg. http://localhost/servicemodelsamples/service.svc?wsdl -->
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [安全性行為](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [中繼資料發行行為](../../../wcf/samples/metadata-publishing-behavior.md)
