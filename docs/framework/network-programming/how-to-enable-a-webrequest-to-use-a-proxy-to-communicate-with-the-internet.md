---
title: 如何：啟用 WebRequest 以使用 Proxy 與網際網路通訊
description: 瞭解如何建立全域 proxy 實例，讓任何 WebRequest 在 .NET Framework 中使用 proxy 與網際網路通訊。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 0fc33cea3f5a7fe4669b110e53e71afdb9561c23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502531"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="17c8a-103">如何：啟用 WebRequest 以使用 Proxy 與網際網路通訊</span><span class="sxs-lookup"><span data-stu-id="17c8a-103">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="17c8a-104">這個範例會建立全域 Proxy 執行個體，可讓任何 <xref:System.Net.WebRequest> 使用 Proxy 與網際網路通訊。</span><span class="sxs-lookup"><span data-stu-id="17c8a-104">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="17c8a-105">這個範例假設 Proxy 伺服器名為 `webproxy`，且在連接埠 80 (標準 HTTP 連接埠) 上進行通訊。</span><span class="sxs-lookup"><span data-stu-id="17c8a-105">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="17c8a-106">範例</span><span class="sxs-lookup"><span data-stu-id="17c8a-106">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="17c8a-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="17c8a-107">Compiling the Code</span></span>

<span data-ttu-id="17c8a-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="17c8a-108">This example requires:</span></span>

- <span data-ttu-id="17c8a-109">**System.Net**命名空間[ `using` 的 c #](../../csharp/language-reference/keywords/using-directive.md)指示詞。</span><span class="sxs-lookup"><span data-stu-id="17c8a-109">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="17c8a-110">**System.Net**命名空間的 Visual Basic [ `Imports` 語句](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="17c8a-110">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="17c8a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17c8a-111">See also</span></span>

- [<span data-ttu-id="17c8a-112">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="17c8a-112">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="17c8a-113">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="17c8a-113">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
