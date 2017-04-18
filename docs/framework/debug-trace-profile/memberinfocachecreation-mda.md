---
title: "memberInfoCacheCreation MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "member info cache creation"
  - "MemberInfoCacheCreation MDA"
  - "reflection, run-time errors"
  - "MDAs (managed debugging assistants), cache"
  - "cache [.NET Framework], reflection"
  - "managed debugging assistants (MDAs), cache"
  - "MemberInfo cache"
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# memberInfoCacheCreation MDA
當建立 <xref:System.Reflection.MemberInfo> 快取時，`memberInfoCacheCreation` Managed 偵錯助理 \(MDA\) 就會啟動。  這是一種程式的強式提示，會利用耗費昂貴資源的反映 \(Reflection\) 功能。  
  
## 症狀  
 程式的工作集增加，因為程式使用耗費昂貴資源的反映。  
  
## 原因  
 與 <xref:System.Reflection.MemberInfo> 物件有關的反映作業會被視為需要昂貴的資源，因為它們必須讀取儲存在頁面中的中繼資料，而且通常會指示此問題使用晚期繫結案例的某個型別。  
  
## 解決方式  
 您可以藉由啟用這個 MDA，然後在偵錯工具中執行程式碼，或在啟動 MDA 時附加偵錯工具，藉以判斷反映在程式中使用的地方。  在偵錯工具之下，您將會取得堆疊追蹤，以顯示建立 <xref:System.Reflection.MemberInfo> 快取的地方，並可以從這個地方判斷程式使用反映的地方。  
  
 解決方法會取決於程式碼的目的；  這個 MDA 提醒您程式有晚期繫結的情況，  您可能會想要判斷是否可以替代早期繫結的情況，或是考量晚期繫結情況的效能。  
  
## 對執行階段的影響  
 每一個建立的 <xref:System.Reflection.MemberInfo> 快取都會啟動這個 MDA；  效能的影響是可以忽略的。  
  
## Output  
 MDA 會輸出一則訊息，表示已經建立 <xref:System.Reflection.MemberInfo> 快取。  請使用偵錯工具來取得堆疊追蹤，以顯示程式正在使用反映。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## 範例  
 此範例程式碼將會啟動 `memberInfoCacheCreation` MDA。  
  
```  
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## 請參閱  
 <xref:System.Reflection.MemberInfo>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)