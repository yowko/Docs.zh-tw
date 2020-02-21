---
title: 介面定義語言-適用于 WCF 開發人員的 gRPC
description: 介紹通訊協定緩衝區 IDL。
ms.date: 09/02/2019
ms.openlocfilehash: 841f041ae350e76e648c71f9d6d113b9d39e0d3b
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543205"
---
# <a name="interface-definition-language"></a><span data-ttu-id="7b8a0-103">介面定義語言</span><span class="sxs-lookup"><span data-stu-id="7b8a0-103">Interface Definition Language</span></span>

<span data-ttu-id="7b8a0-104">使用 Windows Communication Foundation （WCF），服務可以使用 Web 服務定義語言（WSDL）公開描述中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-104">With Windows Communication Foundation (WCF), services can expose description metadata by using the Web Service Definition Language (WSDL).</span></span> <span data-ttu-id="7b8a0-105">WSDL 是在執行時間使用 .NET 反映動態產生的。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-105">WSDL is generated dynamically by using .NET reflection at runtime.</span></span> <span data-ttu-id="7b8a0-106">開發人員可以使用此中繼資料來產生這些服務的用戶端，如果它們使用的是平臺中立的系結，例如 SOAP over HTTP，則可能是其他語言。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-106">Developers can use this metadata to generate clients for those services, potentially in other languages if they're using a platform-neutral binding such as SOAP over HTTP.</span></span>

<span data-ttu-id="7b8a0-107">gRPC 會使用來自通訊協定緩衝區的介面定義語言（IDL）。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-107">gRPC uses the Interface Definition Language (IDL) from Protocol Buffers.</span></span> <span data-ttu-id="7b8a0-108">通訊協定緩衝區 IDL 是一種自訂的平臺中立語言，具有開放式規格。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-108">The Protocol Buffers IDL is a custom, platform-neutral language with an open specification.</span></span> <span data-ttu-id="7b8a0-109">開發人員會撰寫 `.proto` 檔案，以描述服務及其輸入和輸出。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-109">Developers author `.proto` files to describe services, along with their inputs and outputs.</span></span> <span data-ttu-id="7b8a0-110">這些 `.proto` 的檔案可以用來為用戶端和伺服器產生語言或平臺特定的存根，讓多個不同的平臺能夠進行通訊。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-110">These `.proto` files can then be used to generate language- or platform-specific stubs for clients and servers, allowing multiple different platforms to communicate.</span></span> <span data-ttu-id="7b8a0-111">藉由共用 `.proto` 檔案，小組可以產生程式碼，以使用每個其他服務，而不需要採取程式碼相依性。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-111">By sharing `.proto` files, teams can generate code to use each others' services, without needing to take a code dependency.</span></span>

<span data-ttu-id="7b8a0-112">Protobuf IDL 的其中一個優點是，身為自訂語言，它可讓 gRPC 完全不受語言和平臺限制，而不是優先列出其他技術。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-112">One of the advantages of the Protobuf IDL is that as a custom language, it enables gRPC to be completely language and platform agnostic, not favoring any technology over another.</span></span>

<span data-ttu-id="7b8a0-113">Protobuf IDL 也是專為讀取和寫入而設計，而 WSDL 則是做為電腦可讀取/可寫入的格式。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-113">The Protobuf IDL is also designed for humans to both read and write, whereas WSDL is intended as a machine-readable/writable format.</span></span> <span data-ttu-id="7b8a0-114">變更 WCF 服務的 WSDL 通常需要變更服務、執行服務，以及從伺服器重新產生 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-114">Changing the WSDL of a WCF service typically requires changing the service, running the service and regenerating the WSDL file from the server.</span></span> <span data-ttu-id="7b8a0-115">相較之下，使用 `.proto` 檔案時，變更很容易與文字編輯器一起套用，而且會自動流經產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-115">By contrast, with a `.proto` file, changes are simple to apply with a text editor, and automatically flow through the generated code.</span></span> <span data-ttu-id="7b8a0-116">Visual Studio 2019 會在儲存檔案時，于背景建立 `.proto` 檔案。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-116">Visual Studio 2019 builds `.proto` files in the background when they are saved.</span></span> <span data-ttu-id="7b8a0-117">使用其他編輯器（例如 VS Code）時，會在建立專案時套用變更。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-117">With other editors, such as VS Code, the changes are applied when the project is built.</span></span>

<span data-ttu-id="7b8a0-118">相較于 XML，特別是 SOAP，使用 Protobuf 編碼的訊息有許多優點。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-118">When compared with XML, and particularly SOAP, messages encoded by using Protobuf have many advantages.</span></span> <span data-ttu-id="7b8a0-119">Protobuf 訊息通常會小於序列化為 SOAP XML 的相同資料，而且透過網路進行編碼、解碼和傳輸可能會更快。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-119">Protobuf messages tend to be smaller than the same data serialized as SOAP XML, and encoding, decoding, and transmitting them over a network can be faster.</span></span>

<span data-ttu-id="7b8a0-120">相較于 SOAP，Protobuf 的可能缺點是，因為人類無法讀取訊息，所以需要額外的工具才能進行訊息內容的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-120">The potential disadvantage of Protobuf compared to SOAP is that, because the messages aren't readable by humans, additional tooling is required to debug message content.</span></span>

> [!TIP]
> <span data-ttu-id="7b8a0-121">gRPC*確實*支援伺服器反映，以在沒有預先編譯的存根的情況下動態存取服務，但它比應用程式特定的用戶端更適用于一般用途的工具。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-121">gRPC *does* support server reflection for dynamically accessing services without pre-compiled stubs, although it's intended more for general-purpose tools than application-specific clients.</span></span> <span data-ttu-id="7b8a0-122">如需詳細資訊，請參閱 GitHub 上的[GRPC 伺服器反映通訊協定](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-122">For more information, see [GRPC Server Reflection Protocol](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) on GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="7b8a0-123">與 NetTCP 系結搭配使用的 WCF 二進位格式，遠接近 Protobuf 的簡潔性和效能方面。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-123">WCF's binary format, used with the NetTCP binding, is much closer to Protobuf in terms of compactness and performance.</span></span> <span data-ttu-id="7b8a0-124">但是 NetTCP 只能在 .NET 用戶端和伺服器之間使用，而 Protobuf 則是跨平臺的解決方案。</span><span class="sxs-lookup"><span data-stu-id="7b8a0-124">But NetTCP is only usable between .NET clients and servers, whereas Protobuf is a cross-platform solution.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7b8a0-125">[上一頁](approach.md)
>[下一頁](network-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="7b8a0-125">[Previous](approach.md)
[Next](network-protocols.md)</span></span>
