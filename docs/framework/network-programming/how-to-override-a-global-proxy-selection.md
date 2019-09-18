---
title: 作法：覆寫全域 Proxy 的選取範圍
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 44845fb67aac4ff9ab9dda8cf4934153c8c4f23c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048264"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="10967-102">HOW TO：覆寫全域 Proxy 的選取範圍</span><span class="sxs-lookup"><span data-stu-id="10967-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="10967-103">這個範例會在連接埠 80 上將 **WebRequest** 傳送到 `www.contoso.com`，以使用名為 `alternateproxy` 的 Proxy 伺服器覆寫全域 Proxy 的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="10967-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10967-104">範例</span><span class="sxs-lookup"><span data-stu-id="10967-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="10967-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="10967-105">Compiling the Code</span></span>  
 <span data-ttu-id="10967-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="10967-106">This example requires:</span></span>  
  
- <span data-ttu-id="10967-107">**System.Net** 命名空間的[`using`指示詞](../../csharp/language-reference/keywords/using-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="10967-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10967-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10967-108">See also</span></span>

- [<span data-ttu-id="10967-109">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="10967-109">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="10967-110">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="10967-110">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
