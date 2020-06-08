---
title: 如何：要求網頁並擷取結果當做資料流
description: 這個範例示範如何要求網頁，並在 .NET Framework 中取出資料流程中的結果。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: bd57f9af6be29c783d044e785ebb36aaa8592df2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502479"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="9886d-103">如何：要求網頁並擷取結果當做資料流</span><span class="sxs-lookup"><span data-stu-id="9886d-103">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>

<span data-ttu-id="9886d-104">這個範例示範如何要求網頁並擷取資料流中的結果。</span><span class="sxs-lookup"><span data-stu-id="9886d-104">This example shows how to request a Web page and retrieve the results in a stream.</span></span>
  
## <a name="example"></a><span data-ttu-id="9886d-105">範例</span><span class="sxs-lookup"><span data-stu-id="9886d-105">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="9886d-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9886d-106">Compiling the Code</span></span>

 <span data-ttu-id="9886d-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="9886d-107">This example requires:</span></span>

- <span data-ttu-id="9886d-108"><xref:System.IO> 和 <xref:System.Net> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="9886d-108">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="9886d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9886d-109">See also</span></span>

- [<span data-ttu-id="9886d-110">要求資料</span><span class="sxs-lookup"><span data-stu-id="9886d-110">Requesting Data</span></span>](requesting-data.md)
