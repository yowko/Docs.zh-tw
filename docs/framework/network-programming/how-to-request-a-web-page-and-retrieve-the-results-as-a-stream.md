---
title: HOW TO：要求網頁並擷取結果當作資料流
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 5ef1867d84b619c58a7b3e29ed0f81f9db0c07a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54578581"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>HOW TO：要求網頁並擷取結果當作資料流
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
  
## <a name="see-also"></a>另請參閱
- [要求資料](../../../docs/framework/network-programming/requesting-data.md)
