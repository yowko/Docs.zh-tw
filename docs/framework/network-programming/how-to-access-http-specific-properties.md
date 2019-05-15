---
title: 作法：存取 HTTP 特定屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: 044a48aaffbd2d4ef490405a65236b17ecca1fbf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645791"
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="66c3b-102">作法：存取 HTTP 特定屬性</span><span class="sxs-lookup"><span data-stu-id="66c3b-102">How to: Access HTTP-Specific Properties</span></span>
<span data-ttu-id="66c3b-103">這個範例示範如何關閉 HTTP **保持運作**行為，以及如何從 Web 伺服器取得通訊協定版本號碼。</span><span class="sxs-lookup"><span data-stu-id="66c3b-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66c3b-104">範例</span><span class="sxs-lookup"><span data-stu-id="66c3b-104">Example</span></span>  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =   
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="66c3b-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="66c3b-105">Compiling the Code</span></span>  
 <span data-ttu-id="66c3b-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="66c3b-106">This example requires:</span></span>  
  
- <span data-ttu-id="66c3b-107">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="66c3b-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c3b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66c3b-108">See also</span></span>

- [<span data-ttu-id="66c3b-109">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="66c3b-109">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="66c3b-110">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="66c3b-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="66c3b-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="66c3b-111">HTTP</span></span>](../../../docs/framework/network-programming/http.md)
