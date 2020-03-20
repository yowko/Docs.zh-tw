---
title: 如何：啟用 WebRequest 以使用 Proxy 與網際網路通訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 8b38973e4cb2c83ce32b8a08e54d828a8eeef879
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73039544"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="4c0a6-102">如何：啟用 WebRequest 以使用 Proxy 與網際網路通訊</span><span class="sxs-lookup"><span data-stu-id="4c0a6-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="4c0a6-103">這個範例會建立全域 Proxy 執行個體，可讓任何 <xref:System.Net.WebRequest> 使用 Proxy 與網際網路通訊。</span><span class="sxs-lookup"><span data-stu-id="4c0a6-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="4c0a6-104">這個範例假設 Proxy 伺服器名為 `webproxy`，且在連接埠 80 (標準 HTTP 連接埠) 上進行通訊。</span><span class="sxs-lookup"><span data-stu-id="4c0a6-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="4c0a6-105">範例</span><span class="sxs-lookup"><span data-stu-id="4c0a6-105">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="4c0a6-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4c0a6-106">Compiling the Code</span></span>

<span data-ttu-id="4c0a6-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="4c0a6-107">This example requires:</span></span>

- <span data-ttu-id="4c0a6-108">**System.Net**命名空間[`using`](../../csharp/language-reference/keywords/using-directive.md)的 C# 指令。</span><span class="sxs-lookup"><span data-stu-id="4c0a6-108">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="4c0a6-109">**System.Net**命名空間的可視基本[`Imports`語句](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="4c0a6-109">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c0a6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c0a6-110">See also</span></span>

- [<span data-ttu-id="4c0a6-111">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="4c0a6-111">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="4c0a6-112">通過代理訪問互聯網</span><span class="sxs-lookup"><span data-stu-id="4c0a6-112">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
