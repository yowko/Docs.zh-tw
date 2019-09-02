---
title: 連結要求
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f040e1e1706e1f84ced8b253ff3fb15dbcbd6e1e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206018"
---
# <a name="link-demands"></a>連結要求
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 連結要求會在 Just-In-Time 編譯期間進行安全性檢查，並且只檢查程式碼組件的即時呼叫者。 當您的程式碼繫結至類型參考，包括函式指標參考和方法呼叫時，連結就會發生。 如果呼叫的組件並沒有足夠權限可連結到您的程式碼，則程式碼載入和執行時不會允許連結且會擲回執行階段例外狀況。 連結要求可以在繼承自您的程式碼的類別中被覆寫。  
  
 請注意，對這種類型的需求不會執行完整堆疊查核行程，而且您的程式碼仍會受到引誘攻擊。 例如, 如果元件 A 中的方法受到連結要求的保護, 則元件 B 中的直接呼叫端會根據元件 B 的許可權進行評估。 不過, 如果連結要求使用元件 B 中的方法間接呼叫元件 A 中的方法, 則不會評估元件 C 中的方法。連結要求只會指定立即呼叫元件中的直接呼叫端許可權, 必須連結至您的程式碼。 它並未指定所有呼叫端必須擁有以便執行程式碼的權限。  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>、<xref:System.Security.CodeAccessPermission.Deny%2A> 和 <xref:System.Security.CodeAccessPermission.PermitOnly%2A> 堆疊查核行程修飾詞不會影響連結要求的評估。  由於連結要求不會執行堆疊查核行程，堆疊查核行程修飾詞不會影響連結要求。  
  
 如果受連結要求保護的方法是透過[反映](../reflection-and-codedom/reflection.md)來存取, 則連結要求會檢查透過反映存取之程式碼的立即呼叫端。 使用反映來執行的方法探索和方法引動過程都是如此。 例如, 假設程式碼使用反映來<xref:System.Reflection.MethodInfo>傳回物件, 代表受連結要求保護的方法, 然後將該**MethodInfo**物件傳遞給使用物件來叫用原始方法的其他程式碼。 在此情況下, 連結要求檢查會發生兩次: 一次是針對傳回**MethodInfo**物件的程式碼, 另一次是針對叫用它的程式碼。  
  
> [!NOTE]
> 在靜態類別建構函式上執行的連結要求不會保護建構函式，因為靜態建構函式由系統所呼叫，不在應用程式的程式碼執行路徑中。 如此一來，當連結需求套用至整個類別時，它無法保護對靜態建構函式的存取權，不過它確實會保護類別的其餘部分。  
  
 下列程式碼片段以宣告方式指定連結至 `ReadData` 方法的任何程式碼都必須具有 `CustomPermission` 權限。 此權限是假設的自訂權限，並不存在於 .NET Framework 中。 要求是藉由將**SecurityAction**旗標傳遞至來`CustomPermissionAttribute`進行。  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function    
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [屬性](../../standard/attributes/index.md)
- [程式碼存取安全性](code-access-security.md)
