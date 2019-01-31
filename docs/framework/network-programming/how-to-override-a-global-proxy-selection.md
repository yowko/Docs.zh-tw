---
title: HOW TO：覆寫全域 Proxy 的選取範圍
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 6973503f12e0e60ee139c5cd7da09ab319d70218
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592120"
---
# <a name="how-to-override-a-global-proxy-selection"></a>HOW TO：覆寫全域 Proxy 的選取範圍
這個範例會在連接埠 80 上將 **WebRequest** 傳送到 `www.contoso.com`，以使用名為 `alternateproxy` 的 Proxy 伺服器覆寫全域 Proxy 的選取範圍。  
  
## <a name="example"></a>範例  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   **System.Net** 命名空間的[`using`指示詞](~/docs/csharp/language-reference/keywords/using-directive.md)。  
  
## <a name="see-also"></a>另請參閱
- [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)
- [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
