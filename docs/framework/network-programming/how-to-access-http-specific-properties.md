---
title: 如何：存取 HTTP 特定屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: 68ad6b2c55cd5cc467e53441caa778ea10b994fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180857"
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="a4e7d-102">如何：存取 HTTP 特定屬性</span><span class="sxs-lookup"><span data-stu-id="a4e7d-102">How to: Access HTTP-Specific Properties</span></span>
<span data-ttu-id="a4e7d-103">這個範例示範如何關閉 HTTP **保持運作**行為，以及如何從 Web 伺服器取得通訊協定版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a4e7d-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4e7d-104">範例</span><span class="sxs-lookup"><span data-stu-id="a4e7d-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="a4e7d-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a4e7d-105">Compiling the Code</span></span>  
 <span data-ttu-id="a4e7d-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="a4e7d-106">This example requires:</span></span>  
  
- <span data-ttu-id="a4e7d-107">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="a4e7d-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4e7d-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4e7d-108">See also</span></span>

- [<span data-ttu-id="a4e7d-109">通過代理訪問互聯網</span><span class="sxs-lookup"><span data-stu-id="a4e7d-109">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="a4e7d-110">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="a4e7d-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="a4e7d-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="a4e7d-111">HTTP</span></span>](http.md)
