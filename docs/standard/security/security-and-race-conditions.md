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
ms.openlocfilehash: 715bf240a5f7f44ba3f914ad6788631074aa41b2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291015"
---
# <a name="security-and-race-conditions"></a>安全性和競爭情形
另一個考慮領域，是競爭情形所利用的安全性漏洞的潛能。 有數種方式可能會發生這種情況。 接下來的子主題概述開發人員必須避免的一些主要陷阱。  
  
## <a name="race-conditions-in-the-dispose-method"></a>Dispose 方法中的競爭條件  
 如果類別的**dispose**方法（如需詳細資訊，請參閱[垃圾收集](../garbage-collection/index.md)）未同步處理，則可能會多次執行**Dispose**內的清除程式碼，如下列範例所示。  
  
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
  
 因為此**處置**執行不會同步處理，所以第一個 `Cleanup` 執行緒可能會呼叫，而第二個執行緒則會 `_myObj` 設定為**null**。 這是否為安全性考慮，取決於程式碼執行時會發生什麼事 `Cleanup` 。 未同步處理**處置**的主要問題牽涉到使用像是檔案之類的資源控制碼。 不當處置可能會導致使用錯誤的控制碼，這通常會造成安全性弱點。  
  
## <a name="race-conditions-in-constructors"></a>在函式中的競爭條件  
 在某些應用程式中，其他執行緒可能會在其類別的函式完全執行之前存取類別成員。 您應該檢查所有類別的程式，以確保在發生這種情況時沒有安全性問題，或視需要同步處理執行緒。  
  
## <a name="race-conditions-with-cached-objects"></a>具有快取物件的競爭條件  
 如果類別的其他部分未適當地同步處理，則快取安全性資訊或使用代碼[啟用安全性判斷](../../framework/misc/using-the-assert-method.md)提示作業的程式碼，也可能會受到競爭條件的影響，如下列範例所示。  
  
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
  
 如果有其他路徑 `DoOtherWork` 可以從具有相同物件的另一個執行緒呼叫，則不受信任的呼叫端可以超過需求。  
  
 如果您的程式碼會快取安全性資訊，請確定您已針對此弱點進行檢查。  
  
## <a name="race-conditions-in-finalizers"></a>完成項中的競爭條件  
 競爭條件也可能發生在參考靜態或非受控資源的物件中，然後它會在其完成項中釋出。 如果多個物件共用在類別的完成項中操作的資源，則物件必須同步處理該資源的所有存取。  
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](secure-coding-guidelines.md)
