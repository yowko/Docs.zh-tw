---
title: 作法：擷取符合 WebRequest 的通訊協定專屬 WebResponse
description: 瞭解如何取得符合 .NET Framework 中 WebRequest 的通訊協定特定 WebResponse。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: fd163c115dcd19c05f93f4c202b043440834ba9d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266736"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="a952f-103">作法：擷取符合 WebRequest 的通訊協定專屬 WebResponse</span><span class="sxs-lookup"><span data-stu-id="a952f-103">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>

<span data-ttu-id="a952f-104">這個範例示範如何擷取符合 WebRequest 的通訊協定特定 WebResponse。</span><span class="sxs-lookup"><span data-stu-id="a952f-104">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a952f-105">範例</span><span class="sxs-lookup"><span data-stu-id="a952f-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a952f-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a952f-106">Compiling the Code</span></span>  

 <span data-ttu-id="a952f-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="a952f-107">This example requires:</span></span>  
  
- <span data-ttu-id="a952f-108">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="a952f-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a952f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a952f-109">See also</span></span>

- [<span data-ttu-id="a952f-110">要求資料</span><span class="sxs-lookup"><span data-stu-id="a952f-110">Requesting Data</span></span>](requesting-data.md)
