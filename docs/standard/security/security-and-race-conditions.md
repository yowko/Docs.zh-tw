---
title: "Security and Race Conditions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "security [.NET Framework], race conditions"
  - "race conditions"
  - "secure coding, race conditions"
  - "code security, race conditions"
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# Security and Race Conditions
另一個值得注意的部分是在競爭情形中利用安全性漏洞的可能性。  可能出現這種問題的狀況有好幾種。  以下的副標題概述開發人員應該避免的幾個主要危險狀況。  
  
## Dispose 方法中的競爭情形  
 如果類別的 **Dispose** 方法 \(如需詳細資訊，請參閱[Garbage Collection](../../../docs/standard/garbage-collection/index.md)\) 沒有同步處理，**Dispose** 內的清除程式碼可能會執行超過一次以上，如下列範例所示。  
  
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
  
 由於這個 **Dispose** 實作並未同步處理，因此在 `_myObj` 設定為 **null** 之前，`Cleanup` 可能被第一個執行緒呼叫，接著被第二個執行緒呼叫。  這個問題算不算安全性疑慮需視 `Cleanup` 程式碼執行時所發生的狀況而定。  未同步處理的 **Dispose** 實作的主要問題與使用資源控制代碼 \(如檔案\) 有關。  處理不當可能會造成控點的誤用，而常導致安全性出現漏洞。  
  
## 建構函式中的競爭情形  
 某些應用程式中，其他執行緒可能會在它們的類別建構函式還沒執行完畢之前就先存取類別成員。  如果發生這種狀況，您應該檢閱所有的類別建構函式，確定是否有安全性的問題，或是在必要時同步處理執行緒。  
  
## 快取物件的競爭情形  
 如以下的範例所示，如果類別的其他部分沒有經過適當的同步處理，快取安全性資訊或是使用程式碼存取安全性 [Assert](../../../docs/framework/misc/using-the-assert-method.md) 作業的程式碼，可能也比較會有競爭情形的問題。  
  
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
  
 如果有別的路徑可供另一個執行緒使用相同的物件來呼叫 `DoOtherWork`，未受信任的呼叫端就可以暗中送出需求。  
  
 如果您的程式碼快取了安全性資訊，請務必加以檢閱，以確定是否有漏洞。  
  
## 結束常式中的競爭情形  
 另一個可能發生競爭情形的狀況是：物件參考靜態或 Unmanaged 資源，並接著在其結束函式中釋出該資源。  如果有多個物件共用一個在類別的結束函式中操作的資源，則這些物件必須同步處理對該資源的所有存取。  
  
## 請參閱  
 [Secure Coding Guidelines](../../../docs/standard/security/secure-coding-guidelines.md)