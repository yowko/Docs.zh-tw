---
title: "通訊端程式碼範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- Socket class, asynchronous server sockets
- data requests, sockets
- requesting data from Internet, sockets
- server sockets
- sockets, code examples
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: f3fc7533-6956-42c6-bbc3-73e5a221027d
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ac2363ce7c2affcc0b56f7ce8b9d41180b4c3a1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="socket-code-examples"></a><span data-ttu-id="a6db1-102">通訊端程式碼範例</span><span class="sxs-lookup"><span data-stu-id="a6db1-102">Socket Code Examples</span></span>
<span data-ttu-id="a6db1-103">下列程式碼範例示範如何使用 <xref:System.Net.Sockets.Socket> 類別作為用戶端連接到遠端網路服務，以及作為伺服器接聽來自遠端用戶端的連線。</span><span class="sxs-lookup"><span data-stu-id="a6db1-103">The following code examples demonstrate how to use the <xref:System.Net.Sockets.Socket> class as a client to connect to remote network services and as a server to listen for connections from remote clients.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6db1-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="a6db1-104">In This Section</span></span>  
 [<span data-ttu-id="a6db1-105">同步用戶端通訊端範例</span><span class="sxs-lookup"><span data-stu-id="a6db1-105">Synchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-client-socket-example.md)  
 <span data-ttu-id="a6db1-106">示範如何實作同步的 <xref:System.Net.Sockets.Socket> 用戶端，連接到伺服器，並顯示從伺服器傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="a6db1-106">Shows how to implement a synchronous <xref:System.Net.Sockets.Socket> client that connects to a server and displays the data returned from the server.</span></span>  
  
 [<span data-ttu-id="a6db1-107">同步伺服器通訊端範例</span><span class="sxs-lookup"><span data-stu-id="a6db1-107">Synchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-server-socket-example.md)  
 <span data-ttu-id="a6db1-108">示範如何實作同步的 <xref:System.Net.Sockets.Socket> 伺服器，接受來自用戶端的連線，並回應從用戶端收到的資料。</span><span class="sxs-lookup"><span data-stu-id="a6db1-108">Shows how to implement a synchronous <xref:System.Net.Sockets.Socket> server that accepts connections from a client and echoes back the data received from the client.</span></span>  
  
 [<span data-ttu-id="a6db1-109">非同步用戶端通訊端範例</span><span class="sxs-lookup"><span data-stu-id="a6db1-109">Asynchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)  
 <span data-ttu-id="a6db1-110">示範如何實作非同步的 <xref:System.Net.Sockets.Socket> 用戶端，連接到伺服器，並顯示從伺服器傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="a6db1-110">Shows how to implement an asynchronous <xref:System.Net.Sockets.Socket> client that connects to a server and displays the data returned from the server.</span></span>  
  
 [<span data-ttu-id="a6db1-111">非同步伺服器通訊端範例</span><span class="sxs-lookup"><span data-stu-id="a6db1-111">Asynchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)  
 <span data-ttu-id="a6db1-112">示範如何實作非同步的 <xref:System.Net.Sockets.Socket> 伺服器，接受來自用戶端的連線，並回應從用戶端收到的資料。</span><span class="sxs-lookup"><span data-stu-id="a6db1-112">Shows how to implement an asynchronous <xref:System.Net.Sockets.Socket> server that accepts connections from a client and echoes back the data received from the client.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a6db1-113">相關章節</span><span class="sxs-lookup"><span data-stu-id="a6db1-113">Related Sections</span></span>  
 [<span data-ttu-id="a6db1-114">通訊端</span><span class="sxs-lookup"><span data-stu-id="a6db1-114">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)  
 <span data-ttu-id="a6db1-115">提供有關 <xref:System.Net.Sockets> 命名空間和 <xref:System.Net.Sockets.Socket> 類別的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="a6db1-115">Provides basic information about the <xref:System.Net.Sockets> namespace and the <xref:System.Net.Sockets.Socket> class.</span></span>  
  
 [<span data-ttu-id="a6db1-116">網路程式設計的安全性</span><span class="sxs-lookup"><span data-stu-id="a6db1-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)  
 <span data-ttu-id="a6db1-117">描述如何使用標準網際網路安全性和驗證技術。</span><span class="sxs-lookup"><span data-stu-id="a6db1-117">Describes how to use standard Internet security and authentication techniques.</span></span>
