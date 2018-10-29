---
title: 如何：擷取符合 WebRequest 的通訊協定特定 WebResponse
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: f1da226fb62c55f37183404765430c094f1cd63f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188270"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="f7d88-102">如何：擷取符合 WebRequest 的通訊協定特定 WebResponse</span><span class="sxs-lookup"><span data-stu-id="f7d88-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="f7d88-103">這個範例示範如何擷取符合 WebRequest 的通訊協定特定 WebResponse。</span><span class="sxs-lookup"><span data-stu-id="f7d88-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7d88-104">範例</span><span class="sxs-lookup"><span data-stu-id="f7d88-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f7d88-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f7d88-105">Compiling the Code</span></span>  
 <span data-ttu-id="f7d88-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="f7d88-106">This example requires:</span></span>  
  
-   <span data-ttu-id="f7d88-107">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="f7d88-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d88-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="f7d88-108">See Also</span></span>  
 [<span data-ttu-id="f7d88-109">要求資料</span><span class="sxs-lookup"><span data-stu-id="f7d88-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
