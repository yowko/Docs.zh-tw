---
title: Wcf 端點和 gRPC 方法-適用于 WCF 開發人員的 gRPC
description: 比較以 ServiceContract 和 OperationContract 屬性宣告的 WCF 端點，以及 Protobuf 中宣告的 gRPC 方法
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 08f2d0874417c0ca319b0c193e6108536376d693
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184061"
---
# <a name="wcf-endpoints-and-grpc-methods"></a>WCF 端點和 gRPC 方法

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在 WCF 中，當您撰寫應用程式程式碼時，您可以使用下列其中一種方法：

- 您在類別中撰寫應用程式程式碼，並使用[OperationContract](xref:System.ServiceModel.OperationContractAttribute)屬性來裝飾方法。
- 您可以宣告服務的介面，並將[OperationContract](xref:System.ServiceModel.OperationContractAttribute)屬性新增至介面。

例如， `greet.proto` Greeter 服務的 WCF 對等項可能會寫入如下：

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

第3章顯示使用 Protobuf 訊息定義來產生資料類別。 服務和方法宣告是用來產生繼承自的基類，以執行服務。 您只要宣告要在檔案中`.proto`執行的方法，編譯器就會產生具有您必須覆寫之虛擬方法的基類。

## <a name="operationcontract-properties"></a>OperationContract 屬性

[OperationContract](xref:System.ServiceModel.OperationContractAttribute)屬性具有屬性，可控制或精簡其運作方式。 gRPC 方法不提供這種類型的控制項。 下表會設定這些`OperationContract`屬性，以及它們所指定的功能在 gRPC 中的處理方式（或不會）：

| `OperationContract` 屬性 | gRPC                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | 識別作業的 URI。 gRPC 會使用的`package`名稱， `service`以及`rpc`檔案中`.proto`的。 |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | 所有 gRPC 服務方法`Task`都會傳回物件。 |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | 請參閱下列注意事項。 |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | 單向 gRPC 方法`Empty`會傳回結果，或使用用戶端串流。 |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | 請參閱下列注意事項。 |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | SOAP 相關，在 gRPC 中沒有意義。 |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | 無訊息加密;在傳輸層處理的網路加密（TLS over HTTP/2）。 |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | SOAP 相關，在 gRPC 中沒有意義。 |

屬性可讓您指出 [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) 中的方法不能是第一個呼叫作為會話一部分的方法。`IsInitiating` `IsTerminating`屬性會在呼叫作業之後，讓伺服器關閉會話（如果是在回呼用戶端上使用，則會導致用戶端）。 在 gRPC 中，資料流程是由單一方法建立，並且明確地關閉。 請參閱[gRPC 串流](rpc-types.md#grpc-streaming)。

如需有關 gRPC 安全性和加密的詳細資訊，請參閱[第6章](security.md)。

>[!div class="step-by-step"]
>[上一頁](wcf-services-to-grpc-comparison.md)
>[下一頁](wcf-bindings.md)
