---
title: Wcf 端點和 gRPC 方法-適用于 WCF 開發人員的 gRPC
description: 比較以 ServiceContract 和 OperationContract 屬性宣告的 WCF 端點，以及 Protobuf 中宣告的 gRPC 方法
ms.date: 09/02/2019
ms.openlocfilehash: 1bc6ecbc73bfc0a58393e4c28672b897ed6f2f15
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503423"
---
# <a name="wcf-endpoints-and-grpc-methods"></a>WCF 端點和 gRPC 方法

在 Windows Communication Foundation （WCF）中，當您撰寫應用程式程式碼時，您可以使用下列其中一種方法：

- 您在類別中撰寫應用程式程式碼，並使用[OperationContract](xref:System.ServiceModel.OperationContractAttribute)屬性來裝飾方法。
- 您可以宣告服務的介面，並將[OperationContract](xref:System.ServiceModel.OperationContractAttribute)屬性新增至介面。

例如，`greet.proto` Greeter 服務的 WCF 對等項可能會寫入如下：

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

第3章顯示使用 Protobuf 訊息定義來產生資料類別。 服務和方法宣告是用來產生繼承自的基類，以執行服務。 您只要宣告要在 `.proto` 檔案中執行的方法，編譯器就會產生具有您必須覆寫之虛擬方法的基類。

## <a name="operationcontract-properties"></a>OperationContract 屬性

[OperationContract](xref:System.ServiceModel.OperationContractAttribute)屬性具有屬性，可控制或精簡其運作方式。 gRPC 方法不提供這種類型的控制項。 下表列出這些 `OperationContract` 屬性，並說明在 gRPC 中，它們所指定的功能是（或未）處理：

| `OperationContract` 屬性 | gRPC                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | URI 可識別作業。 gRPC 會使用 `.proto` 檔案中 `package`、`service`和 `rpc` 的名稱。 |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | 所有的 gRPC 服務方法都會傳回 `Task` 物件。 |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | 請參閱此表格後面的段落。 |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | 單向 gRPC 方法會傳回 `Empty` 結果，或使用用戶端串流。 |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | 請參閱此表格後面的段落。 |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | 這個屬性與 SOAP 相關，在 gRPC 中沒有意義。 |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | 沒有訊息加密。 網路加密會在傳輸層處理（TLS over HTTP/2）。 |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | 這個屬性與 SOAP 相關，在 gRPC 中沒有意義。 |

`IsInitiating` 屬性可讓您指出[ServiceContract](xref:System.ServiceModel.ServiceContractAttribute)中的方法不能是第一個呼叫作為會話一部分的方法。 在呼叫作業之後，`IsTerminating` 屬性會導致伺服器關閉會話（如果在回呼用戶端上使用此屬性，則為用戶端）。 在 gRPC 中，資料流程是由單一方法建立，並且明確地關閉。 請參閱[gRPC 串流](rpc-types.md#grpc-streaming)。

如需有關 gRPC 安全性和加密的詳細資訊，請參閱[第6章](security.md)。

>[!div class="step-by-step"]
>[上一頁](wcf-services-to-grpc-comparison.md)
>[下一頁](wcf-bindings.md)
