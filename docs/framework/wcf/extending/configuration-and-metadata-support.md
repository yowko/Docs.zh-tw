---
title: "組態與中繼資料支援 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 組態與中繼資料支援
這個主題描述如何啟用繫結和繫結項目的組態與中繼資料支援。  
  
## 組態與中繼資料概觀  
 這個主題討論下列工作，這些工作是[開發通道](../../../../docs/framework/wcf/extending/developing-channels.md)工作清單中的選用項目 1、2 和 4。  
  
-   啟用繫結項目的組態檔支援。  
  
-   啟用繫結的組態檔支援。  
  
-   匯出繫結項目的 WSDL 和原則判斷提示。  
  
-   識別要插入並設定繫結或繫結項目的 WSDL 和原則判斷提示。  
  
 如需建立使用者定義繫結和繫結項目的相關資訊，請分別參閱[建立使用者定義繫結](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)和[建立 BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)。  
  
## 新增組態支援  
 若要啟用通道的組態檔支援，您必須實作兩個組態區段，其中一個是 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=fullName>，它會啟用繫結項目的組態支援；而另一個是 <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=fullName> 和 <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=fullName>，它會啟用繫結的組態支援。  
  
 若要達到這個目的，其中一個較容易的方法是使用 [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) 範例工具，以產生繫結和繫結項目的組態程式碼。  
  
### 延伸 BindingElementExtensionElement  
 下列範例程式碼是取自[傳輸：UDP](../../../../docs/framework/wcf/samples/transport-udp.md) 範例。`UdpTransportElement` 是 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>，它會將 `UdpTransportBindingElement` 公開至組態系統。範例會使用一些基本的覆寫，定義組態區段名稱、繫結項目的型別，以及如何建立繫結項目。然後使用者可以在組態檔中登錄延伸區段，如同下列所示。  
  
```  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
  
```  
  
 您可以從自訂繫結參考該延伸，以使用 UDP 做為傳輸方式。  
  
```  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
  
```  
  
### 新增繫結組態  
 區段 `SampleProfileUdpBindingCollectionElement` 是 <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602>，它會將 `SampleProfileUdpBinding` 公開至組態系統。大量實作會委派至衍生自 <xref:System.ServiceModel.Configuration.StandardBindingElement> 的 `SampleProfileUdpBindingConfigurationElement`。`SampleProfileUdpBindingConfigurationElement` 的某些屬性會對應至 `SampleProfileUdpBinding` 的屬性，以及有些從 `ConfigurationElement` 繫結對應的函式。最後，在 `SampleProfileUdpBinding` 中會覆寫 `OnApplyConfiguration` 方法，如同下列範例程式碼所示。  
  
```  
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,  
                    "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",  
                    typeof(SampleProfileUdpBinding).AssemblyQualifiedName,  
                    binding.GetType().AssemblyQualifiedName));  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
  
```  
  
 若要使用組態系統註冊這個處理常式，請將下列區段新增至相關的組態檔。  
  
```  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 然後就可以從 [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 組態區段參考它。  
  
```  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
  
```  
  
## 新增繫結項目的中繼資料支援  
 若要將通道整合至中繼資料系統，通道必須同時支援匯入與匯出原則。這可以讓像是 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 的工具產生繫結項目的用戶端。  
  
### 新增 WSDL 支援  
 繫結中的傳輸繫結項目是負責匯出與匯入中繼資料中的定址資訊。當使用 SOAP 繫結時，傳輸繫結項目也應該匯出中繼資料中的正確傳輸 URI。下列範例程式碼是取自[傳輸：UDP](../../../../docs/framework/wcf/samples/transport-udp.md) 範例。  
  
#### WSDL 匯出  
 若要匯出定址資訊，`UdpTransportBindingElement` 會實作 <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=fullName>介面。<xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=fullName>方法會將正確的定址資訊加入至 WSDL 通訊埠。  
  
```  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 當端點使用 SOAP 繫結時，<xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> 方法的 `UdpTransportBindingElement` 實作也會匯出傳輸 URI：  
  
```  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### WSDL 匯入  
 若要延伸 WSDL 匯入系統以處理位址匯入，請將下列組態新增至 Svcutil.exe 的組態檔中，如同 Svcutil.exe.config 檔中所示：  
  
```  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 當執行 Svcutil.exe 時，有兩個選項可以讓 Svcutil.exe 載入 WSDL 匯入延伸：  
  
1.  使用 \/SvcutilConfig:\<file\> 將 Svcutil.exe 指向組態檔。  
  
2.  將組態區段新增至與 Svcutil.exe 位於相同目錄的 Svcutil.exe.config 中。  
  
 `UdpBindingElementImporter` 型別會實作 <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=fullName>介面。`ImportEndpoint` 方法會從 WSDL 連接埠匯入位址：  
  
```  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### 新增原則支援  
 自訂繫結項目可以匯出服務端點之 WSDL 繫結的原則判斷提示，以表示該繫結項目的功能。下列範例程式碼是取自[傳輸：UDP](../../../../docs/framework/wcf/samples/transport-udp.md) 範例。  
  
#### 原則匯出  
 `UdpTransportBindingElement` 型別會實作``<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName>以增加對匯出原則的支援。因此，<xref:System.ServiceModel.Description.MetadataExporter?displayProperty=fullName> 會針對包含它的任何繫結，在產生原則時包含 `UdpTransportBindingElement`。  
  
 在 <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=fullName> 中，新增 UDP 的判斷提示和其他判斷提示 \(如果通道使用多點傳送模式\)。這是因為多點傳送模式會影響通訊堆疊的建構方式，所以必須同時對兩端進行協調。  
  
```  
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.MulticastAssertion,     UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 因為自訂傳輸繫結項目會負責處理定址，所以 `UdpTransportBindingElement` 上的 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName> 實作也必須處理適當之 WS\-Addressing 原則判斷提示的匯出，以表示所使用的 WS\-Addressing 版本。  
  
```  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### 原則匯入  
 若要延伸原則匯入系統，請將下列組態新增至 Svcutil.exe 的組態檔中，如同 Svcutil.exe.config 檔中所示：  
  
```  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 然後從已註冊類別 \(`UdpBindingElementImporter`\) 實作 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName>。在 <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=fullName> 中，檢視適當命名空間的判斷提示，然後處理用來產生傳輸的判斷提示，並且檢查其是否使用多點傳送。此外，從繫結判斷提示清單中移除匯入工具處理的判斷提示。同樣地，當執行 Svcutil.exe 時有兩個整合的選項：  
  
1.  使用 \/SvcutilConfig:\<file\> 將 Svcutil.exe 指向組態檔。  
  
2.  將組態區段新增至與 Svcutil.exe 位於相同目錄的 Svcutil.exe.config 中。  
  
### 新增自訂標準繫結匯入工具  
 根據預設，Svcutil.exe 和 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName> 型別會識別與匯入系統提供的繫結。否則，會將繫結當做 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName> 執行個體匯入。為了讓 Svcutil.exe 和 <xref:System.ServiceModel.Description.WsdlImporter> 能夠匯入 `SampleProfileUdpBinding`，`UdpBindingElementImporter` 也會當做自訂標準繫結匯入工具。  
  
 自訂標準繫結匯入工具會實作 <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=fullName> 介面上的 `ImportEndpoint` 方法，檢視從中繼資料匯入的 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName>執行個體，以檢查特定標準繫結是否已產生該執行個體。  
  
```  
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 一般來說，實作自訂標準繫結匯入工具包含檢查已匯入之繫結項目的屬性，以驗證只有變更由標準繫結設定的屬性，而所有其他屬性都還是預設值。實作標準繫結匯入工具的基本策略，是建立標準繫結的執行個體、從繫結項目將屬性傳播至標準繫結支援的標準繫結執行個體，然後比較標準繫結與已匯入繫結項目上的繫結項目。