---
title: 作法：覆寫全域 Proxy 的選取範圍
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: f822aa18b6eecaa1b1302ad6cc6b94f0b016e330
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127370"
---
# <a name="how-to-override-a-global-proxy-selection"></a>作法：覆寫全域 Proxy 的選取範圍
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
