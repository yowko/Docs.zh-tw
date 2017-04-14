---
title: "invalidMemberDeclaration MDA | Microsoft Docs"
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
  - "invalid member declaration"
  - "InvalidMemberDeclaration MDA"
  - "marshaling, run-time errors"
  - "managed debugging assistants (MDAs), marshaling"
  - "MDAs (managed debugging assistants), marshaling"
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# invalidMemberDeclaration MDA
會啟動 `invalidMemberDeclaration` Managed 偵錯助理 \(MDA\) 來報告錯誤，這些錯誤發生在決定如何封送處理成員參數為由 COM 所呼叫時。  
  
## 徵兆  
 失敗的 HRESULT 會傳回給 COM，而不呼叫 Managed 方法。  
  
## 原因  
 最可能的原因是其中一個參數上不相容的 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性。  
  
## 解決方式  
 請在此參數上指定有效的 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性。  
  
## 對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## 輸出  
 告知性訊息，包含成員名稱、類型名稱和錯誤訊息。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)