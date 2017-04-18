---
title: "成員多載 | Microsoft Docs"
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
  - "預設引數"
  - "多載成員 [.NET Framework]"
  - "多載成員設計方針 [.NET Framework]"
  - "多載成員"
  - "成員簽章"
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 成員多載
成員多載是指只有的數字或參數型別不同，但具有相同名稱的相同型別上建立兩個或多個成員。 例如，下列命令，在 `WriteLine` 方法多載︰  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
  
```  
  
 方法、 建構函式和索引的屬性可以包含參數，因為只有這些成員可以多載。  
  
 多載是其中一個最重要的技術，提升可用性、 生產力和可重複使用程式庫的可讀性。 多載的參數數目可以提供更簡單的建構函式和方法的版本。 多載的參數型別上可以使用相同的成員名稱，執行相同作業上將選取的不同類型的成員。  
  
 **✓ 執行** 嘗試使用描述性的參數名稱，表示使用較短的多載的預設值。  
  
 **X 避免** 任意改變中多載的參數名稱。 如果其中一個多載中的參數代表相同的輸入參數，以在另一個多載，這些參數應該有相同的名稱。  
  
 **X 避免** 不一致順序中的參數中的多載成員。 具有相同名稱的參數應該會出現在所有多載中的相同位置。  
  
 **✓ 執行** 讓只有最長的多載虛擬 （如果需要這項擴充性）。 較短的多載只應該呼叫較長的多載。  
  
 **X 不** 使用 `ref` 或 `out` 多載成員的修飾詞。  
  
 某些語言無法解析多載，就像這樣的呼叫。 此外，此類多載通常具有完全不同的語意，而且可能不應該多載，但這兩種方法改為。  
  
 **X 不** 具有多載具有相同的位置和類似的型別參數，但使用不同的語意。  
  
 **✓ 執行**  允許 `null` 為選擇性引數傳遞。  
  
 **✓ 執行** 使用成員多載，而不會定義具有預設引數的成員。  
  
 預設引數不符合 CLS 標準。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)