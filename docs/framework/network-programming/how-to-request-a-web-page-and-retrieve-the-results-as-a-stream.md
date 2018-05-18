---
title: 如何：要求網頁並擷取結果當做資料流
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 31856e7fc7136b3bdb8fab9fdf8185de32a3007a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>如何：要求網頁並擷取結果當做資料流
這個範例示範如何要求網頁並擷取資料流中的結果。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   <xref:System.IO> 和 <xref:System.Net> 命名空間的參考。  
  
## <a name="see-also"></a>請參閱  
 [要求資料](../../../docs/framework/network-programming/requesting-data.md)
