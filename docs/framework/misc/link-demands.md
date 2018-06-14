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
ms.openlocfilehash: 29a3254bb5ccfe422a1c2d7d156975c0887d9273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390659"
---
# <a name="link-demands"></a>連結要求
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 連結要求會在 Just-In-Time 編譯期間進行安全性檢查，並且只檢查程式碼組件的即時呼叫者。 當您的程式碼繫結至類型參考，包括函式指標參考和方法呼叫時，連結就會發生。 如果呼叫的組件並沒有足夠權限可連結到您的程式碼，則程式碼載入和執行時不會允許連結且會擲回執行階段例外狀況。 連結要求可以在繼承自您的程式碼的類別中被覆寫。  
  
 請注意，對這種類型的需求不會執行完整堆疊查核行程，而且您的程式碼仍會受到引誘攻擊。 比方說，如果組件 A 中的方法受到連結要求保護，組件 B 中的直接呼叫端是根據評估組件 b 的權限 不過，連結要求不會評估組件 C 中的方法間接呼叫該方法組件 b 中的使用方式的組件中連結要求會指定立即呼叫組件中的呼叫端必須具備要連結至您的程式碼的直接權限。 它並未指定所有呼叫端必須擁有以便執行程式碼的權限。  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>、<xref:System.Security.CodeAccessPermission.Deny%2A> 和 <xref:System.Security.CodeAccessPermission.PermitOnly%2A> 堆疊查核行程修飾詞不會影響連結要求的評估。  由於連結要求不會執行堆疊查核行程，堆疊查核行程修飾詞不會影響連結要求。  
  
 如果連結要求保護的方法透過存取[反映](../../../docs/framework/reflection-and-codedom/reflection.md)，則連結要求會檢查透過反映來存取之程式碼的立即呼叫端。 使用反映來執行的方法探索和方法引動過程都是如此。 例如，假設程式碼使用反映來傳回<xref:System.Reflection.MethodInfo>物件表示方法受到連結要求，然後再將其傳遞**MethodInfo**其他一些使用物件來叫用原始方法的程式碼的物件。 在此情況下，連結要求檢查就會發生兩次： 一次是針對傳回**MethodInfo**物件和一次是針對叫用它。  
  
> [!NOTE]
>  在靜態類別建構函式上執行的連結要求不會保護建構函式，因為靜態建構函式由系統所呼叫，不在應用程式的程式碼執行路徑中。 如此一來，當連結需求套用至整個類別時，它無法保護對靜態建構函式的存取權，不過它確實會保護類別的其餘部分。  
  
 下列程式碼片段以宣告方式指定連結至 `ReadData` 方法的任何程式碼都必須具有 `CustomPermission` 權限。 此權限是假設的自訂權限，並不存在於 .NET Framework 中。 要求是藉由傳遞**SecurityAction.LinkDemand**旗標設為`CustomPermissionAttribute`。  
  
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
 [屬性](../../../docs/standard/attributes/index.md)  
 [程式碼存取安全性](../../../docs/framework/misc/code-access-security.md)
