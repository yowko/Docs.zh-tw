---
title: HOW TO：覆寫全域 Proxy 的選取範圍
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: f822aa18b6eecaa1b1302ad6cc6b94f0b016e330
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127370"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="fe059-102">HOW TO：覆寫全域 Proxy 的選取範圍</span><span class="sxs-lookup"><span data-stu-id="fe059-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="fe059-103">這個範例會在連接埠 80 上將 **WebRequest** 傳送到 `www.contoso.com`，以使用名為 `alternateproxy` 的 Proxy 伺服器覆寫全域 Proxy 的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="fe059-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe059-104">範例</span><span class="sxs-lookup"><span data-stu-id="fe059-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fe059-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="fe059-105">Compiling the Code</span></span>  
 <span data-ttu-id="fe059-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="fe059-106">This example requires:</span></span>  
  
-   <span data-ttu-id="fe059-107">**System.Net** 命名空間的[`using`指示詞](~/docs/csharp/language-reference/keywords/using-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="fe059-107">A [`using` directive](~/docs/csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe059-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe059-108">See also</span></span>

- [<span data-ttu-id="fe059-109">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="fe059-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="fe059-110">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="fe059-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
