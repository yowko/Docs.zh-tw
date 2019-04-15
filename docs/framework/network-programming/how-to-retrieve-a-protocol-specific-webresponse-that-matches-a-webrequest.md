---
title: 作法：擷取符合 WebRequest 的通訊協定專屬 WebResponse
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: fee2b725afbceef45b9651a7cd88a61b37952e32
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087374"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a>作法：擷取符合 WebRequest 的通訊協定專屬 WebResponse
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
  
## <a name="see-also"></a>另請參閱

- [要求資料](../../../docs/framework/network-programming/requesting-data.md)
