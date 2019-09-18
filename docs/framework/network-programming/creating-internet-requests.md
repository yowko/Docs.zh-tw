---
title: 建立網際網路要求
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 80e3a6bd199691df9391e88d5a64fab5df2a08a1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048612"
---
# <a name="creating-internet-requests"></a>建立網際網路要求
應用程式會透過 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 方法來建立 <xref:System.Net.WebRequest> 執行個體。 這是建立衍生自 **WebRequest** 之類別的靜態方法 (視傳遞給它的 URI 配置而定)。  
  
## <a name="web-file-and-ftp-requests"></a>Web、檔案和 FTP 要求  
 .NET Framework 提供衍生自 **WebRequest** 的 <xref:System.Net.HttpWebRequest> 類別，來處理 HTTP 和 HTTPS 要求。 在大部分情況下，**WebRequest** 類別會提供您提出要求所需的所有屬性；不過，必要時，您可以將 **WebRequest.Create** 方法所建立的 **WebRequest** 物件轉換為 **HttpWebRequest** 類型，以存取要求的 HTTP 特定屬性。 同樣地，**HttpWebResponse** 物件會處理來自 HTTP 和 HTTPS 要求的回應。 若要存取 **HttpWebResponse** 物件的 HTTP 特定屬性，您需要將 **WebResponse** 物件轉換為 **HttpWebResponse** 類型。  
  
 .NET Framework 也會提供 <xref:System.Net.FileWebRequest> 和 <xref:System.Net.FileWebResponse> 類別，來處理使用 "file:"URI 配置之資源的要求。 同樣地，提供 <xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 類別，以處理使用 "ftp:" 配置之資源的要求。 如果您的要求適用於使用所有這些配置的資源，則可以使用 **WebRequest.Create** 方法，來取得用來提出要求的物件。  
  
 若要處理使用其他應用程式層級通訊協定的要求，您需要實作衍生自 **WebRequest** 和 **WebResponse** 的通訊協定特定類別。 如需詳細資訊，請參閱[可插式通訊協定程式設計](programming-pluggable-protocols.md)。  
  
## <a name="see-also"></a>另請參閱

- [如何：使用 WebRequest 類別要求資料](how-to-request-data-using-the-webrequest-class.md)
- [要求資料](requesting-data.md)
