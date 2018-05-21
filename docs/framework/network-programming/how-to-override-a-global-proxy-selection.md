---
title: 如何：覆寫全域 Proxy 的選取範圍
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c10cff979a18d8e07a1e7089f96157e4c38f040e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="ad02d-102">如何：覆寫全域 Proxy 的選取範圍</span><span class="sxs-lookup"><span data-stu-id="ad02d-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="ad02d-103">這個範例會在連接埠 80 上將 **WebRequest** 傳送到 www.contoso.com，以使用名為 `alternateproxy` 的 Proxy 伺服器覆寫全域 Proxy 的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="ad02d-103">This example sends a **WebRequest** to www.contoso.com that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad02d-104">範例</span><span class="sxs-lookup"><span data-stu-id="ad02d-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ad02d-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ad02d-105">Compiling the Code</span></span>  
 <span data-ttu-id="ad02d-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="ad02d-106">This example requires:</span></span>  
  
-   <span data-ttu-id="ad02d-107">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="ad02d-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad02d-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="ad02d-108">See Also</span></span>  
 [<span data-ttu-id="ad02d-109">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="ad02d-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="ad02d-110">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="ad02d-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
