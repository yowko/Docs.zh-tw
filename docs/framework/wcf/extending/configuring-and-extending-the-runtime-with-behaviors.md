---
title: 使用行為來設定與擴充執行階段
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 707b365a0f64055497e6b8814633acf7f4d7097c
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50041189"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>使用行為來設定與擴充執行階段
行為可讓您修改預設行為，並新增自訂延伸模組，檢查及驗證服務組態或修改在 Windows Communication Foundation (WCF) 用戶端和服務應用程式的執行階段行為。 本主題會說明行為介面、如何實作這些介面，以及如何透過程式設計方式或組態檔來將它們新增到服務描述 (在服務應用程式中) 或端點 (在用戶端應用程式中)。 如需使用系統提供行為的詳細資訊，請參閱 <<c0> [ 指定服務執行階段行為](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)並[指定用戶端執行階段行為](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)。  
  
## <a name="behaviors"></a>「行為」  
 行為類型會新增至服務或服務端點描述物件 (服務或用戶端，分別) 使用這些物件由 Windows Communication Foundation (WCF) 來建立執行 WCF 服務或 WCF 用戶端執行階段之前。 當在執行階段建構程序期間呼叫這些行為之後，這些行為即可存取可修改由合約、繫結及位址所構成之執行階段的執行階段屬性和方法。  
  
### <a name="behavior-methods"></a>行為方法  
 所有的行為方法都有 `AddBindingParameters` 方法、`ApplyDispatchBehavior` 方法、`Validate` 方法，以及例外的 `ApplyClientBehavior` 方法：因為 <xref:System.ServiceModel.Description.IServiceBehavior> 無法在用戶端中執行，因此它不會實作 `ApplyClientBehavior`。  
  
-   使用 `AddBindingParameters` 方法來修改自訂物件，或將其加入至自訂繫結可在執行階段建構時存取以供自己使用的集合中。 例如，在這種情況下，通道開發人員不知道實際影響通道建置方式的保護需求指定方式。  
  
-   使用 `Validate` 方法來檢查描述樹狀目錄和對應的執行階段物件，以確定該物件符合一些準則。  
  
-   使用 `ApplyDispatchBehavior` 和 `ApplyClientBehavior` 方法來檢查描述樹狀目錄，以及修改服務或用戶端上之特定範圍的執行階段。 您也可以插入擴充物件。  
  
    > [!NOTE]
    >  雖然在這些方法中有提供描述樹狀目錄，但它僅供檢查用途。 如果描述樹狀目錄遭到修改，該行為便屬於未定義的。  
  
 您可以修改的屬性及可以實作的自訂介面，將透過服務和用戶端執行階段類別來存取。 這些服務類型是 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 與 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別。 用戶端類型則是 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 與 <xref:System.ServiceModel.Dispatcher.ClientOperation> 類別。 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 與 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 類別分別是存取全用戶端及全服務執行階段屬性和擴充集合的擴充性進入點 (Entry Point)。 同樣地，<xref:System.ServiceModel.Dispatcher.ClientOperation> 與 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別會分別公開 (Expose) 用戶端作業及服務作業執行階段屬性和擴充集合。 不過，您可以從作業執行階段物件存取範圍更廣的執行階段物件，或是在需要時反向執行。  
  
> [!NOTE]
>  如需執行階段屬性和延伸模組類型可供您修改用戶端的執行行為的討論，請參閱 <<c0> [ 擴充用戶端](../../../../docs/framework/wcf/extending/extending-clients.md)。 如需執行階段屬性和延伸模組類型可供您修改服務發送器的執行行為的討論，請參閱 <<c0> [ 擴充發送器](../../../../docs/framework/wcf/extending/extending-dispatchers.md)。  
  
 大部分的 WCF 使用者直接; 不會互動的執行階段改為使用核心程式設計模型建構，例如端點、 合約、 繫結、 位址和行為上的類別或行為在組態檔中的屬性。 這些建構組成*描述樹狀目錄*，這是完整的規格來建構執行階段以支援服務，或描述樹狀結構所描述的用戶端。  
  
 有四種 WCF 中的行為：  
  
-   服務行為 (<xref:System.ServiceModel.Description.IServiceBehavior> 類型) 讓整個服務執行階段 (包括 <xref:System.ServiceModel.ServiceHostBase>) 能夠進行自訂。  
  
-   端點行為 (<xref:System.ServiceModel.Description.IEndpointBehavior> 類型) 讓服務端點及其關聯的 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 物件能夠進行自訂。  
  
-   合約行為 (<xref:System.ServiceModel.Description.IContractBehavior> 類型) 讓 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 與 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 類別能夠分別在用戶端及服務應用程式中進行自訂。  
  
-   作業行為 (<xref:System.ServiceModel.Description.IOperationBehavior> 類型) 同樣地讓 <xref:System.ServiceModel.Dispatcher.ClientOperation> 與 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別能在用戶端及服務上進行自訂。  
  
 將這些行為新增到各種描述物件的作業，可以透過實作自訂屬性、使用應用程式組態檔來完成，或是將這些行為直接新增到適當描述物件的行為集合中。 不過，在呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.ServiceHost><xref:System.ServiceModel.ChannelFactory%601>上的  之前，這些行為一定要先新增到服務描述或服務端點描述物件。  
  
### <a name="behavior-scopes"></a>行為範圍  
 這四個行為類型都會分別對應到執行階段存取的特定範圍。  
  
#### <a name="service-behaviors"></a>服務行為  
 實作 <xref:System.ServiceModel.Description.IServiceBehavior> 的服務行為，是您用來修改整個服務執行階段的主要機制。 將服務行為新增到服務時可使用三種機制。  
  
1.  在服務類別上使用屬性。  當已建構 <xref:System.ServiceModel.ServiceHost> 時，<xref:System.ServiceModel.ServiceHost> 實作 (Implementation) 會使用反映 (Reflection) 來找出該服務類型上的一組屬性。 如果其中任何一個屬性是 <xref:System.ServiceModel.Description.IServiceBehavior> 的實作，這組屬性便會新增到 <xref:System.ServiceModel.Description.ServiceDescription> 上的行為集合中。 這樣便可讓這些行為參與建構服務執行階段的程序。  
  
2.  以程式設計方式將行為新增到 <xref:System.ServiceModel.Description.ServiceDescription> 上的行為集合中。 運用下列幾行程式碼即可達成這點：  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3.  實作會擴充組態的自訂 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>。 這樣便可從應用程式組態檔使用服務行為。  
  
 在 WCF 中的服務行為的範例包括<xref:System.ServiceModel.ServiceBehaviorAttribute>屬性， <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>，和<xref:System.ServiceModel.Description.ServiceMetadataBehavior>行為。  
  
#### <a name="contract-behaviors"></a>合約行為  
 實作 <xref:System.ServiceModel.Description.IContractBehavior> 介面的合約行為，可用於擴充整個合約的用戶端與服務執行階段。  
  
 將合約行為新增到合約時可以使用兩種機制。  第一種機制是建立要在合約介面上使用的自訂屬性。 當合約介面傳遞至<xref:System.ServiceModel.ServiceHost>或<xref:System.ServiceModel.ChannelFactory%601>，WCF 會檢查在介面上的屬性。 如果其中任何一個屬性是 <xref:System.ServiceModel.Description.IContractBehavior> 的實作，這些屬性便會新增到為該介面建立之 <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> 上的行為集合中。  
  
 您也可以在自訂合約行為屬性上實作 <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType>。 在此情況下，將依套用對象產生類似下列的行為：  
  
 •合約介面。 在此情況下，行為會套用至任何端點中該類型的所有合約，WCF 會忽略值<xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType>屬性。  
  
 •服務類別。 在此情況下，行為只會套用至其中合約為 <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> 屬性值的端點。  
  
 •回呼類別。 在此情況下，行為會套用至雙工用戶端的端點，WCF 會忽略值<xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A>屬性。  
  
 第二種機制是將行為新增至 <xref:System.ServiceModel.Description.ContractDescription> 上的行為集合。  
  
 在 WCF 中的合約行為的範例包括<xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType>屬性。 如需詳細資訊和範例，請參閱參考主題。  
  
#### <a name="endpoint-behaviors"></a>端點行為  
 實作 <xref:System.ServiceModel.Description.IEndpointBehavior> 的端點行為，是您用來針對特定端點修改整個服務或用戶端執行階段的主要機制。  
  
 將端點行為新增到服務時可以使用兩種機制。  
  
1.  將行為新增到 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 屬性。  
  
2.  實作會擴充組態的自訂 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>。  
  
 如需詳細資訊和範例，請參閱參考主題。  
  
#### <a name="operation-behaviors"></a>作業行為  
 實作 <xref:System.ServiceModel.Description.IOperationBehavior> 介面的作業行為，可用來擴充每個作業的用戶端與服務執行階段。  
  
 將作業行為新增到作業時可以使用兩種機制。 第一種機制是建立要用於建立作業模型之方法的自訂屬性。 當將作業新增至<xref:System.ServiceModel.ServiceHost>或<xref:System.ServiceModel.ChannelFactory>，WCF 新增<xref:System.ServiceModel.Description.IOperationBehavior>屬性的行為集合<xref:System.ServiceModel.Description.OperationDescription>建立該作業。  
  
 第二種機制是將行為直接新增至已建構 <xref:System.ServiceModel.Description.OperationDescription> 上的行為集合中。  
  
 在 WCF 中的作業行為的範例包括<xref:System.ServiceModel.OperationBehaviorAttribute>而<xref:System.ServiceModel.TransactionFlowAttribute>。  
  
 如需詳細資訊和範例，請參閱參考主題。  
  
### <a name="using-configuration-to-create-behaviors"></a>使用組態來建立行為  
 服務行為、端點行為以及合約行為都可以設計成透過程式碼或使用屬性來加以指定；只有服務行為和端點行為可以使用應用程式或 Web 組態檔來加以設定。 使用屬性公開行為，可讓開發人員在編譯時期指定在執行階段時所無法新增、移除或修改的行為。 這種做法往往適用於正確服務作業一定需要的行為 (例如，<xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> 屬性的交易相關參數)。 使用組態公開行為，可讓開發人員將這些行為的規格和組態留給部署該服務的人員來決定。 這種做法適用於屬於選擇性元件或其他部署特定組態的行為，例如是否要向服務公開中繼資料，或是服務的特定授權組態。  
  
> [!NOTE]
>  您也可以使用支援組態強制公司應用程式原則的行為，使用方法是將這些行為插入 machine.config 組態檔，並鎖定這些項目。 如需說明和範例，請參閱 < [How to: Lock Down Endpoints in 企業](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)。  
  
 若要使用組態公開行為，開發人員必須建立 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 的衍生類別 (Derived Class)，然後再向組態註冊該延伸。  
  
 下列程式碼範例會示範 <xref:System.ServiceModel.Description.IEndpointBehavior> 如何實作 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>：  
  
```csharp
// BehaviorExtensionElement members  
public override Type BehaviorType  
{  
  get { return typeof(EndpointBehaviorMessageInspector); }  
}  
  
protected override object CreateBehavior()  
{  
  return new EndpointBehaviorMessageInspector();  
}  
```  
  
 為了讓組態系統載入自訂 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>，此項目必須註冊為延伸。 下列程式碼範例顯示了前述端點行為的組態檔：  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
        name="Microsoft.WCF.Documentation.SampleService"  
        behaviorConfiguration="metadataSupport"  
      >  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8080/ServiceMetadata" />  
          </baseAddresses>  
        </host>  
        <endpoint  
          address="/SampleService"  
          binding="wsHttpBinding"  
          behaviorConfiguration="withMessageInspector"   
          contract="Microsoft.WCF.Documentation.ISampleService"  
        />  
        <endpoint  
           address="mex"  
           binding="mexHttpBinding"  
           contract="IMetadataExchange"  
        />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="metadataSupport">  
        <serviceMetadata httpGetEnabled="true" httpGetUrl=""/>  
      </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="withMessageInspector">  
          <endpointMessageInspector />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <extensions>  
      <behaviorExtensions>  
        <add   
          name="endpointMessageInspector"  
          type="Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector, HostApplication, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"  
        />  
      </behaviorExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 何處`Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector`是行為延伸型別和`HostApplication`是該類別已編譯所在的組件的名稱。  
  
### <a name="evaluation-order"></a>評估順序  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 和 <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> 會負責從程式設計模型及描述來建置執行階段。 正如先前所述，行為會作用於位在服務、端點、合約及作業時的建置程序。  
  
 <xref:System.ServiceModel.ServiceHost> 會依照下列順序來套用行為：  
  
1.  服務  
  
2.  合約  
  
3.  端點  
  
4.  運算  
  
 在任何行為集合內，並不會保證任何順序。  
  
 <xref:System.ServiceModel.ChannelFactory%601> 會依照下列順序來套用行為：  
  
1.  合約  
  
2.  端點  
  
3.  運算  
  
 同樣地，在任何行為集合內，並不會保證任何順序。  
  
### <a name="adding-behaviors-programmatically"></a>以程式設計方式來新增行為  
 在服務應用程式中 <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> 的屬性，絕對不能在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> 上的 <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> 方法之後遭到修改。 有些方法在通過該點後若遭到修改，就會擲回例外狀況，這些方法包括 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> 屬性，以及在 `AddServiceEndpoint` 與 <xref:System.ServiceModel.ServiceHostBase> 上的 <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> 方法。 其他成員可讓您加以修改，但結果仍未定義。  
  
 同樣地，您不可以在呼叫 <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> 上的 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 之後修改用戶端上的 <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> 值。 如果 <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> 屬性在通過該點之後遭到修改，它便會擲回例外狀況，不過其他用戶端描述值在遭到修改時並不會造成錯誤。 不過產生結果將會是未定義的。  
  
 無論是在服務或是用戶端，建議的做法都是在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> 之前修改說明。  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>行為屬性的繼承規則  
 這四種行為都可以使用屬性 (服務行為與合約行為) 來填入。 由於屬性是定義在 Managed 物件與成員上，而 Managed 物件與成員會支援繼承 (Inheritance)，所以這時必須定義行為屬性在繼承內容中的運作方式。  
  
 在高層級的規則是指針對特定範圍 (例如，服務、合約或作業) 的規則，而繼承階層架構 (Inheritance Hierarchy) 中的所有行為屬性是指針對該範圍所套用的行為屬性。 如果這時出現兩個相同型別的行為屬性，將只套用最末層衍生型別。  
  
#### <a name="service-behaviors"></a>服務行為  
 對於特定的服務類別，將套用該類別及其父代 (Parent) 上的所有服務行為屬性。 如果相同型別的屬性套用在繼承階層架構的多個位置，這時會使用最具衍生性的型別。  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 例如，在上述範例中，服務 B 最後產生 <xref:System.ServiceModel.InstanceContextMode><xref:System.ServiceModel.InstanceContextMode.Single>的 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode>、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> 的 <xref:System.ServiceModel.ConcurrencyMode> 模式，以及 <xref:System.ServiceModel.ConcurrencyMode.Single> 的 。 由於服務 B 上的 <xref:System.ServiceModel.ConcurrencyMode> 屬性比服務 A 上的相同屬性「更具衍生性」，所以 <xref:System.ServiceModel.ConcurrencyMode.Single> 會是 <xref:System.ServiceModel.ServiceBehaviorAttribute>。  
  
#### <a name="contract-behaviors"></a>合約行為  
 對於指定的合約，將套用該介面及其父代上的所有合約行為屬性。 如果相同型別的屬性套用在繼承階層架構的多個位置，這時會使用最具衍生性的型別。  
  
#### <a name="operation-behaviors"></a>作業行為  
 如果指定的作業沒有覆寫現有的抽象或虛擬作業，就不會套用任何繼承規則。  
  
 如果作業確實覆寫了現有的作業，這時將套用該作業及其父代上的所有作業行為屬性。  如果相同型別的屬性套用在繼承階層架構的多個位置，這時會使用最具衍生性的型別。
