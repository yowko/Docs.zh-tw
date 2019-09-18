---
title: 作法：轉換 WebRequest 類型以存取通訊協定特定屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: a224d9dbab0157d77c05a5937fe35c027296a674
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048018"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a><span data-ttu-id="ba4a1-102">作法：轉換 WebRequest 類型以存取通訊協定特定屬性</span><span class="sxs-lookup"><span data-stu-id="ba4a1-102">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>
<span data-ttu-id="ba4a1-103">這個範例示範如何轉換 WebRequest 類型以存取通訊協定特定屬性。</span><span class="sxs-lookup"><span data-stu-id="ba4a1-103">This example shows how to typecast a WebRequest so that you can access protocol specific properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba4a1-104">範例</span><span class="sxs-lookup"><span data-stu-id="ba4a1-104">Example</span></span>  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba4a1-105">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba4a1-105">See also</span></span>

- [<span data-ttu-id="ba4a1-106">可插式通訊協定程式設計</span><span class="sxs-lookup"><span data-stu-id="ba4a1-106">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
