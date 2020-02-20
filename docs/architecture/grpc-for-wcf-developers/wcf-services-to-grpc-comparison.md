---
title: 針對 WCF 開發人員比較 WCF 與 gRPC-gRPC
description: 建立分散式應用程式的 WCF 和 gRPC 架構比較。
ms.date: 09/02/2019
ms.openlocfilehash: 4f54db76c9512b770b4dd993496d95437dd89753
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503341"
---
# <a name="comparing-wcf-to-grpc"></a>比較 WCF 與 gRPC

上一章可讓您瞭解 Protobuf 以及 gRPC 如何處理訊息。 在您進行從 Windows Communication Foundation （WCF）到 gRPC 的詳細轉換之前，請務必瞭解 WCF 中可用的功能在 gRPC 中的處理方式，以及當沒有 gRPC 對等的情況時，您可以使用的因應措施。 具體而言，本章將涵蓋下列主題：

- 作業和方法
- 系結和傳輸
- RPC 類型
- 中繼資料
- 錯誤處理
- WS-\* 通訊協定

## <a name="grpc-example"></a>gRPC 範例

當您從 Visual Studio 2019 或命令列建立新的 ASP.NET Core 3.0 gRPC 專案時，系統會為您產生 gRPC 對等的 "Hello World"。 其中包含定義服務和其訊息的 `greeter.proto` 檔案，以及含有服務執行的 `GreeterService.cs` 檔案。

```protobuf
syntax = "proto3";

option csharp_namespace = "HelloGrpc";

package Greet;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// The request message that contains the user's name.
message HelloRequest {
  string name = 1;
}

// The response message that contains the greetings.
message HelloReply {
  string message = 1;
}
```

```csharp
using System.Threading.Tasks;
using Grpc.Core;
using Microsoft.Extensions.Logging;

namespace HelloGrpc
{
    public class GreeterService : Greeter.GreeterBase
    {
        private readonly ILogger<GreeterService> _logger;
        public GreeterService(ILogger<GreeterService> logger)
        {
            _logger = logger;
        }

        public override Task<HelloReply> SayHello(HelloRequest request, ServerCallContext context)
        {
            return Task.FromResult(new HelloReply
            {
                Message = "Hello " + request.Name
            });
        }
    }
}
```

本章節會在說明 gRPC 的不同概念和功能時，參考此範例程式碼。

>[!div class="step-by-step"]
>[上一頁](protobuf-maps.md)
>[下一頁](wcf-endpoints-grpc-methods.md)
