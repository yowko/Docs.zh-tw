---
title: 作法：啟用 WebRequest 以使用 Proxy 與網際網路通訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 99bbff5a3350f55f04fdbd6ce7147b6597773322
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624592"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="924ef-102">作法：啟用 WebRequest 以使用 Proxy 與網際網路通訊</span><span class="sxs-lookup"><span data-stu-id="924ef-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="924ef-103">這個範例會建立全域 Proxy 執行個體，可讓任何 <xref:System.Net.WebRequest> 使用 Proxy 與網際網路通訊。</span><span class="sxs-lookup"><span data-stu-id="924ef-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="924ef-104">這個範例假設 Proxy 伺服器名為 `webproxy`，且在連接埠 80 (標準 HTTP 連接埠) 上進行通訊。</span><span class="sxs-lookup"><span data-stu-id="924ef-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="924ef-105">範例</span><span class="sxs-lookup"><span data-stu-id="924ef-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="924ef-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="924ef-106">Compiling the Code</span></span>  
 <span data-ttu-id="924ef-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="924ef-107">This example requires:</span></span>  
  
- <span data-ttu-id="924ef-108">**System.Net** 命名空間的[`using`指示詞](../../csharp/language-reference/keywords/using-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="924ef-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="924ef-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="924ef-109">See also</span></span>

- [<span data-ttu-id="924ef-110">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="924ef-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="924ef-111">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="924ef-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
