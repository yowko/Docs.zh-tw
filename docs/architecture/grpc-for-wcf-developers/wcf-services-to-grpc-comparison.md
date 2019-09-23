---
title: 針對 WCF 開發人員比較 WCF 與 gRPC-gRPC
description: 建立分散式應用程式的 WCF 和 gRPC 架構比較。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: c763048d09e7ed5ca0a3d5240f6b3cf5262f897c
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184040"
---
# <a name="comparing-wcf-to-grpc"></a>比較 WCF 與 gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

上一章應該讓您瞭解 Protobuf 以及 gRPC 如何處理訊息。 在進行從 WCF 到 gRPC 的詳細轉換之前，請務必查看 WCF 中目前可用的功能範圍如何在 gRPC 中處理，以及當沒有 gRPC 對等的情況時，您可以使用的因應措施。 具體而言，本章將涵蓋下列主題：

- 作業和方法
- 系結和傳輸
- RPC 類型
- 中繼資料
- 錯誤處理
- WS-\*通訊協定

## <a name="grpc-example"></a>gRPC 範例

當您從 Visual Studio 2019 或命令列建立新的 ASP.NET Core 3.0 gRPC 專案時，系統會為您產生 gRPC 對等的 "Hello World"。 其中包含`greeter.proto`定義服務及其訊息的檔案， `GreeterService.cs`以及具有服務執行的檔案。

```protobuf
syntax = "proto3";

option csharp_namespace = "HelloGrpc";

package Greet;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings.
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

本章節會在說明 gRPC 的各種概念和功能時，參考此範例程式碼。

>[!div class="step-by-step"]
>[上一頁](protobuf-maps.md)
>[下一頁](wcf-endpoints-grpc-methods.md)
