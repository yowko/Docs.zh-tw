---
title: HOW TO：使用 WebRequest 註冊自訂通訊協定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 05b6f6c3f0f1fc1b36b60e8b0dae50de2826aba4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048256"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>HOW TO：使用 WebRequest 註冊自訂通訊協定
這個範例示範如何註冊在其他位置定義的通訊協定特定類別。 在此範例中，`CustomWebRequestCreator` 是使用者實作的物件，其可實作 `CustomWebRequest` 物件傳回的 **Create**方法。 此程式碼範例假設您已撰寫實作自訂通訊協定的 `CustomWebRequest` 程式碼。  
  
## <a name="example"></a>範例  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
 對 <xref:System.Net> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱

- [可插式通訊協定程式設計](programming-pluggable-protocols.md)
