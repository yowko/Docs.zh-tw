---
title: 安全性和競爭情形
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57ceaedc7c38ae70a0db5a7fd584a765a7474aff
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210490"
---
# <a name="security-and-race-conditions"></a>安全性和競爭情形
值得注意的另一個部分是利用競爭條件安全性漏洞的可能性。 有數種方式，這可能發生。 請依照下列子主題說明一些主要的開發人員必須避免的陷阱。  
  
## <a name="race-conditions-in-the-dispose-method"></a>Dispose 方法中的競爭情形  
 如果類別的**處置**方法 (如需詳細資訊，請參閱[回收](../../../docs/standard/garbage-collection/index.md)) 是未同步處理，就可以在該清除程式碼**處置**可以執行多個一次，如下列範例所示。  
  
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
  
 因為這**處置**實作未同步處理，就可能`Cleanup`由第一個執行緒，然後第二個執行緒呼叫`_myObj`設定為**null**。 這是否有安全性考量而定會發生什麼事時`Cleanup`程式碼隨即執行。 未同步處理的主要問題**處置**實作牽涉到的資源控制代碼，例如檔案使用。 處理不當，可能會導致錯誤控制代碼使用，通常會導致安全性弱點。  
  
## <a name="race-conditions-in-constructors"></a>建構函式中的競爭情形  
 在某些應用程式，它可能會供其他執行緒來存取類別成員，才能完全執行其類別建構函式。 您應該再次檢查以確定沒有任何安全性問題如果這應該會發生，或如有必要，同步處理執行緒的所有類別建構函式。  
  
## <a name="race-conditions-with-cached-objects"></a>使用快取物件的競爭情形  
 程式碼會快取安全性資訊，或是使用程式碼存取安全性[Assert](../../../docs/framework/misc/using-the-assert-method.md)作業可能也會很容易的競爭情形如果未適當地同步處理類別的其他部分，如下列範例所示。  
  
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
  
 如果有其他路徑`DoOtherWork`，可以從相同的物件與另一個執行緒呼叫，不受信任的呼叫者可略過過去的需求。  
  
 如果您的程式碼會快取安全性資訊，請確定該檢閱的這項弱點。  
  
## <a name="race-conditions-in-finalizers"></a>完成項中的競爭情形  
 物件，參考靜態或不受管理的資源，然後讓其完成項中也可能會發生競爭情形。 如果多個物件共用資源類別的完成項中操作時，物件必須同步處理所有存取該資源。  
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)
