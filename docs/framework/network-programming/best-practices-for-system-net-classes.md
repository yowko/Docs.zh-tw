---
title: System.Net 類別的最佳作法
ms.date: 03/30/2017
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
ms.openlocfilehash: 5bb3ac545613da68d5f370fefbf94b674b70fe64
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200944"
---
# <a name="best-practices-for-systemnet-classes"></a>System.Net 類別的最佳作法
下列建議將協助您善加利用 <xref:System.Net> 中所含的類別：  
  
-   如需傳輸層安全性 (TLS) 的最佳做法，請參閱 [.NET Framework 的傳輸層安全性 (TLS) 最佳做法](tls.md)。

-   可能的話，請使用 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse>，而不是對子系類別進行類型轉換。 使用 **WebRequest** 和 **WebResponse** 的應用程式可以利用新的網際網路通訊協定，而不需要大量的程式碼變更。  
  
-   使用 **System.Net** 類別撰寫在伺服器上執行的 ASP.NET 應用程式時，其效能通常會比使用 <xref:System.Net.WebRequest.GetResponse%2A> 和 <xref:System.Net.WebResponse.GetResponseStream%2A> 的非同步方法還要好。  
  
-   開啟至網際網路資源的連線數目，會對網路效能和輸送量造成明顯影響。 **System.Net** 預設會為每個主機的每個應用程式使用兩個連線。 在應用程式的 <xref:System.Net.ServicePoint> 中設定 <xref:System.Net.ServicePoint.ConnectionLimit%2A> 屬性，可能會針對特定主機增加這個數目。 設定 <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> 屬性可以為所有主機增加這個預設值。  
  
-   撰寫通訊端層級通訊協定時，請盡可能嘗試使用 <xref:System.Net.Sockets.TcpClient> 或 <xref:System.Net.Sockets.UdpClient>，而不是直接寫入至 <xref:System.Net.Sockets.Socket>。 這兩個用戶端類別會封裝 TCP 和 UDP 通訊端的建立，而不需要您處理連線的詳細資料。  
  
-   存取需要認證的網站時，請使用 <xref:System.Net.CredentialCache> 類別建立認證的快取，而不是每個要求都提供它們。 **CredentialCache** 類別會搜尋快取，以透過要求找到要呈現的適當認證，讓您不需要負責根據 URL 來建立和呈現認證。  
  
## <a name="see-also"></a>另請參閱

- [以 .NET Framework 進行網路程式設計](../../../docs/framework/network-programming/index.md)
