---
title: 比較 wcf 和 WCF 開發人員的 gRPC-gRPC
description: 用來建立分散式應用程式的 WCF 和 gRPC 架構比較。
ms.date: 12/15/2020
ms.openlocfilehash: 7dd41c3d6f248bb1ef5eacb323b1443c7bc575a7
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938490"
---
# <a name="comparing-wcf-to-grpc"></a>比較 WCF 與 gRPC

上一章讓您瞭解 Protobuf 以及 gRPC 如何處理訊息。 在您進行從 Windows Communication Foundation (WCF) 到 gRPC 的詳細轉換之前，請務必瞭解 WCF 中的可用功能如何在 gRPC 中處理，以及當沒有任何 gRPC 對等專案時可使用的因應措施。 具體來說，本章節將討論下列主題：

- 作業和方法
- 系結和傳輸
- RPC 類型
- 中繼資料
- 錯誤處理
- WS- \* 通訊協定

## <a name="grpc-example"></a>gRPC 範例

當您從 Visual Studio 2019 或命令列建立新的 ASP.NET Core 5.0 gRPC 專案時，系統會為您產生相當於 "Hello World" 的 gRPC。 它是由 `greeter.proto` 定義服務及其訊息的檔案，以及具有服務執行的檔案所組成 `GreeterService.cs` 。

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

本章節將說明 gRPC 的不同概念和功能時的範例程式碼。

>[!div class="step-by-step"]
>[上一個](protobuf-maps.md) 
>[下一步](wcf-endpoints-grpc-methods.md)
