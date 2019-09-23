---
title: GRPC 如何為 WCF 開發人員提供 RPC gRPC 的方法
description: 比較 WCF 與 gRPC 的主要功能。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 65d61c8246569d81dfec3aeb8e3df4bea26258dc
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184600"
---
# <a name="how-grpc-approaches-rpc"></a><span data-ttu-id="b67fe-103">GRPC 如何方法 RPC</span><span class="sxs-lookup"><span data-stu-id="b67fe-103">How gRPC approaches RPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="b67fe-104">Windows Communication Foundation （WCF）和 gRPC 兩者都是*遠端程序呼叫*（RPC）模式的執行，它的目的是要呼叫在不同電腦上執行的服務，或是在不同的進程中，順暢地像是用戶端應用程式中的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="b67fe-104">Windows Communication Foundation (WCF) and gRPC are both implementations of the *Remote Procedure Call* (RPC) pattern, which aims to make calls to services running on a different machine, or in a different process, seamlessly work as though they were just method calls in the client application.</span></span> <span data-ttu-id="b67fe-105">雖然 WCF 和 gRPC 的目標都相同，但執行的詳細資料也很不同。</span><span class="sxs-lookup"><span data-stu-id="b67fe-105">While the aims of WCF and gRPC are the same, the details of the implementation are quite different.</span></span>

<span data-ttu-id="b67fe-106">下表將說明 WCF 的主要功能與 gRPC 的關聯性，以及您可以在本書其餘部分找到更詳細的解釋。</span><span class="sxs-lookup"><span data-stu-id="b67fe-106">The following table sets out how the key features of WCF relate to gRPC and where you can find more detailed explanations in the rest of the book.</span></span>

| <span data-ttu-id="b67fe-107">功能</span><span class="sxs-lookup"><span data-stu-id="b67fe-107">Features</span></span> | <span data-ttu-id="b67fe-108">WCF</span><span class="sxs-lookup"><span data-stu-id="b67fe-108">WCF</span></span> | <span data-ttu-id="b67fe-109">gRPC</span><span class="sxs-lookup"><span data-stu-id="b67fe-109">gRPC</span></span> |
| -------- | --- | ---- |
| <span data-ttu-id="b67fe-110">目標</span><span class="sxs-lookup"><span data-stu-id="b67fe-110">Objective</span></span> | <span data-ttu-id="b67fe-111">將商務程式碼與網路功能執行分開</span><span class="sxs-lookup"><span data-stu-id="b67fe-111">Separate business code from networking implementation</span></span> | <span data-ttu-id="b67fe-112">將商務程式碼與介面定義和網路功能執行分開</span><span class="sxs-lookup"><span data-stu-id="b67fe-112">Separate business code from interface definition and networking implementation</span></span> |
| <span data-ttu-id="b67fe-113">定義服務和訊息（第3-4 章）</span><span class="sxs-lookup"><span data-stu-id="b67fe-113">Define Services and messages (chapter 3-4)</span></span>  | <span data-ttu-id="b67fe-114">服務合約、作業合約和資料合約</span><span class="sxs-lookup"><span data-stu-id="b67fe-114">Service Contract, Operation Contract, and Data Contract</span></span> | <span data-ttu-id="b67fe-115">使用 proto 檔案來宣告服務和訊息</span><span class="sxs-lookup"><span data-stu-id="b67fe-115">Uses proto file to declare services and messages</span></span> |
| <span data-ttu-id="b67fe-116">語言（第3-5 章）</span><span class="sxs-lookup"><span data-stu-id="b67fe-116">Language (chapter 3-5)</span></span> | <span data-ttu-id="b67fe-117">在或 Visual Basic C#中撰寫的合約</span><span class="sxs-lookup"><span data-stu-id="b67fe-117">Contracts written in C# or Visual Basic</span></span> | <span data-ttu-id="b67fe-118">通訊協定緩衝區語言</span><span class="sxs-lookup"><span data-stu-id="b67fe-118">Protocol Buffer language</span></span> |
| <span data-ttu-id="b67fe-119">電傳格式（第3章）</span><span class="sxs-lookup"><span data-stu-id="b67fe-119">Wire format (chapter 3)</span></span> | <span data-ttu-id="b67fe-120">可設定，包括 SOAP/XML、純 XML、JSON、.NET 二進位檔等等。</span><span class="sxs-lookup"><span data-stu-id="b67fe-120">Configurable, including SOAP/XML, Plain XML, JSON, .NET Binary, and so on.</span></span> | <span data-ttu-id="b67fe-121">通訊協定緩衝區二進位格式（雖然可以使用其他格式）。</span><span class="sxs-lookup"><span data-stu-id="b67fe-121">Protocol Buffer binary format (although it's possible to use other formats).</span></span>
| <span data-ttu-id="b67fe-122">互通性（第4章）</span><span class="sxs-lookup"><span data-stu-id="b67fe-122">Interoperability (chapter 4)</span></span> | <span data-ttu-id="b67fe-123">使用 SOAP over HTTP 時</span><span class="sxs-lookup"><span data-stu-id="b67fe-123">When using SOAP over HTTP</span></span> | <span data-ttu-id="b67fe-124">正式支援： .NET、JAVA、Python、JavaScript、C/C++、Go、Rust、Ruby、Swift、DART、PHP。</span><span class="sxs-lookup"><span data-stu-id="b67fe-124">Official support: .NET, Java, Python, JavaScript, C/C++, Go, Rust, Ruby, Swift, Dart, PHP.</span></span> <span data-ttu-id="b67fe-125">來自社區的其他語言非官方支援。</span><span class="sxs-lookup"><span data-stu-id="b67fe-125">Unofficial support for other languages from the community.</span></span> |
| <span data-ttu-id="b67fe-126">網路功能（第4章）</span><span class="sxs-lookup"><span data-stu-id="b67fe-126">Networking (chapter 4)</span></span> | <span data-ttu-id="b67fe-127">在執行時間設定。</span><span class="sxs-lookup"><span data-stu-id="b67fe-127">Configured at runtime.</span></span> <span data-ttu-id="b67fe-128">在 TCP、HTTP、MSMQ 等之間切換。</span><span class="sxs-lookup"><span data-stu-id="b67fe-128">Switch between TCP, HTTP, MSMQ, and so on.</span></span> | <span data-ttu-id="b67fe-129">一律為 HTTP/2</span><span class="sxs-lookup"><span data-stu-id="b67fe-129">Always HTTP/2</span></span> |
| <span data-ttu-id="b67fe-130">方法（第4章）</span><span class="sxs-lookup"><span data-stu-id="b67fe-130">Approach (chapter 4)</span></span> | <span data-ttu-id="b67fe-131">在基類中產生序列化/deserialization 和網路程式碼的執行時間</span><span class="sxs-lookup"><span data-stu-id="b67fe-131">Runtime generation of serialization /deserialization and networking code in base classes</span></span> | <span data-ttu-id="b67fe-132">基底類別中的組建階段產生序列化/deserialization 和網路程式碼</span><span class="sxs-lookup"><span data-stu-id="b67fe-132">Build-time generation of serialization /deserialization and networking code in base classes</span></span> |
| <span data-ttu-id="b67fe-133">安全性（第6章）</span><span class="sxs-lookup"><span data-stu-id="b67fe-133">Security (chapter 6)</span></span> | <span data-ttu-id="b67fe-134">驗證，WS-安全性，訊息加密</span><span class="sxs-lookup"><span data-stu-id="b67fe-134">Authentication, WS-Security, message encryption</span></span> | <span data-ttu-id="b67fe-135">認證，ASP.NET Core 安全性，TLS 網路</span><span class="sxs-lookup"><span data-stu-id="b67fe-135">Credentials, ASP.NET Core security, TLS networking</span></span> |

>[!div class="step-by-step"]
><span data-ttu-id="b67fe-136">[上一頁](grpc-overview.md)
>[下一頁](interface-definition-language.md)</span><span class="sxs-lookup"><span data-stu-id="b67fe-136">[Previous](grpc-overview.md)
[Next](interface-definition-language.md)</span></span>
