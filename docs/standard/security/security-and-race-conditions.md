---
title: 安全性和競爭情形
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
ms.openlocfilehash: 870dc0ac956bad045cb87b9c0968b4a8e9733812
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824118"
---
# <a name="security-and-race-conditions"></a>安全性和競爭情形

另一個考慮的地方是競爭情形所利用的安全性漏洞。 發生這種情況的方式有好幾種。 接下來的子主題概述了開發人員必須避免的一些主要陷阱。  
  
## <a name="race-conditions-in-the-dispose-method"></a>Dispose 方法中的競爭條件  

如果類別的 **Dispose** 方法 (如需詳細資訊，請參閱 [垃圾收集](../garbage-collection/index.md)) 不會進行同步處理。 **Dispose** 內的清除程式碼可能會執行一次以上，如下列範例所示。  
  
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
  
因為這項 **處置** 不會進行同步處理，所以可能 `Cleanup` 會由第一個執行緒呼叫，然後在 `_myObj` 設定為 **null** 之前呼叫第二個執行緒。 這是否為安全性考慮，取決於程式碼執行時所發生的情況 `Cleanup` 。 未同步處理 **處置** 的主要問題包括使用資源控制碼，例如檔案。 不當處置可能會導致使用錯誤的控制碼，而這通常會導致安全性漏洞。  
  
## <a name="race-conditions-in-constructors"></a>函數中的競爭條件

在某些應用程式中，其他執行緒可能會在其類別的函式完全執行之前，存取類別成員。 您應該檢查所有類別的函式，以確保在發生這種情況時，不會發生安全性問題，或是在必要時同步處理執行緒。  
  
## <a name="race-conditions-with-cached-objects"></a>使用快取物件的競爭條件  

如果類別的其他部分未適當地進行同步處理，則快取安全性資訊或使用代碼 [啟用安全性判斷](../../framework/misc/using-the-assert-method.md) 提示作業的程式碼可能也會很容易受到競爭條件的影響，如下列範例所示。  
  
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
  
如果有其他路徑 `DoOtherWork` 可以從具有相同物件的另一個執行緒呼叫，不受信任的呼叫端可能會超過要求。  
  
如果您的程式碼會快取安全性資訊，請務必檢查此弱點。  
  
## <a name="race-conditions-in-finalizers"></a>完成項中的競爭條件  

競爭條件也可以出現在參考靜態或非受控資源的物件中，然後它會在其完成項中釋出。 如果有多個物件共用在類別的完成項中操作的資源，則物件必須同步處理該資源的所有存取。  
  
## <a name="see-also"></a>請參閱

- [安全程式碼撰寫方針](secure-coding-guidelines.md)
- [ASP.NET Core 安全性](/aspnet/core/security/)
