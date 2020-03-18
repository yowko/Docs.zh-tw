---
title: 安全性和競爭情形
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
ms.openlocfilehash: 09d8d0d6e85af04fe0fb00f53df408126012081e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186785"
---
# <a name="security-and-race-conditions"></a>安全性和競爭情形
另一個令人關切的領域是，由於比賽條件，可能存在安全性漏洞。 有幾種方法可以做到這一點。 以下子主題概述了開發人員必須避免的一些主要缺陷。  
  
## <a name="race-conditions-in-the-dispose-method"></a>處置方法中的競爭條件  
 如果類的**Dispose**方法（有關詳細資訊，請參閱[垃圾回收](../../../docs/standard/garbage-collection/index.md)）未同步，則 Dispose**內的清理**代碼可能會運行多次，如以下示例所示。  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()
{  
    if (myObj != null)
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 由於此**Dispose**實現不是同步的，因此第`Cleanup`一個執行緒可以調用第一個執行緒，然後將第`_myObj`二個執行緒設置為**null**。 這是否是一個安全問題，取決於`Cleanup`代碼運行時會發生什麼情況。 不同步的**Dispose**實現的主要問題是使用資源控制碼（如檔）。 不當處置可能導致使用錯誤的控制碼，這通常會導致安全性漏洞。  
  
## <a name="race-conditions-in-constructors"></a>建構函式中的競爭條件  
 在某些應用程式中，其他執行緒可能在其類建構函式完全運行之前訪問類成員。 您應該查看所有類建構函式，以確保如果發生這種情況時沒有安全問題，或者在必要時同步執行緒。  
  
## <a name="race-conditions-with-cached-objects"></a>具有緩存物件的競爭條件  
 如果類的其他部分未適當同步，則緩存安全資訊或使用代碼訪問安全[Assert](../../../docs/framework/misc/using-the-assert-method.md)操作的代碼也可能容易受到競爭條件的影響，如下例所示。  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()
{  
    if (SomeDemandPasses())
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()
{  
    if (fCallersOK)
    {  
        DoSomethingTrusted();  
    }  
    else
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 如果可以從具有相同物件的另一`DoOtherWork`個執行緒調用其他路徑，則不受信任的調用方可能會滑過請求。  
  
 如果代碼緩存安全資訊，請確保查看此漏洞。  
  
## <a name="race-conditions-in-finalizers"></a>終端子中的競爭條件  
 競爭條件也可能發生在引用靜態或非託管資源的物件中，然後該資源在其終端子中釋放。 如果多個物件共用在類的終端子中操作的資源，則物件必須同步對該資源的所有訪問。  
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)
