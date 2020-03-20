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
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>如何：要求網頁並擷取結果當做資料流

這個範例示範如何要求網頁並擷取資料流中的結果。
  
## <a name="example"></a>範例

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

## <a name="compiling-the-code"></a>編譯程式碼

 這個範例需要：

- <xref:System.IO> 和 <xref:System.Net> 命名空間的參考。

## <a name="see-also"></a>另請參閱

- [要求資料](requesting-data.md)
