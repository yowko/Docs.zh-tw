---
title: "通訊端"
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
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9050c7bdae8f08601259e865742016f188d3e0af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sockets"></a>通訊端
<xref:System.Net.Sockets> 命名空間包含 Windows Sockets 介面的 Managed 實作。 <xref:System.Net> 命名空間中的所有其他網路存取類別都建立在此通訊端實作之上。  
  
 .NET Framework <xref:System.Net.Sockets.Socket> 類別是 Winsock32 API 所提供的通訊端服務 Managed 程式碼版本。 在大部分情況下，**Socket** 類別方法，只會將資料封送處理成原生 Win32 相對物，並處理任何必要的安全性檢查。  
  
 **Socket** 類別支援兩種基本的模式，同步和非同步。 在同步模式中，呼叫執行網路作業的函式 (例如 <xref:System.Net.Sockets.Socket.Send%2A> 和 <xref:System.Net.Sockets.Socket.Receive%2A>) 會等候作業完成，然後才將控制權傳回給呼叫端程式。 在非同步模式中，這些呼叫會立即傳回。  
  
## <a name="see-also"></a>請參閱  
 [如何：建立通訊端](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)
