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
ms.openlocfilehash: a0466eb5c24840c77a3b191f9b0e001f6b267fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181165"
---
# <a name="link-demands"></a>連結要求
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 連結要求會在 Just-In-Time 編譯期間進行安全性檢查，並且只檢查程式碼組件的即時呼叫者。 當您的程式碼繫結至類型參考，包括函式指標參考和方法呼叫時，連結就會發生。 如果呼叫的組件並沒有足夠權限可連結到您的程式碼，則程式碼載入和執行時不會允許連結且會擲回執行階段例外狀況。 連結要求可以在繼承自您的程式碼的類別中被覆寫。  
  
 請注意，對這種類型的需求不會執行完整堆疊查核行程，而且您的程式碼仍會受到引誘攻擊。 例如，如果程式集 A 中的方法受鏈路請求保護，則根據程式集 B 的許可權計算程式集 B 中的直接調用方。 但是，如果鏈路要求在裝配體 B 中使用方法間接調用程式集 A 中的方法，則不會計算程式集 C 中的方法。連結請求僅指定直接調用程式集中必須連結到代碼的許可權。 它並未指定所有呼叫端必須擁有以便執行程式碼的權限。  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>、<xref:System.Security.CodeAccessPermission.Deny%2A> 和 <xref:System.Security.CodeAccessPermission.PermitOnly%2A> 堆疊查核行程修飾詞不會影響連結要求的評估。  由於連結要求不會執行堆疊查核行程，堆疊查核行程修飾詞不會影響連結要求。  
  
 如果通過[反射](../reflection-and-codedom/reflection.md)訪問受連結請求保護的方法，則連結請求將檢查通過反射訪問的代碼的直接調用方。 使用反映來執行的方法探索和方法引動過程都是如此。 例如，假設代碼使用反射返回表示受連結<xref:System.Reflection.MethodInfo>請求保護的方法的物件，然後將**該方法資訊**物件傳遞給使用該物件調用原始方法的其他代碼。 在這種情況下，連結需求檢查發生兩次：一次用於返回**MethodInfo**物件的代碼，一次用於調用它的代碼。  
  
> [!NOTE]
> 在靜態類別建構函式上執行的連結要求不會保護建構函式，因為靜態建構函式由系統所呼叫，不在應用程式的程式碼執行路徑中。 如此一來，當連結需求套用至整個類別時，它無法保護對靜態建構函式的存取權，不過它確實會保護類別的其餘部分。  
  
 下列程式碼片段以宣告方式指定連結至 `ReadData` 方法的任何程式碼都必須具有 `CustomPermission` 權限。 此權限是假設的自訂權限，並不存在於 .NET Framework 中。 通過將**安全操作.LinkDemand**標誌傳遞給 。 `CustomPermissionAttribute`  
  
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
- [代碼訪問安全性](code-access-security.md)
