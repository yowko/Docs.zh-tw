---
title: 如何：擷取符合 WebRequest 的通訊協定特定 WebResponse
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2a72e57156903c9d436a49aaf6da596868af4003
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47454865"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a>如何：擷取符合 WebRequest 的通訊協定特定 WebResponse
這個範例示範如何擷取符合 WebRequest 的通訊協定特定 WebResponse。  
  
## <a name="example"></a>範例  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   對 **System.Net** 命名空間的參考。  
  
## <a name="see-also"></a>請參閱  
 [要求資料](../../../docs/framework/network-programming/requesting-data.md)
