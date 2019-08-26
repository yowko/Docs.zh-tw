---
title: 作法：覆寫全域 Proxy 的選取範圍
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: e5f4dc22ad75dc4d4f7dc30f44e6ae304403ef16
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914522"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="e40de-102">作法：覆寫全域 Proxy 的選取範圍</span><span class="sxs-lookup"><span data-stu-id="e40de-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="e40de-103">這個範例會在連接埠 80 上將 **WebRequest** 傳送到 `www.contoso.com`，以使用名為 `alternateproxy` 的 Proxy 伺服器覆寫全域 Proxy 的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="e40de-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e40de-104">範例</span><span class="sxs-lookup"><span data-stu-id="e40de-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e40de-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e40de-105">Compiling the Code</span></span>  
 <span data-ttu-id="e40de-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="e40de-106">This example requires:</span></span>  
  
- <span data-ttu-id="e40de-107">**System.Net** 命名空間的[`using`指示詞](../../csharp/language-reference/keywords/using-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="e40de-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40de-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e40de-108">See also</span></span>

- [<span data-ttu-id="e40de-109">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="e40de-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="e40de-110">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="e40de-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
