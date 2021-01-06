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
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="d5857-103">比較 WCF 與 gRPC</span><span class="sxs-lookup"><span data-stu-id="d5857-103">Comparing WCF to gRPC</span></span>

<span data-ttu-id="d5857-104">上一章讓您瞭解 Protobuf 以及 gRPC 如何處理訊息。</span><span class="sxs-lookup"><span data-stu-id="d5857-104">The previous chapter gave you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="d5857-105">在您進行從 Windows Communication Foundation (WCF) 到 gRPC 的詳細轉換之前，請務必瞭解 WCF 中的可用功能如何在 gRPC 中處理，以及當沒有任何 gRPC 對等專案時可使用的因應措施。</span><span class="sxs-lookup"><span data-stu-id="d5857-105">Before you work through a detailed conversion from Windows Communication Foundation (WCF) to gRPC, it's important know how the features available in WCF are handled in gRPC and what workarounds you can use when there's no gRPC equivalent.</span></span> <span data-ttu-id="d5857-106">具體來說，本章節將討論下列主題：</span><span class="sxs-lookup"><span data-stu-id="d5857-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="d5857-107">作業和方法</span><span class="sxs-lookup"><span data-stu-id="d5857-107">Operations and methods</span></span>
- <span data-ttu-id="d5857-108">系結和傳輸</span><span class="sxs-lookup"><span data-stu-id="d5857-108">Bindings and transports</span></span>
- <span data-ttu-id="d5857-109">RPC 類型</span><span class="sxs-lookup"><span data-stu-id="d5857-109">RPC types</span></span>
- <span data-ttu-id="d5857-110">中繼資料</span><span class="sxs-lookup"><span data-stu-id="d5857-110">Metadata</span></span>
- <span data-ttu-id="d5857-111">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="d5857-111">Error handling</span></span>
- <span data-ttu-id="d5857-112">WS- \* 通訊協定</span><span class="sxs-lookup"><span data-stu-id="d5857-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="d5857-113">gRPC 範例</span><span class="sxs-lookup"><span data-stu-id="d5857-113">gRPC example</span></span>

<span data-ttu-id="d5857-114">當您從 Visual Studio 2019 或命令列建立新的 ASP.NET Core 5.0 gRPC 專案時，系統會為您產生相當於 "Hello World" 的 gRPC。</span><span class="sxs-lookup"><span data-stu-id="d5857-114">When you create a new ASP.NET Core 5.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="d5857-115">它是由 `greeter.proto` 定義服務及其訊息的檔案，以及具有服務執行的檔案所組成 `GreeterService.cs` 。</span><span class="sxs-lookup"><span data-stu-id="d5857-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

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

<span data-ttu-id="d5857-116">本章節將說明 gRPC 的不同概念和功能時的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="d5857-116">This chapter will refer to this example code when explaining different concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d5857-117">[上一個](protobuf-maps.md) 
>[下一步](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="d5857-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
