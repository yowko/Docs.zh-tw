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
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="68e48-102">作法：擷取符合 WebRequest 的通訊協定專屬 WebResponse</span><span class="sxs-lookup"><span data-stu-id="68e48-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="68e48-103">這個範例示範如何擷取符合 WebRequest 的通訊協定特定 WebResponse。</span><span class="sxs-lookup"><span data-stu-id="68e48-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68e48-104">範例</span><span class="sxs-lookup"><span data-stu-id="68e48-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="68e48-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="68e48-105">Compiling the Code</span></span>  
 <span data-ttu-id="68e48-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="68e48-106">This example requires:</span></span>  
  
-   <span data-ttu-id="68e48-107">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="68e48-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e48-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68e48-108">See also</span></span>

- [<span data-ttu-id="68e48-109">要求資料</span><span class="sxs-lookup"><span data-stu-id="68e48-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
