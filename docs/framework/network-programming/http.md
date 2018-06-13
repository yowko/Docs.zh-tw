---
title: HTTP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ed61a8addd204320560c773e917613c52e56bff4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394455"
---
# <a name="http"></a>HTTP
.NET Framework 可透過 <xref:System.Net.HttpWebRequest> 和 <xref:System.Net.HttpWebResponse> 類別，對於佔據所有網際網路流量絕大部分的 HTTP 通訊協定提供全面的支援。 這些類別衍生自 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse>，每當靜態方法 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 碰到以 "http" 或 "https" 開頭的 URI 時，預設會傳回這些類別。 在大部分情況下，**WebRequest** 和 **WebResponse** 類別提供了提出要求所需的一切功能，但是如果您需要存取以屬性方式公開的 HTTP 特定功能，則可以將這些類別轉型為 **HttpWebRequest** 或 **HttpWebResponse**。  
  
 **HttpWebRequest** 和 **HttpWebResponse** 封裝了標準的 HTTP 要求與回應交易，並提供對一般 HTTP 標頭的存取。 這些類別也支援大部分的 HTTP 1.1 功能，包括管線操作、以區塊方式傳送和接收資料 、驗證、預先驗證、加密、Proxy 支援、伺服器憑證驗證，以及連線管理。 自訂標頭和未透過屬性提供的標頭則可透過 **Headers** 屬性來儲存和存取。  
  
 **HttpWebRequest** 是 **WebRequest** 所使用的預設類別，在您將 URI 傳遞至 **WebRequest.Create** 方法之前，不需要登錄此類別。  
  
 您可以將 <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> 屬性設定為 **true** (預設值)，讓您的應用程式自動遵循 HTTP 重新導向。 應用程式將重新導向要求，而 **HttpWebResponse** 的 <xref:System.Net.HttpWebResponse.ResponseUri%2A> 屬性會包含回應要求的實際 Web 資源。 如果將 **AllowAutoRedirect** 設定為 **false**，則您的應用程式必須能夠處理重新導向當成 HTTP 通訊協定錯誤。  
  
 應用程式藉由將 <xref:System.Net.WebException.Status%2A> 設為 <xref:System.Net.WebExceptionStatus> 來捕捉 <xref:System.Net.WebException>，以便接收 HTTP 通訊協定錯誤。 <xref:System.Net.WebException.Response%2A> 屬性包含伺服器所傳送的 **WebResponse**，並指出實際發生的 HTTP 錯誤。  
  
## <a name="see-also"></a>請參閱  
 [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)  
 [如何：存取 HTTP 特定屬性](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
