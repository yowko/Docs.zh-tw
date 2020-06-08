---
title: 如何：擷取符合 WebRequest 的通訊協定特定 WebResponse
description: 瞭解如何在 .NET Framework 中，取得符合 WebRequest 的通訊協定特定 WebResponse。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 15b1912a7bd951df7f3c14eb96251c2bdf237b4f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502453"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="515cf-103">如何：擷取符合 WebRequest 的通訊協定特定 WebResponse</span><span class="sxs-lookup"><span data-stu-id="515cf-103">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="515cf-104">這個範例示範如何擷取符合 WebRequest 的通訊協定特定 WebResponse。</span><span class="sxs-lookup"><span data-stu-id="515cf-104">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="515cf-105">範例</span><span class="sxs-lookup"><span data-stu-id="515cf-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="515cf-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="515cf-106">Compiling the Code</span></span>  
 <span data-ttu-id="515cf-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="515cf-107">This example requires:</span></span>  
  
- <span data-ttu-id="515cf-108">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="515cf-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="515cf-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="515cf-109">See also</span></span>

- [<span data-ttu-id="515cf-110">要求資料</span><span class="sxs-lookup"><span data-stu-id="515cf-110">Requesting Data</span></span>](requesting-data.md)
