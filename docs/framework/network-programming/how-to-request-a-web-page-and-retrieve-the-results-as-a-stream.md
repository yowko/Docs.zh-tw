---
title: 作法：要求網頁並擷取結果當作資料流
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 23c094f0a3f528750c9589dbc99a0ada86236967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097196"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="9a2be-102">作法：要求網頁並擷取結果當作資料流</span><span class="sxs-lookup"><span data-stu-id="9a2be-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="9a2be-103">這個範例示範如何要求網頁並擷取資料流中的結果。</span><span class="sxs-lookup"><span data-stu-id="9a2be-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a2be-104">範例</span><span class="sxs-lookup"><span data-stu-id="9a2be-104">Example</span></span>  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9a2be-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9a2be-105">Compiling the Code</span></span>  
 <span data-ttu-id="9a2be-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="9a2be-106">This example requires:</span></span>  
  
-   <span data-ttu-id="9a2be-107"><xref:System.IO> 和 <xref:System.Net> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="9a2be-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a2be-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a2be-108">See also</span></span>

- [<span data-ttu-id="9a2be-109">要求資料</span><span class="sxs-lookup"><span data-stu-id="9a2be-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
