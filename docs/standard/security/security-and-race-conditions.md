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
ms.openlocfilehash: fdfc4d9e9ba3653bd1a762767e3c39a4f62e587a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582131"
---
# <a name="security-and-race-conditions"></a>安全性和競爭情形
值得注意的另一個部分是利用競爭情形的安全性漏洞的可能性。 有幾種的方式可能造成此。 請依照下列子主題簡述一些主要開發人員必須避免的陷阱。  
  
## <a name="race-conditions-in-the-dispose-method"></a>Dispose 方法中的競爭情形  
 如果類別的**處置**方法 (如需詳細資訊，請參閱[回收](../../../docs/standard/garbage-collection/index.md)) 是未同步處理，則可能該的清除程式碼內**處置**可以執行多個一次，如下列範例所示。  
  
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
    if( myObj != null )   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 因為這**處置**實作未同步處理，就可能`Cleanup`由第一個執行緒，然後才能在第二個執行緒呼叫`_myObj`設**null**。 是否有安全性考量而定會發生什麼事時`Cleanup`程式碼執行。 未同步處理的主要問題**處置**實作牽涉到的資源控制代碼，例如檔案使用。 處理不當，可能會導致錯誤使用控制代碼，這通常會導致安全性弱點。  
  
## <a name="race-conditions-in-constructors"></a>建構函式中的競爭情形  
 在某些應用程式，它可能會完全執行其類別建構函式 」 之前存取類別成員的其他執行緒。 您應該檢閱以確定沒有任何安全性問題如果此事件應該會發生，還是有必要，同步處理執行緒的所有類別建構函式。  
  
## <a name="race-conditions-with-cached-objects"></a>快取物件的競爭情形  
 快取安全性資訊或使用程式碼存取安全性的程式碼[Assert](../../../docs/framework/misc/using-the-assert-method.md)作業可能也會很容易競爭如果未適當地同步處理類別的其他部分，如下列範例所示。  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False()  
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
    if(SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false();  
    }  
}  
void DoOtherWork()   
{  
    if( fCallersOK )   
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
  
 如果沒有其他路徑`DoOtherWork`可從另一個執行緒使用相同的物件進行呼叫，不受信任的呼叫端可以略過需求。  
  
 如果您的程式碼會快取的安全性資訊，請確定它檢閱此弱點。  
  
## <a name="race-conditions-in-finalizers"></a>完成項中的競爭情形  
 物件，參考的靜態或未受管理的資源，然後釋放其完成項中也可能會發生競爭情形。 如果多個物件共用資源的操作中類別的完成項，則物件必須同步處理所有對該資源的存取。  
  
## <a name="see-also"></a>另請參閱  
 [安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)
