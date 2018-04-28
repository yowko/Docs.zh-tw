---
title: WCF 用戶端概觀
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b0042d9b90066553d6fc962bba1b7a7b990ca242
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="wcf-client-overview"></a>WCF 用戶端概觀
本節描述用戶端應用程式的功能、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 用戶端的設定、建立和使用方式，以及保護用戶端應用程式安全的方法。  
  
## <a name="using-wcf-client-objects"></a>使用 WCF 用戶端物件  
 用戶端應用程式是使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端與其他應用程式進行通訊的一種 Managed 應用程式。 建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務的用戶端應用程式時，需要執行下列步驟：  
  
1.  取得服務端點的服務合約、繫結和位址資訊。  
  
2.  使用這些資訊建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端。  
  
3.  呼叫作業。  
  
4.  關閉 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件。  
  
 下列各節將討論這些步驟，並簡要介紹以下問題：  
  
-   處理錯誤。  
  
-   設定和保護用戶端。  
  
-   建立雙工服務的回呼物件。  
  
-   非同步呼叫服務。  
  
-   透過用戶端通道呼叫服務。  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>取得服務合約、繫結和位址  
 在 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 中，服務和用戶端模型合約會使用 Managed 屬性、介面和方法。 若要在用戶端應用程式中連接到服務，您必須取得服務合約的類型資訊。 一般而言，您可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)，從服務下載中繼資料會將它轉換成在您選擇的語言中的 managed 的原始程式碼檔，並建立用戶端應用程式組態檔可讓您設定您[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]用戶端物件。 例如，如果您要建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件來叫用 `MyCalculatorService`，並且知道這個服務的中繼資料的發行位置是在 `http://computerName/MyCalculatorService/Service.svc?wsdl`，那麼下列程式碼範例將會告訴您如何使用 Svcutil.exe 來取得 `ClientCode.vb` 檔案，該檔案包含以 Managed 程式碼撰寫的服務合約。  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 您可以將這段合約程式碼編譯成用戶端應用程式，或編譯成用戶端應用程式能用來建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件的另一個組件。 您可以使用組態檔來設定用戶端物件，以便正確連接到服務。  
  
 如需此程序的範例，請參閱[How to： 建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。 如需完整合約的詳細資訊，請參閱[合約](../../../docs/framework/wcf/feature-details/contracts.md)。  
  
## <a name="create-a-wcf-client-object"></a>建立 WCF 用戶端物件  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端為本機物件，這個物件是以用戶端可用來和遠端服務通訊的形式來表示 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端類型會實作目標服務合約，所以當您建立並設定服務合約時，就可以直接使用用戶端物件來叫用服務作業。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]執行階段會將為方法呼叫訊息、 將它們傳送至服務，接聽回覆，並傳回這些值到[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]作為傳回值的用戶端物件或`out`或`ref`參數。  
  
 您也可以使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端通道物件來連接及使用服務。 如需詳細資訊，請參閱[WCF 用戶端架構](../../../docs/framework/wcf/feature-details/client-architecture.md)。  
  
#### <a name="creating-a-new-wcf-object"></a>建立新的 WCF 物件  
 為說明 <xref:System.ServiceModel.ClientBase%601> 類別的使用方式，請假設已從服務應用程式產生下列簡單服務合約。  
  
> [!NOTE]
>  如果您使用 Visual Studio 來建立您[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]用戶端，會自動將物件載入物件瀏覽器時加入服務參考加入專案。  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 如果您不使用 Visual Studio，請檢查產生的合約程式碼，以尋找擴充的型別<xref:System.ServiceModel.ClientBase%601>和服務合約介面`ISampleService`。 在這種情況下，該型別看起來類似下列程式碼：  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 您可以將這個類別建立成本機物件，其方式是使用其中一個建構函式，然後加以設定，再用來連接到型別為 `ISampleService` 的服務。  
  
 建議您先建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件，然後在單一的 try/catch 區塊內使用並關閉它。 您不應該使用`using`陳述式 (`Using`在 Visual Basic 中) 因為這可能會遮罩中特定失敗模式的例外狀況。 如需詳細資訊，請參閱下列各節以及[避免 Using 陳述式的問題](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)。  
  
### <a name="contracts-bindings-and-addresses"></a>合約、繫結和位址  
 您必須先設定用戶端物件，才可以建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件。 具體來說，它必須有服務*端點*使用。 端點是服務合約、繫結和位址的組合  ([!INCLUDE[crabout](../../../includes/crabout-md.md)]端點，請參閱[端點： 位址、 繫結和合約](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)。)一般而言，這項資訊位於[\<端點 >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)中用戶端應用程式組態檔，例如，Svcutil.exe 工具產生的而且當您建立您的用戶端時自動載入的項目物件。 這兩個 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端型別也有多載，可讓您以程式設計方式來指定這項資訊。  
  
 例如，針對前面範例中使用的 `ISampleService` 所產生的組態檔會包含下列端點資訊。  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 這個組態檔會在 `<client>` 元素中指定目標端點。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]使用多個目標端點的詳細資訊，請參閱 <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> 建構函式。  
  
## <a name="calling-operations"></a>呼叫作業  
 建立並設定用戶端物件之後，請建立 try/catch 區塊，然後就當做物件是在本機一般來呼叫作業，再關閉 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件。 當用戶端應用程式呼叫第一項作業時，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 會自動開啟基礎通道，而當物件遭回收時，則會關閉基礎通道  (或者，您也可以在呼叫其他作業之前或之後明確地開啟和關閉通道)。  
  
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
  
 就可以建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件並呼叫其方法來呼叫作業，如下列程式碼範例所示。 請注意，開啟、呼叫和關閉 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件的動作都是在單一的 try/catch 區塊中進行。 如需詳細資訊，請參閱[使用 WCF 用戶端存取服務](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)和[避免 Using 陳述式的問題](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)。  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>處理錯誤  
 當開啟基礎用戶端通道 (無論是明確或是自動呼叫作業)、使用用戶端或通道物件來呼叫作業，或關閉基礎用戶端通道時，都可能會在用戶端應用程式中發生例外狀況。 除了要由作業傳回因 SOAP 錯誤而擲回的任何 <xref:System.TimeoutException?displayProperty=nameWithType> 物件之外，建議您最少還要讓應用程式有能力處理可能發生的 <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> 和 <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> 例外狀況。 作業合約中指定的 SOAP 錯誤會針對用戶端應用程式引發為 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>，其中的類型參數是 SOAP 錯誤的詳細類型。 [!INCLUDE[crabout](../../../includes/crabout-md.md)] 處理用戶端應用程式中的錯誤狀況，請參閱[傳送和接收錯誤](../../../docs/framework/wcf/sending-and-receiving-faults.md)。 如需完整範例將示範如何在用戶端中處理錯誤，請參閱[預期的例外狀況](../../../docs/framework/wcf/samples/expected-exceptions.md)。  
  
## <a name="configuring-and-securing-clients"></a>設定和保護用戶端  
 設定用戶端時，通常是先從組態檔載入用戶端或通道物件的必要目標端點資訊；儘管可以透過用戶端建構函式和屬性，使用程式設計方式載入這項資訊， 但是為了啟用特定用戶端行為，並符合許多安全性案例的需要，您應該另外執行其他必要的設定步驟。  
  
 例如，服務合約的安全性需求會在服務合約介面中宣告；如果 Svcutil.exe 建立了組態檔，這個檔案通常應包含能夠支援服務安全性需求的繫結。 不過，在某些情況下，可能需要進行更多的安全性設定，例如設定用戶端認證。 如需安全性組態的完整資訊[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]用戶端，請參閱[保護用戶端](../../../docs/framework/wcf/securing-clients.md)。  
  
 此外，還可以在用戶端應用程式中啟用某些自訂修改，例如自訂執行階段行為。 [!INCLUDE[crabout](../../../includes/crabout-md.md)] 如何設定自訂用戶端行為，請參閱[設定用戶端行為](../../../docs/framework/wcf/configuring-client-behaviors.md)。  
  
## <a name="creating-callback-objects-for-duplex-services"></a>建立雙工服務的回呼物件  
 雙工服務會指定回呼合約，這是用戶端應用程式為了在服務根據合約需求進行呼叫時提供其所需之回呼物件而必須實作的合約。 雖然回呼物件並非完整的服務 (例如，您無法透過回呼物件啟始通道)，但基於實作和組態設定的目的，不妨將它們視為一種服務。  
  
 雙工服務的用戶端必須：  
  
-   實作回呼合約類別。  
  
-   建立回呼合約實作類別的執行個體，然後使用它建立傳遞給 <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> 用戶端建構函式的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 物件。  
  
-   叫用作業和處理作業回呼。  
  
 雙工 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件的運作方式類似其非雙工的對應物件，但不同之處在於前者會公開支援回呼所需的功能，包括回呼服務的組態。  
  
 例如，您可以在回呼類別上使用 <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> 屬性 (Attribute) 的屬性 (Property)，控制回呼物件執行階段行為的各種層面。 此外，還可以使用 <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> 類別，讓例外狀況資訊回傳給呼叫回呼物件的服務。 如需詳細資訊，請參閱[雙工服務](../../../docs/framework/wcf/feature-details/duplex-services.md)。 如需完整範例，請參閱[雙工](../../../docs/framework/wcf/samples/duplex.md)。  
  
 在執行 Internet Information Services (IIS) 5.1 的 Windows XP 電腦上，雙工用戶端必須使用 <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> 類別來指定用戶端基底位址，否則會擲回例外狀況。 下列程式碼範例示範如何在程式碼中執行這項工作。  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 下列程式碼範例示範如何在組態檔中執行這項工作。  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>以非同步方式呼叫服務  
 呼叫作業的方式完全取決於用戶端開發人員。 這是因為透過 Managed 程式碼來表達呼叫程序時，您可以將組成作業的訊息對應至同步或非同步的方法。 因此，如果要建置以非同步方式呼叫作業的用戶端，您可以透過 Svcutil.exe，使用 `/async` 選項來產生非同步用戶端程式碼。 如需詳細資訊，請參閱[如何： 非同步呼叫服務作業](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)。  
  
## <a name="calling-services-using-wcf-client-channels"></a>使用 WCF 用戶端通道呼叫服務  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端型別會擴充 <xref:System.ServiceModel.ClientBase%601>，而後者則是從 <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> 介面衍生以公開基礎通道系統。 您可以搭配 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 類別使用目標服務合約來叫用服務。 如需詳細資訊，請參閱[WCF 用戶端架構](../../../docs/framework/wcf/feature-details/client-architecture.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
