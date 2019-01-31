---
title: HOW TO：啟用 WebRequest 以使用 Proxy 與網際網路通訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: d8bcf20831a806694ab40ed7584365d8109e1460
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689009"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>HOW TO：啟用 WebRequest 以使用 Proxy 與網際網路通訊
這個範例會建立全域 Proxy 執行個體，可讓任何 <xref:System.Net.WebRequest> 使用 Proxy 與網際網路通訊。 這個範例假設 Proxy 伺服器名為 `webproxy`，且在連接埠 80 (標準 HTTP 連接埠) 上進行通訊。  
  
## <a name="example"></a>範例  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   **System.Net** 命名空間的[`using`指示詞](../../csharp/language-reference/keywords/using-directive.md)。  
  
## <a name="see-also"></a>另請參閱
- [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)
- [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
