---
title: 作法：存取 HTTP 特定屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: 107e57ca947012f5e2f65835d684f5e6068b3681
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176588"
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="2bd0e-102">作法：存取 HTTP 特定屬性</span><span class="sxs-lookup"><span data-stu-id="2bd0e-102">How to: Access HTTP-Specific Properties</span></span>
<span data-ttu-id="2bd0e-103">這個範例示範如何關閉 HTTP **保持運作**行為，以及如何從 Web 伺服器取得通訊協定版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2bd0e-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bd0e-104">範例</span><span class="sxs-lookup"><span data-stu-id="2bd0e-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="2bd0e-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="2bd0e-105">Compiling the Code</span></span>  
 <span data-ttu-id="2bd0e-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="2bd0e-106">This example requires:</span></span>  
  
-   <span data-ttu-id="2bd0e-107">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="2bd0e-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd0e-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bd0e-108">See also</span></span>

- [<span data-ttu-id="2bd0e-109">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="2bd0e-109">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="2bd0e-110">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="2bd0e-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="2bd0e-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="2bd0e-111">HTTP</span></span>](../../../docs/framework/network-programming/http.md)
