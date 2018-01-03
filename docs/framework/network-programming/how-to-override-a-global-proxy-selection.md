---
title: "如何：覆寫全域 Proxy 的選取範圍"
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
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 970b428343f4e2dec73e7eceec20414cd8bdfbac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="93ab6-102">如何：覆寫全域 Proxy 的選取範圍</span><span class="sxs-lookup"><span data-stu-id="93ab6-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="93ab6-103">這個範例會在連接埠 80 上將 **WebRequest** 傳送到 www.contoso.com，以使用名為 `alternateproxy` 的 Proxy 伺服器覆寫全域 Proxy 的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="93ab6-103">This example sends a **WebRequest** to www.contoso.com that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93ab6-104">範例</span><span class="sxs-lookup"><span data-stu-id="93ab6-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="93ab6-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="93ab6-105">Compiling the Code</span></span>  
 <span data-ttu-id="93ab6-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="93ab6-106">This example requires:</span></span>  
  
-   <span data-ttu-id="93ab6-107">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="93ab6-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93ab6-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="93ab6-108">See Also</span></span>  
 [<span data-ttu-id="93ab6-109">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="93ab6-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="93ab6-110">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="93ab6-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
