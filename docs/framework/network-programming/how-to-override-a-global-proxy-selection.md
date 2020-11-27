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
  
- **System.Net** 命名 [ `using` 空間的指示](../../csharp/language-reference/keywords/using-directive.md)詞。  
  
## <a name="see-also"></a>另請參閱

- [使用應用程式通訊協定](using-application-protocols.md)
- [透過 Proxy 存取網際網路](accessing-the-internet-through-a-proxy.md)
