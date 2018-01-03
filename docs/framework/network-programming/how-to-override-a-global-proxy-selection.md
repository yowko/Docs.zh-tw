---
title: "如何：覆寫全域 Proxy 的選取範圍"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 970b428343f4e2dec73e7eceec20414cd8bdfbac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-override-a-global-proxy-selection"></a>如何：覆寫全域 Proxy 的選取範圍
這個範例會在連接埠 80 上將 **WebRequest** 傳送到 www.contoso.com，以使用名為 `alternateproxy` 的 Proxy 伺服器覆寫全域 Proxy 的選取範圍。  
  
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
  
-   對 **System.Net** 命名空間的參考。  
  
## <a name="see-also"></a>請參閱  
 [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)  
 [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
