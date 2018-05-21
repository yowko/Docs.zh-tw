---
title: 如何：啟用 WebRequest 以使用 Proxy 與網際網路通訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0f57869dfecce3e59d0a255a6201dd966bc407e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="28614-102">如何：啟用 WebRequest 以使用 Proxy 與網際網路通訊</span><span class="sxs-lookup"><span data-stu-id="28614-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="28614-103">這個範例會建立全域 Proxy 執行個體，可讓任何 <xref:System.Net.WebRequest> 使用 Proxy 與網際網路通訊。</span><span class="sxs-lookup"><span data-stu-id="28614-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="28614-104">這個範例假設 Proxy 伺服器名為 `webproxy`，且在連接埠 80 (標準 HTTP 連接埠) 上進行通訊。</span><span class="sxs-lookup"><span data-stu-id="28614-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28614-105">範例</span><span class="sxs-lookup"><span data-stu-id="28614-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="28614-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="28614-106">Compiling the Code</span></span>  
 <span data-ttu-id="28614-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="28614-107">This example requires:</span></span>  
  
-   <span data-ttu-id="28614-108">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="28614-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28614-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="28614-109">See Also</span></span>  
 [<span data-ttu-id="28614-110">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="28614-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="28614-111">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="28614-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
