---
title: 如何：要求網頁並擷取結果當做資料流
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 65bda268cd77959dbcd786c365d0a30c324b89ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "71393103"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="e7f7b-102">如何：要求網頁並擷取結果當做資料流</span><span class="sxs-lookup"><span data-stu-id="e7f7b-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>

<span data-ttu-id="e7f7b-103">這個範例示範如何要求網頁並擷取資料流中的結果。</span><span class="sxs-lookup"><span data-stu-id="e7f7b-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>
  
## <a name="example"></a><span data-ttu-id="e7f7b-104">範例</span><span class="sxs-lookup"><span data-stu-id="e7f7b-104">Example</span></span>

```csharp
var myClient = new WebClient();
Stream response = myClient.OpenRead("https://docs.microsoft.com/dotnet/");
// The stream data is used here.
response.Close();
```

```vb
Dim myClient As New WebClient()
Dim response As Stream = myClient.OpenRead("https://docs.microsoft.com/dotnet/")
' The stream data is used here.
response.Close()
```

## <a name="compiling-the-code"></a><span data-ttu-id="e7f7b-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e7f7b-105">Compiling the Code</span></span>

 <span data-ttu-id="e7f7b-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="e7f7b-106">This example requires:</span></span>

- <span data-ttu-id="e7f7b-107"><xref:System.IO> 和 <xref:System.Net> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="e7f7b-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7f7b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7f7b-108">See also</span></span>

- [<span data-ttu-id="e7f7b-109">要求資料</span><span class="sxs-lookup"><span data-stu-id="e7f7b-109">Requesting Data</span></span>](requesting-data.md)
