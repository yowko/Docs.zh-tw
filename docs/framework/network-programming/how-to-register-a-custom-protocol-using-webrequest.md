---
title: "如何：使用 WebRequest 註冊自訂通訊協定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7fefaf65fe0bf1c761e976359f3015389a557369
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>如何：使用 WebRequest 註冊自訂通訊協定
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
  
## <a name="see-also"></a>請參閱  
 [可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
