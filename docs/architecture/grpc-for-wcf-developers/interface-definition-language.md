---
title: 介面定義語言-適用于 WCF 開發人員的 gRPC
description: 介紹通訊協定緩衝區 IDL。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 71bdf8bf488e0a5bed177817343051bcd7847d25
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184425"
---
# <a name="interface-definition-language"></a><span data-ttu-id="bf220-103">介面定義語言</span><span class="sxs-lookup"><span data-stu-id="bf220-103">Interface Definition Language</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="bf220-104">使用 WCF 時，服務可以使用 Web 服務定義語言（WSDL）公開描述中繼資料，這是在執行時間使用 .NET 反映動態產生的。</span><span class="sxs-lookup"><span data-stu-id="bf220-104">With WCF, services can expose description metadata using the Web Service Definition Language (WSDL), which is generated dynamically using .NET Reflection at runtime.</span></span> <span data-ttu-id="bf220-105">開發人員可以使用此中繼資料來產生這些服務的用戶端，如果使用以平臺中立的系結（例如 SOAP over HTTP），則可能是其他語言。</span><span class="sxs-lookup"><span data-stu-id="bf220-105">Developers can use this metadata to generate clients for those services, potentially in other languages if a platform-neutral binding such as SOAP over HTTP is used.</span></span>

<span data-ttu-id="bf220-106">gRPC 會使用來自通訊協定緩衝區的介面定義語言（IDL）。</span><span class="sxs-lookup"><span data-stu-id="bf220-106">gRPC uses the Interface Definition Language (IDL) from Protocol Buffers.</span></span> <span data-ttu-id="bf220-107">通訊協定緩衝區 IDL 是一種自訂的平臺中立語言，具有開放式規格。</span><span class="sxs-lookup"><span data-stu-id="bf220-107">The Protocol Buffers IDL is a custom, platform-neutral language with an open specification.</span></span> <span data-ttu-id="bf220-108">開發人員會撰寫`.proto`程式碼檔案，以描述服務及其輸入和輸出。</span><span class="sxs-lookup"><span data-stu-id="bf220-108">Developers hand-code `.proto` files to describe services along with their inputs and outputs.</span></span> <span data-ttu-id="bf220-109">然後`.proto` ，這些檔案可以用來為用戶端和伺服器產生語言或平臺特定的存根，讓多個不同的平臺能夠進行通訊。</span><span class="sxs-lookup"><span data-stu-id="bf220-109">These `.proto` files can then be used to generate language- or platform-specific stubs for clients and servers, allowing multiple different platforms to communicate.</span></span> <span data-ttu-id="bf220-110">藉由`.proto`共用檔案，小組可以產生程式碼以使用彼此的服務，而不需要採取程式碼相依性。</span><span class="sxs-lookup"><span data-stu-id="bf220-110">By sharing `.proto` files, teams can generate code to use each others' services without needing to take a code dependency.</span></span>

<span data-ttu-id="bf220-111">Protobuf IDL 的其中一個優點是，身為自訂語言，其可讓 gRPC 完全不受語言和平臺限制，而不是優先列出其他技術。</span><span class="sxs-lookup"><span data-stu-id="bf220-111">One of the advantages of the Protobuf IDL is that as a custom language it enables gRPC to be completely language and platform agnostic, not favoring any technology over another.</span></span>

<span data-ttu-id="bf220-112">Protobuf IDL 也是專為讀取和寫入而設計，而 WSDL 則是做為電腦可讀取/可寫入的格式。</span><span class="sxs-lookup"><span data-stu-id="bf220-112">The Protobuf IDL is also designed for humans to both read and write, whereas WSDL is intended as a machine-readable/writable format.</span></span> <span data-ttu-id="bf220-113">變更 WCF 服務的 WSDL 通常需要對服務程式代碼本身進行變更、執行服務，以及從伺服器重新產生 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="bf220-113">Changing the WSDL of a WCF service typically requires making the changes to the service code itself, running the service and regenerating the WSDL file from the server.</span></span> <span data-ttu-id="bf220-114">相較之下，使用`.proto`檔案時，您可以輕鬆地使用文字編輯器來套用變更，並自動流經產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf220-114">By contrast, with a `.proto` file, changes are simple to apply with a text editor, and automatically flow through the generated code.</span></span> <span data-ttu-id="bf220-115">Visual Studio 2019 會`.proto`在儲存檔案時于背景建立檔案; 使用其他編輯器（例如 VS Code）時，將會在建立專案時套用變更。</span><span class="sxs-lookup"><span data-stu-id="bf220-115">Visual Studio 2019 builds `.proto` files in the background when they are saved; when using other editors such as VS Code the changes will be applied when the project is built.</span></span>

<span data-ttu-id="bf220-116">相較于 XML，特別是 SOAP，使用 Protobuf 編碼的訊息有許多優點。</span><span class="sxs-lookup"><span data-stu-id="bf220-116">When compared with XML, and particularly SOAP, messages encoded using Protobuf have many advantages.</span></span> <span data-ttu-id="bf220-117">Protobuf 訊息通常會小於序列化為 SOAP XML 的相同資料，而透過網路進行編碼、解碼和傳輸可能會更快。</span><span class="sxs-lookup"><span data-stu-id="bf220-117">Protobuf messages tend to be smaller than the same data serialized as SOAP XML, and encoding, decoding and transmitting them over a network can be faster.</span></span>

<span data-ttu-id="bf220-118">相較于 SOAP，Protobuf 的可能缺點是，由於訊息不是人類可讀的，因此需要額外的工具來進行訊息內容的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bf220-118">The potential disadvantage of Protobuf compared to SOAP is that, because the messages are not human readable, additional tooling is required to debug message content.</span></span>

> [!TIP]
> <span data-ttu-id="bf220-119">gRPC*不*支援伺服器反映來動態存取服務，而不需要預先編譯的存根，雖然它比應用程式特定的用戶端更適用于一般用途的工具。</span><span class="sxs-lookup"><span data-stu-id="bf220-119">gRPC *does* support server reflection for dynamically accessing services without pre-compiled stubs, although it is intended more for general-purpose tools than application-specific clients.</span></span> <span data-ttu-id="bf220-120">如需 gRPC 伺服器反映的詳細資訊，請參閱 GitHub 上的[gRPC/gRPC](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md)儲存機制。</span><span class="sxs-lookup"><span data-stu-id="bf220-120">For more information about gRPC Server Reflection, see [grpc/grpc](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) repository on GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="bf220-121">與 NetTCP 系結搭配使用的 WCF 二進位格式，比簡潔性和效能更接近 Protobuf，但是 NetTCP 只能在 .NET 用戶端和伺服器之間使用，而 Protobuf 則是跨平臺的解決方案。</span><span class="sxs-lookup"><span data-stu-id="bf220-121">WCF's binary format, used with the NetTCP binding, is much closer to Protobuf in terms of compactness and performance, but NetTCP is only usable between .NET clients and servers, whereas Protobuf is a cross-platform solution.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bf220-122">[上一頁](approach.md)
>[下一頁](network-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="bf220-122">[Previous](approach.md)
[Next](network-protocols.md)</span></span>
