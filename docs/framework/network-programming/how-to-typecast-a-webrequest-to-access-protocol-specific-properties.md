---
title: 作法：轉換 WebRequest 類型以存取通訊協定特定屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: a9488e484aad7ba3df23c33b2cb5b79f234b758e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088362"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a>作法：轉換 WebRequest 類型以存取通訊協定特定屬性
這個範例示範如何轉換 WebRequest 類型以存取通訊協定特定屬性。  
  
## <a name="example"></a>範例  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a>另請參閱

- [可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
