---
title: "如何：啟用 WebRequest 以使用 Proxy 與網際網路通訊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 68871505e735485dd73d219b4144d56eabe21e43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="795eb-102">如何：啟用 WebRequest 以使用 Proxy 與網際網路通訊</span><span class="sxs-lookup"><span data-stu-id="795eb-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="795eb-103">這個範例會建立全域 Proxy 執行個體，可讓任何 <xref:System.Net.WebRequest> 使用 Proxy 與網際網路通訊。</span><span class="sxs-lookup"><span data-stu-id="795eb-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="795eb-104">這個範例假設 Proxy 伺服器名為 `webproxy`，且在連接埠 80 (標準 HTTP 連接埠) 上進行通訊。</span><span class="sxs-lookup"><span data-stu-id="795eb-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="795eb-105">範例</span><span class="sxs-lookup"><span data-stu-id="795eb-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="795eb-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="795eb-106">Compiling the Code</span></span>  
 <span data-ttu-id="795eb-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="795eb-107">This example requires:</span></span>  
  
-   <span data-ttu-id="795eb-108">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="795eb-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="795eb-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="795eb-109">See Also</span></span>  
 [<span data-ttu-id="795eb-110">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="795eb-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="795eb-111">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="795eb-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
