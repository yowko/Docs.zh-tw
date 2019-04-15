---
title: 3.5 版中的通訊端效能增強功能
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
ms.openlocfilehash: 28f2543d1f8c81efd32ffbb644265fb5709a9bb3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333284"
---
# <a name="socket-performance-enhancements-in-version-35"></a>3.5 版中的通訊端效能增強功能
<xref:System.Net.Sockets.Socket?displayProperty=nameWithType> 類別已經在版本 3.5 中增強，以供使用非同步網路 I/O 的應用程式使用，以達到最高的效能。 一系列新類別已新增在 <xref:System.Net.Sockets.Socket> 類別的一組增強功能當中，提供另一種非同步模式，可供專業化的高效能通訊端應用程式使用。 這些增強功能專為需要高效能的網路伺服器應用程式而設計。 應用程式可以獨佔方式，使用增強的非同步模式，或是只在其應用程式的目標熱區使用 (例如接收大量資料時)。  
  
## <a name="class-enhancements"></a>類別增強功能  
 這些增強功能的主要功能是在大量的非同步通訊端 I/O 期間，避免重複配置和同步處理物件。 <xref:System.Net.Sockets.Socket> 類別目前針對非同步通訊端 I/O 所實作的 Begin/End 設計模式，需要為每個非同步通訊端作業配置一個 <xref:System.IAsyncResult?displayProperty=nameWithType> 物件。  
  
 在新的 <xref:System.Net.Sockets.Socket> 類別增強功能中，應用程式所配置和維護的可重複使用 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> 類別物件會描述非同步通訊端作業。 高效能通訊端應用程式最知道必須維持的重疊通訊端作業量。 應用程式可以視需要建立許多 <xref:System.Net.Sockets.SocketAsyncEventArgs> 物件。 例如，如果伺服器應用程式需要隨時有 15 個通訊端接受作業，以支援內送的用戶端連線比率，它可以事先配置 15 個可重複使用的 <xref:System.Net.Sockets.SocketAsyncEventArgs> 物件以用於此用途。  
  
 以這個類別執行非同步通訊端作業的模式，包含下列步驟：  
  
1. 配置新 <xref:System.Net.Sockets.SocketAsyncEventArgs> 內容物件，或從應用程式集區取得一個可用的內容物件。  
  
2. 將內容物件上的屬性設為即將執行的作業 (例如回呼委派方法和資料緩衝處理)。  
  
3. 呼叫適當的通訊端方法 (xxxAsync) 來啟始非同步作業。  
  
4. 如果非同步通訊端方法 (xxxAsync) 在回呼中傳回 true，請查詢內容屬性以取得完成狀態。  
  
5. 如果非同步通訊端方法 (xxxAsync) 在回呼中傳回 false，則作業以同步方式完成。 可以查詢內容屬性以取得作業結果。  
  
6. 重複使用內容進行另一個作業、將它放入集區，或是將它捨棄。  
  
 新非同步通訊端作業內容物件的存留期，取決於應用程式程式碼中的參考和非同步 I/O 參考。 應用程式不需要在送出作為其中一個非同步通訊端作業方法的參數之後，保留對非同步通訊端作業內容物件的參考。 在完成回呼傳回之前，它會一直被參考。 不過讓應用程式保留內容物件的參考有好處，它可以重複用於未來的非同步通訊端作業。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>
- [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)
- [通訊端程式碼範例](socket-code-examples.md)
