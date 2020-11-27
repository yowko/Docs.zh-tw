---
title: 通訊端
description: 瞭解 .NET Framework Socket 類別，這是 Winsock32 API 所提供之通訊端服務的 managed 程式碼版本。
ms.date: 03/30/2017
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- Windows Sockets
- sockets, about sockets
- Socket class, about Socket class
- sockets
- requesting data from Internet, sockets
- network, sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
ms.openlocfilehash: e00d04164f7ce5251b7f30b5abd16c14643f6862
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263122"
---
# <a name="sockets"></a><span data-ttu-id="97805-103">通訊端</span><span class="sxs-lookup"><span data-stu-id="97805-103">Sockets</span></span>

<span data-ttu-id="97805-104"><xref:System.Net.Sockets> 命名空間包含 Windows Sockets 介面的 Managed 實作。</span><span class="sxs-lookup"><span data-stu-id="97805-104">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="97805-105"><xref:System.Net> 命名空間中的所有其他網路存取類別都建立在此通訊端實作之上。</span><span class="sxs-lookup"><span data-stu-id="97805-105">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="97805-106">.NET Framework <xref:System.Net.Sockets.Socket> 類別是 Winsock32 API 所提供的通訊端服務 Managed 程式碼版本。</span><span class="sxs-lookup"><span data-stu-id="97805-106">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="97805-107">在大部分情況下，**Socket** 類別方法，只會將資料封送處理成原生 Win32 相對物，並處理任何必要的安全性檢查。</span><span class="sxs-lookup"><span data-stu-id="97805-107">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="97805-108">**Socket** 類別支援兩種基本的模式，同步和非同步。</span><span class="sxs-lookup"><span data-stu-id="97805-108">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="97805-109">在同步模式中，呼叫執行網路作業的函式 (例如 <xref:System.Net.Sockets.Socket.Send%2A> 和 <xref:System.Net.Sockets.Socket.Receive%2A>) 會等候作業完成，然後才將控制權傳回給呼叫端程式。</span><span class="sxs-lookup"><span data-stu-id="97805-109">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="97805-110">在非同步模式中，這些呼叫會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="97805-110">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97805-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97805-111">See also</span></span>

- [<span data-ttu-id="97805-112">作法：建立通訊端</span><span class="sxs-lookup"><span data-stu-id="97805-112">How to: Create a Socket</span></span>](how-to-create-a-socket.md)

- [<span data-ttu-id="97805-113">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="97805-113">Using Application Protocols</span></span>](using-application-protocols.md)
