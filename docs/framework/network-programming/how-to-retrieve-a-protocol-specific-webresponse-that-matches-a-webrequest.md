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
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="4cd1b-102">如何：擷取符合 WebRequest 的通訊協定特定 WebResponse</span><span class="sxs-lookup"><span data-stu-id="4cd1b-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="4cd1b-103">這個範例示範如何擷取符合 WebRequest 的通訊協定特定 WebResponse。</span><span class="sxs-lookup"><span data-stu-id="4cd1b-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cd1b-104">範例</span><span class="sxs-lookup"><span data-stu-id="4cd1b-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4cd1b-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4cd1b-105">Compiling the Code</span></span>  
 <span data-ttu-id="4cd1b-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="4cd1b-106">This example requires:</span></span>  
  
-   <span data-ttu-id="4cd1b-107">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="4cd1b-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd1b-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="4cd1b-108">See Also</span></span>  
 [<span data-ttu-id="4cd1b-109">要求資料</span><span class="sxs-lookup"><span data-stu-id="4cd1b-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
