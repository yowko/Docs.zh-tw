---
title: 作法：覆寫全域 Proxy 的選取範圍
description: 遵循此範例以覆寫全域 proxy 選取專案，方法是將 WebRequest 傳送至 URL，以使用 proxy 伺服器覆寫選取專案。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 8931cdc471b957447277c333ba482a0cec0e6aa5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265735"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="08af7-103">作法：覆寫全域 Proxy 的選取範圍</span><span class="sxs-lookup"><span data-stu-id="08af7-103">How to: Override a Global Proxy Selection</span></span>

<span data-ttu-id="08af7-104">這個範例會在連接埠 80 上將 **WebRequest** 傳送到 `www.contoso.com`，以使用名為 `alternateproxy` 的 Proxy 伺服器覆寫全域 Proxy 的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="08af7-104">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08af7-105">範例</span><span class="sxs-lookup"><span data-stu-id="08af7-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="08af7-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="08af7-106">Compiling the Code</span></span>  

 <span data-ttu-id="08af7-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="08af7-107">This example requires:</span></span>  
  
- <span data-ttu-id="08af7-108">**System.Net** 命名 [ `using` 空間的指示](../../csharp/language-reference/keywords/using-directive.md)詞。</span><span class="sxs-lookup"><span data-stu-id="08af7-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08af7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08af7-109">See also</span></span>

- [<span data-ttu-id="08af7-110">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="08af7-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="08af7-111">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="08af7-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
