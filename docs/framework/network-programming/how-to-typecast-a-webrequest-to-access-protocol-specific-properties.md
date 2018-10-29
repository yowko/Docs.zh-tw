---
title: 如何：轉換 WebRequest 類型以存取通訊協定特定屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: ec5b9f1db17cf1c90484b0a44063efef9fa16cf9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50180084"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a><span data-ttu-id="2f559-102">如何：轉換 WebRequest 類型以存取通訊協定特定屬性</span><span class="sxs-lookup"><span data-stu-id="2f559-102">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>
<span data-ttu-id="2f559-103">這個範例示範如何轉換 WebRequest 類型以存取通訊協定特定屬性。</span><span class="sxs-lookup"><span data-stu-id="2f559-103">This example shows how to typecast a WebRequest so that you can access protocol specific properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f559-104">範例</span><span class="sxs-lookup"><span data-stu-id="2f559-104">Example</span></span>  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f559-105">請參閱</span><span class="sxs-lookup"><span data-stu-id="2f559-105">See Also</span></span>  
 [<span data-ttu-id="2f559-106">可插式通訊協定程式設計</span><span class="sxs-lookup"><span data-stu-id="2f559-106">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
