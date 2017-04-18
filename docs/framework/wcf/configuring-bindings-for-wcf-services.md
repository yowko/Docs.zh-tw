---
title: "設定 Windows Communication Foundation 服務的繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "繫結組態 [WCF]"
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
caps.latest.revision: 36
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 36
---
# 設定 Windows Communication Foundation 服務的繫結
建立應用程式時，您經常會需要在應用程式部署後，延後系統管理員的決定。例如，我們很多時都無法預知服務位址，或統一資源識別元 \(URI\)。這時候，為位址進行硬式編碼並不是理想的作法，較好的作法是讓系統管理員在建立服務後再處理。這樣的靈活性可以透過組態達成。  
  
> [!NOTE]
>  使用具有 `/config` 參數的 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 快速建立組態檔。  
  
## 主要區段  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 組態配置包括下列三個主要區段 \(`serviceModel`、`bindings`以及 `services`\)。  
  
```  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### ServiceModel 項目  
 您可使用 `system.ServiceModel` 項目界限的區段設定一個或更多端點的服務類型，以及服務的設定值。然後可以使用位址、合約與繫結來設定每個端點。[!INCLUDE[crabout](../../../includes/crabout-md.md)]端點的詳細資訊，請參閱[端點建立概觀](../../../docs/framework/wcf/endpoint-creation-overview.md)。如果沒有指定任何端點，則執行階段會加入預設端點。[!INCLUDE[crabout](../../../includes/crabout-md.md)]預設端點、繫結和行為的詳細資訊，請參閱[簡化的組態](../../../docs/framework/wcf/simplified-configuration.md)和 [WCF 服務的簡化組態](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
 繫結指定傳輸 \(HTTP、TCP、管道、訊息佇列\) 與通訊協定 \(安全性、可靠性、交易流\) 並且包含繫結項目，每個皆指定端點如何與外界通訊。  
  
 例如，指定 [\<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) 元件表示使用 HTTP 做為端點傳輸。這是在執行階段，當使用此端點的服務開啟時，用來連接端點。  
  
 有兩類的繫結：預先定義和自訂。預先定義的繫結包含有用的項目組合，在一般狀況下使用。如需 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 提供之預先定義繫結類型，請參閱 [系統提供的繫結](../../../docs/framework/wcf/system-provided-bindings.md)。如果沒有預先定義繫結集合擁有服務應用程式所需的正確功能組合，您可以建構自訂繫結來滿足應用程式的需求。[!INCLUDE[crabout](../../../includes/crabout-md.md)]自訂繫結的詳細資訊，請參閱[\<customBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。  
  
 以下四個範例說明用來設定 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務，最常見的繫結組態。  
  
#### 指定使用繫結型別的端點  
 第一個範例說明如何指定由位址、合約及繫結設定其組態的端點。  
  
```  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!—- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />  
  </endpoint>  
</service>  
```  
  
 在此範例中，`name` 屬性表示組態是針對哪種服務類型。當您在編碼中以 `HelloWorld` 合約建立服務，它將以範例組態定義的所有端點進行初始化。若組件只實作一份服務合約，則可省略 `name` 屬性，因為服務只使用可用的類型。該屬性取用一個字串，格式必須為 `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 `address` 屬性指定其他端點用來和服務通訊的 URI。URI 可能是絕對或相對路徑。如果提供相對位址，主機必須為繫結中使用的傳輸配置提供適當的基底位址。如果沒有設定位址，會將基底位址假設為該端點的位址。  
  
 `contract` 屬性指定此端點所公開的合約。服務實作型別必須實作合約類型。如果服務實作僅實作單一合約類型，便可省略這個屬性。  
  
 `binding` 屬性選擇此特定端點使用之預先定義或自訂繫結。未明確選擇繫結的端點會使用預設的繫結選擇，也就是 `BasicHttpBinding`。  
  
#### 修改預先定義繫結  
 下列範例會修改預先定義的繫結，然後就可以使用此繫結設定服務中的任何端點。設定 <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> 值為 1 秒以修改繫結。請注意，屬性傳回 <xref:System.TimeSpan> 物件。  
  
 更動後的繫結會在繫結區段內。如今當您設定 `endpoint` 項目的 `binding` 屬性建立任何端點時，都可以使用此已更動的繫結。  
  
> [!NOTE]
>  如果您賦予此繫結一個特定名稱，則服務端點所指定的 `bindingConfiguration` 必須與其相一致。  
  
```  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />  
  </endpoint>  
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## 設定行為以套用至服務  
 下列範例會針對服務類型設定特定行為。當中使用 `ServiceMetadataBehavior` 項目以啟用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)，查詢服務並從中繼資料產生 Web 服務描述語言 \(WSDL\) 文件。  
  
> [!NOTE]
>  如果您賦予此行為一個特定名稱，則服務或端點區段內所指定的 `behaviorConfiguration` 必須與其相一致。  
  
```  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />  
       </endpoint>  
    </service>  
</services>  
```  
  
 前述組態讓用戶端得以呼叫 "HelloWorld" 類型的服務並取得中繼資料。  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## 指定具有使用不同繫結值之兩端點的服務  
 在此最後的範例，兩個端點設定為 `HelloWorld` 服務類型。這兩個端點使用了自訂為不同  `bindingConfiguration` 屬性的同一繫結類型 \(各自修改 `basicHttpBinding`\)。  
  
```  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout"  
    </endpoint>  
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure"  
     </endpoint>  
</service>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
 您可以使用預設組態再加入 `protocolMapping` 區段並設定繫結，而得到同樣的行為，如下列範例所示。  
  
```xml  
<protocolMapping>  
    <add scheme=”http” binding=”basicHttpBinding” bindingConfiguration=”shortTimeout” />  
    <add scheme=”https” binding=”basicHttpBinding” bindingConfiguration=”Secure” />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## 請參閱  
 [簡化的組態](../../../docs/framework/wcf/simplified-configuration.md)   
 [系統提供的繫結](../../../docs/framework/wcf/system-provided-bindings.md)   
 [端點建立概觀](../../../docs/framework/wcf/endpoint-creation-overview.md)   
 [使用繫結來設定服務和用戶端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)