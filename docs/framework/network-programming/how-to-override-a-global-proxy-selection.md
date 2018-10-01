---
title: 如何：覆寫全域 Proxy 的選取範圍
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2be271123e34f155a79269d3b810c50fe24a40c6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2018
ms.locfileid: "47235932"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="73415-102">如何：覆寫全域 Proxy 的選取範圍</span><span class="sxs-lookup"><span data-stu-id="73415-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="73415-103">這個範例會在連接埠 80 上將 **WebRequest** 傳送到 `www.contoso.com`，以使用名為 `alternateproxy` 的 Proxy 伺服器覆寫全域 Proxy 的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="73415-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73415-104">範例</span><span class="sxs-lookup"><span data-stu-id="73415-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="73415-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="73415-105">Compiling the Code</span></span>  
 <span data-ttu-id="73415-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="73415-106">This example requires:</span></span>  
  
-   <span data-ttu-id="73415-107">**System.Net** 命名空間的[`using`指示詞](~/docs/csharp/language-reference/keywords/using-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="73415-107">A [`using` directive](~/docs/csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73415-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="73415-108">See Also</span></span>  
 [<span data-ttu-id="73415-109">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="73415-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="73415-110">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="73415-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
