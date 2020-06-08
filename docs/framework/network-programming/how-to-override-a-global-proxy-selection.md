---
title: 如何：覆寫全域 Proxy 的選取範圍
description: 請遵循此範例來覆寫全域 proxy 選取專案，方法是將 WebRequest 傳送至 URL，以使用 proxy 伺服器來覆寫選取專案。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 91f64775e2f401be9b740fe9e4c41e1087eb9617
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502505"
---
# <a name="how-to-override-a-global-proxy-selection"></a>如何：覆寫全域 Proxy 的選取範圍
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
  
- **System.Net**命名[ `using` 空間的指示](../../csharp/language-reference/keywords/using-directive.md)詞。  
  
## <a name="see-also"></a>另請參閱

- [使用應用程式通訊協定](using-application-protocols.md)
- [透過 Proxy 存取網際網路](accessing-the-internet-through-a-proxy.md)
