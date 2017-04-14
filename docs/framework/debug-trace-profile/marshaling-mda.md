---
title: "marshaling MDA | Microsoft Docs"
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
  - "marshaling, run-time errors"
  - "marshaling MDA"
  - "managed debugging assistants (MDAs), marshaling"
  - "MDAs (managed debugging assistants), marshaling"
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# marshaling MDA
當 CLR 設定方法參數或結構之欄位的封送處理資訊時，會啟動 `marshaling` managed 偵錯助理 \(MDA\)。  此 MDA 不適用於 JIT 編譯的組件。  
  
## 對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## 輸出  
 MDA 會顯示在 managed 和 unmanaged 內容的參數或欄位類型，以及包含類型的結構或方法。  以下是欄位輸出的範例：  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## 組態  
 MDA 組態可讓您根據相關的欄位或方法名稱篩選報告的封送處理資訊。  下列範例顯示如何使用 `methodFilter``fieldFilter` 和 `match` 項目以指定篩選條件。  將 `name` 屬性設定為星號 \(\*\) 會比對所有項目。  
  
```  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)