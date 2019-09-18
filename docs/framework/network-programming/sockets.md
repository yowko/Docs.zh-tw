---
title: 通訊端
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
ms.openlocfilehash: cffad6b4677a880bd63f5ae0232c639f7a262c59
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047248"
---
# <a name="sockets"></a>通訊端
<xref:System.Net.Sockets> 命名空間包含 Windows Sockets 介面的 Managed 實作。 <xref:System.Net> 命名空間中的所有其他網路存取類別都建立在此通訊端實作之上。  
  
 .NET Framework <xref:System.Net.Sockets.Socket> 類別是 Winsock32 API 所提供的通訊端服務 Managed 程式碼版本。 在大部分情況下，**Socket** 類別方法，只會將資料封送處理成原生 Win32 相對物，並處理任何必要的安全性檢查。  
  
 **Socket** 類別支援兩種基本的模式，同步和非同步。 在同步模式中，呼叫執行網路作業的函式 (例如 <xref:System.Net.Sockets.Socket.Send%2A> 和 <xref:System.Net.Sockets.Socket.Receive%2A>) 會等候作業完成，然後才將控制權傳回給呼叫端程式。 在非同步模式中，這些呼叫會立即傳回。  
  
## <a name="see-also"></a>另請參閱

- [如何：建立通訊端](how-to-create-a-socket.md)

- [使用應用程式通訊協定](using-application-protocols.md)
