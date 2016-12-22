---
title: "Unsafe 程式碼和指標 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "安全性 [C#]，類型安全"
  - "C# 語言，不安全的程式碼"
  - "類型安全 [C#]"
  - "unsafe 關鍵字 [C#]"
  - "unsafe 程式碼 [C#]"
  - "C# 語言，指標"
  - "指標 [C#]，關於指標"
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Unsafe 程式碼和指標 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

為了維護型別安全 \(Type Safety\) 和安全性，C\# 預設不支援指標算術。  然而，藉由使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字，即可定義能在其中使用指標的 unsafe 內容。  如需指標的詳細資訊，請參閱[指標型別](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)主題。  
  
> [!NOTE]
>  在 Common Language Runtime \(CLR\) 中，Unsafe 程式碼稱為無法驗證的程式碼。  C\# 中的 Unsafe 程式碼不一定具有危險性，只是它的安全性無法由 CLR 驗證。  因此，CLR 將只會執行位於完全受信任組件內部的 Unsafe 程式碼。  如果您使用 Unsafe 程式碼，請務必確認程式碼不會帶來安全性風險或造成指標錯誤。  
  
## Unsafe 程式碼概觀  
 Unsafe 程式碼具有下列屬性：  
  
-   方法、型別及程式碼區塊都可以定義為 Unsafe  
  
-   在某些情況下，Unsafe 程式碼可能藉由移除陣列界限檢查，來增加應用程式的效能  
  
-   當呼叫需要指標的原生函式時，便會需要使用 Unsafe 程式碼  
  
-   使用 Unsafe 程式碼會帶來安全性和穩定性風險  
  
-   為了讓 C\# 編譯 Unsafe 程式碼，必須以 [\/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) 來編譯應用程式  
  
## 相關章節  
 如需詳細資訊，請參閱：  
  
-   [指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [固定大小的緩衝區](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [如何：使用指標複製位元組陣列](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)