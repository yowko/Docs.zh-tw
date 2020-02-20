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
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="ca16b-103">比較 WCF 與 gRPC</span><span class="sxs-lookup"><span data-stu-id="ca16b-103">Comparing WCF to gRPC</span></span>

<span data-ttu-id="ca16b-104">上一章可讓您瞭解 Protobuf 以及 gRPC 如何處理訊息。</span><span class="sxs-lookup"><span data-stu-id="ca16b-104">The previous chapter gave you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="ca16b-105">在您進行從 Windows Communication Foundation （WCF）到 gRPC 的詳細轉換之前，請務必瞭解 WCF 中可用的功能在 gRPC 中的處理方式，以及當沒有 gRPC 對等的情況時，您可以使用的因應措施。</span><span class="sxs-lookup"><span data-stu-id="ca16b-105">Before you work through a detailed conversion from Windows Communication Foundation (WCF) to gRPC, it's important know how the features available in WCF are handled in gRPC and what workarounds you can use when there's no gRPC equivalent.</span></span> <span data-ttu-id="ca16b-106">具體而言，本章將涵蓋下列主題：</span><span class="sxs-lookup"><span data-stu-id="ca16b-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="ca16b-107">作業和方法</span><span class="sxs-lookup"><span data-stu-id="ca16b-107">Operations and methods</span></span>
- <span data-ttu-id="ca16b-108">系結和傳輸</span><span class="sxs-lookup"><span data-stu-id="ca16b-108">Bindings and transports</span></span>
- <span data-ttu-id="ca16b-109">RPC 類型</span><span class="sxs-lookup"><span data-stu-id="ca16b-109">RPC types</span></span>
- <span data-ttu-id="ca16b-110">中繼資料</span><span class="sxs-lookup"><span data-stu-id="ca16b-110">Metadata</span></span>
- <span data-ttu-id="ca16b-111">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="ca16b-111">Error handling</span></span>
- <span data-ttu-id="ca16b-112">WS-\* 通訊協定</span><span class="sxs-lookup"><span data-stu-id="ca16b-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="ca16b-113">gRPC 範例</span><span class="sxs-lookup"><span data-stu-id="ca16b-113">gRPC example</span></span>

<span data-ttu-id="ca16b-114">當您從 Visual Studio 2019 或命令列建立新的 ASP.NET Core 3.0 gRPC 專案時，系統會為您產生 gRPC 對等的 "Hello World"。</span><span class="sxs-lookup"><span data-stu-id="ca16b-114">When you create a new ASP.NET Core 3.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="ca16b-115">其中包含定義服務和其訊息的 `greeter.proto` 檔案，以及含有服務執行的 `GreeterService.cs` 檔案。</span><span class="sxs-lookup"><span data-stu-id="ca16b-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

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

<span data-ttu-id="ca16b-116">本章節會在說明 gRPC 的不同概念和功能時，參考此範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="ca16b-116">This chapter will refer to this example code when explaining different concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ca16b-117">[上一頁](protobuf-maps.md)
>[下一頁](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="ca16b-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
