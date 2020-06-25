---
title: 建立網際網路要求
description: 瞭解應用程式如何透過 WebRequest 建立 WebRequest 實例，此方法會根據傳遞給它的 URI 配置來建立衍生類別。
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
ms.openlocfilehash: 389c7bf5969eca4322aa680a6f28dec0b899709a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325639"
---
# <a name="create-internet-requests"></a>建立網際網路要求

應用程式會透過 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 方法來建立 <xref:System.Net.WebRequest> 執行個體。 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>是一種靜態方法，會 <xref:System.Net.WebRequest> 根據傳遞給它的 URI 配置，建立衍生自的類別。  
  
## <a name="web-file-and-ftp-requests"></a>Web、檔案和 FTP 要求

.NET Framework 提供 <xref:System.Net.HttpWebRequest> 衍生自的類別， `WebRequest` 以處理 HTTP 和 HTTPS 要求。 在大多數情況下， `WebRequest` 類別會提供提出要求所需的所有屬性; 不過，如有必要，您可以將 `WebRequest` 方法所建立的物件轉換 `WebRequest.Create` 成 `HttpWebRequest` 類型，以存取要求的 HTTP 特定屬性。 同樣地， `HttpWebResponse` 物件會處理來自 HTTP 和 HTTPS 要求的回應。 若要存取物件的 HTTP 特定屬性 `HttpWebResponse` ，您必須將 `WebResponse` 物件轉換成 `HttpWebResponse` 類型。  
  
.NET Framework 也會提供 <xref:System.Net.FileWebRequest> 和 <xref:System.Net.FileWebResponse> 類別，來處理使用 "file：" URI 配置之資源的要求。 同樣地，提供 <xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 類別，以處理使用 "ftp:" 配置之資源的要求。 如果您的要求是針對使用任何這些配置的資源，您可以使用 `WebRequest.Create` 方法來取得要用來提出要求的物件。  
  
若要處理使用其他應用層級通訊協定的要求，請執行衍生自和的通訊協定特定類別 `WebRequest` `WebResponse` 。 如需詳細資訊，請參閱程式[設計插即用通訊協定](programming-pluggable-protocols.md)。  
  
## <a name="see-also"></a>另請參閱

- [如何：使用 WebRequest 類別要求資料](how-to-request-data-using-the-webrequest-class.md)
- [要求資料](requesting-data.md)
