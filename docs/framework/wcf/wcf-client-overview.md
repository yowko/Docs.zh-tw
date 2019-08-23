---
title: WCF 用戶端概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: adaaca596650c5bff486bd0c295c4f840ae58051
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916875"
---
# <a name="wcf-client-overview"></a>WCF 用戶端概觀
本節描述用戶端應用程式的用途、如何設定、建立和使用 Windows Communication Foundation (WCF) 用戶端, 以及如何保護用戶端應用程式。  
  
## <a name="using-wcf-client-objects"></a>使用 WCF 用戶端物件  
 用戶端應用程式是一個使用 WCF 用戶端與另一個應用程式通訊的受控應用程式。 若要建立 WCF 服務的用戶端應用程式, 需要執行下列步驟:  
  
1. 取得服務端點的服務合約、繫結和位址資訊。  
  
2. 使用該資訊建立 WCF 用戶端。  
  
3. 呼叫作業。  
  
4. 關閉 WCF 用戶端物件。  
  
 下列各節將討論這些步驟，並簡要介紹以下問題：  
  
- 處理錯誤。  
  
- 設定和保護用戶端。  
  
- 建立雙工服務的回呼物件。  
  
- 非同步呼叫服務。  
  
- 透過用戶端通道呼叫服務。  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>取得服務合約、繫結和位址  
 在 WCF 中, 服務和用戶端會使用 managed 屬性、介面和方法來模型合約。 若要在用戶端應用程式中連接到服務，您必須取得服務合約的類型資訊。 一般來說, 您會使用[System.servicemodel 中繼資料公用程式工具 (Svcutil)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來執行這項操作, 這會從服務下載中繼資料, 並以您選擇的語言將它轉換成 managed 原始程式碼檔, 並建立用戶端應用程式設定檔, 您可以使用來設定 WCF 用戶端物件。 例如, 如果您要建立 WCF 用戶端物件來叫用`MyCalculatorService`, 而且您知道該服務的中繼資料是在`http://computerName/MyCalculatorService/Service.svc?wsdl`發行, 則下列程式碼範例會示範如何使用 Svcutil 來取得`ClientCode.vb`檔案,包含 managed 程式碼中的服務合約。  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 您可以將此合約程式碼編譯成用戶端應用程式, 或編譯成用戶端應用程式可以用來建立 WCF 用戶端物件的另一個元件。 您可以使用組態檔來設定用戶端物件，以便正確連接到服務。  
  
 如需此程式的範例, 請[參閱如何:建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。 如需有關合約的完整資訊, 請參閱[合約](../../../docs/framework/wcf/feature-details/contracts.md)。  
  
## <a name="create-a-wcf-client-object"></a>建立 WCF 用戶端物件  
 WCF 用戶端是一個代表 WCF 服務的本機物件, 而用戶端可以使用它來與遠端服務進行通訊。 WCF 用戶端類型會實作為目標服務合約, 因此當您建立一個並設定它時, 可以直接使用用戶端物件來叫用服務作業。 WCF 執行時間會將方法呼叫轉換為訊息、將其傳送至服務、接聽回復, 然後將這些值當做傳回值或`out`或`ref`參數傳回給 WCF 用戶端物件。  
  
 您也可以使用 WCF 用戶端通道物件來連接及使用服務。 如需詳細資訊, 請參閱[WCF 用戶端架構](../../../docs/framework/wcf/feature-details/client-architecture.md)。  
  
#### <a name="creating-a-new-wcf-object"></a>建立新的 WCF 物件  
 為說明 <xref:System.ServiceModel.ClientBase%601> 類別的使用方式，請假設已從服務應用程式產生下列簡單服務合約。  
  
> [!NOTE]
> 如果您使用 Visual Studio 建立 WCF 用戶端, 當您將服務參考加入至專案時, 物件就會自動載入至 [物件瀏覽器] 中。  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 如果您不是使用 Visual Studio, 請檢查產生的合約程式碼, 以尋找擴充<xref:System.ServiceModel.ClientBase%601>和服務合約介面`ISampleService`的型別。 在這種情況下，該型別看起來類似下列程式碼：  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 您可以將這個類別建立成本機物件，其方式是使用其中一個建構函式，然後加以設定，再用來連接到型別為 `ISampleService` 的服務。  
  
 建議您先建立 WCF 用戶端物件, 然後使用它並在單一 try/catch 區塊內將它關閉。 您不應該使用`using`語句 (`Using`在 Visual Basic 中), 因為它可能會遮罩特定失敗模式的例外狀況。 如需詳細資訊, 請參閱下列各節, 以及[使用 Close 和 Abort 釋放 WCF 用戶端資源](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)。  
  
### <a name="contracts-bindings-and-addresses"></a>合約、繫結和位址  
 建立 WCF 用戶端物件之前, 您必須先設定用戶端物件。 具體而言, 它必須具有要使用的服務*端點*。 端點是服務合約、繫結和位址的組合 (如需有關端點的詳細資訊[, 請參閱端點:位址、系結和合約](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)。)一般來說, 這項資訊位於用戶端應用程式設定檔中的[ \<端點 >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)專案 (例如 Svcutil 所產生的專案), 而且會在您建立用戶端物件時自動載入。 這兩種 WCF 用戶端類型也有多載, 可讓您以程式設計方式指定這項資訊。  
  
 例如，針對前面範例中使用的 `ISampleService` 所產生的組態檔會包含下列端點資訊。  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 這個組態檔會在 `<client>` 元素中指定目標端點。 如需使用多個目標端點的詳細資訊, <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType>請參閱<xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType>或函數。  
  
## <a name="calling-operations"></a>呼叫作業  
 建立並設定用戶端物件之後, 請建立 try/catch 區塊, 呼叫作業的方式與物件是否為 local 時相同, 然後關閉 WCF 用戶端物件。 當用戶端應用程式呼叫第一個作業時, WCF 會自動開啟基礎通道, 而當物件被回收時, 會關閉基礎通道。 (或者，您也可以在呼叫其他作業之前或之後明確地開啟和關閉通道)。  
  
 例如，您若有下列服務合約：  
  
```csharp  
namespace Microsoft.ServiceModel.Samples  
{  
    using System;  
    using System.ServiceModel;  
  
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
   {  
        [OperationContract]  
        double Add(double n1, double n2);  
        [OperationContract]  
        double Subtract(double n1, double n2);  
        [OperationContract]  
        double Multiply(double n1, double n2);  
        [OperationContract]  
        double Divide(double n1, double n2);  
    }  
}  
```  
  
```vb  
Namespace Microsoft.ServiceModel.Samples  
  
    Imports System  
    Imports System.ServiceModel  
  
    <ServiceContract(Namespace:= _  
    "http://Microsoft.ServiceModel.Samples")> _   
   Public Interface ICalculator  
        <OperationContract> _   
        Function Add(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Subtract(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Multiply(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
     Function Divide(n1 As Double, n2 As Double) As Double  
End Interface  
```  
  
 您可以藉由建立 WCF 用戶端物件並呼叫其方法來呼叫作業, 如下列程式碼範例所示。 請注意, WCF 用戶端物件的開啟、呼叫和關閉會出現在單一 try/catch 區塊中。 如需詳細資訊, 請參閱[使用 WCF 用戶端存取服務](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)和[使用 Close 和 Abort 釋放 WCF 用戶端資源](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)。  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>處理錯誤  
 當開啟基礎用戶端通道 (無論是明確或是自動呼叫作業)、使用用戶端或通道物件來呼叫作業，或關閉基礎用戶端通道時，都可能會在用戶端應用程式中發生例外狀況。 除了要由作業傳回因 SOAP 錯誤而擲回的任何 <xref:System.TimeoutException?displayProperty=nameWithType> 物件之外，建議您最少還要讓應用程式有能力處理可能發生的 <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> 和 <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> 例外狀況。 作業合約中指定的 SOAP 錯誤會針對用戶端應用程式引發為 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>，其中的型別參數是 SOAP 錯誤的詳細類型。 如需有關在用戶端應用程式中處理錯誤狀況的詳細資訊, 請參閱傳送[和接收錯誤](../../../docs/framework/wcf/sending-and-receiving-faults.md)。 如需說明如何在用戶端中處理錯誤的完整範例, 請參閱[預期的例外](../../../docs/framework/wcf/samples/expected-exceptions.md)狀況。  
  
## <a name="configuring-and-securing-clients"></a>設定和保護用戶端  
 設定用戶端時，通常是先從組態檔載入用戶端或通道物件的必要目標端點資訊；儘管可以透過用戶端建構函式和屬性，使用程式設計方式載入這項資訊， 但是為了啟用特定用戶端行為，並符合許多安全性案例的需要，您應該另外執行其他必要的設定步驟。  
  
 例如，服務合約的安全性需求會在服務合約介面中宣告；如果 Svcutil.exe 建立了組態檔，這個檔案通常應包含能夠支援服務安全性需求的繫結。 不過，在某些情況下，可能需要進行更多的安全性設定，例如設定用戶端認證。 如需 WCF 用戶端安全性設定的完整資訊, 請參閱[保護用戶端](../../../docs/framework/wcf/securing-clients.md)。  
  
 此外，還可以在用戶端應用程式中啟用某些自訂修改，例如自訂執行階段行為。 如需如何設定自訂用戶端行為的詳細資訊, 請參閱設定[用戶端](../../../docs/framework/wcf/configuring-client-behaviors.md)行為。  
  
## <a name="creating-callback-objects-for-duplex-services"></a>建立雙工服務的回呼物件  
 雙工服務會指定回呼合約，這是用戶端應用程式為了在服務根據合約需求進行呼叫時提供其所需之回呼物件而必須實作的合約。 雖然回呼物件並非完整的服務 (例如，您無法透過回呼物件啟始通道)，但基於實作和組態設定的目的，不妨將它們視為一種服務。  
  
 雙工服務的用戶端必須：  
  
- 實作回呼合約類別。  
  
- 建立回呼合約實類別的實例, 並使用它來建立<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>傳遞給 WCF 用戶端程式的物件。  
  
- 叫用作業和處理作業回呼。  
  
 雙工 WCF 用戶端物件的運作方式類似其非雙工對應專案, 唯一的例外是它們會公開支援回呼所需的功能, 包括回呼服務的設定。  
  
 例如，您可以在回呼類別上使用 <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> 屬性 (Attribute) 的屬性 (Property)，控制回呼物件執行階段行為的各種層面。 此外，還可以使用 <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> 類別，讓例外狀況資訊回傳給呼叫回呼物件的服務。 如需詳細資訊, 請參閱[雙工服務](../../../docs/framework/wcf/feature-details/duplex-services.md)。 如需完整範例, 請參閱[雙工](../../../docs/framework/wcf/samples/duplex.md)。  
  
 在執行 Internet Information Services (IIS) 5.1 的 Windows XP 電腦上，雙工用戶端必須使用 <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> 類別來指定用戶端基底位址，否則會擲回例外狀況。 下列程式碼範例示範如何在程式碼中執行這項工作。  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 下列程式碼範例示範如何在組態檔中執行這項工作。  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>以非同步方式呼叫服務  
 呼叫作業的方式完全取決於用戶端開發人員。 這是因為透過 Managed 程式碼來表達呼叫程序時，您可以將組成作業的訊息對應至同步或非同步的方法。 因此，如果要建置以非同步方式呼叫作業的用戶端，您可以透過 Svcutil.exe，使用 `/async` 選項來產生非同步用戶端程式碼。 如需詳細資訊，請參閱[如何：以非同步方式](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)呼叫服務作業。  
  
## <a name="calling-services-using-wcf-client-channels"></a>使用 WCF 用戶端通道呼叫服務  
 WCF 用戶端類型<xref:System.ServiceModel.ClientBase%601>會擴充, 其本身<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>會衍生自介面, 以公開基礎通道系統。 您可以搭配 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 類別使用目標服務合約來叫用服務。 如需詳細資訊, 請參閱[WCF 用戶端架構](../../../docs/framework/wcf/feature-details/client-architecture.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
