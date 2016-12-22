---
title: "fixed 陳述式 (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "fixed_CSharpKeyword"
  - "fixed"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "fixed 關鍵字 [C#]"
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# fixed 陳述式 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`fixed` 陳述式可讓記憶體回收行程避免重新配置可移動的變數。  `fixed` 陳述式只允許在 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 內容中。  `Fixed` 也可用來建立[固定大小緩衝區](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)。  
  
 `fixed` 陳述式會設定一個指標至 Managed 變數，並在陳述式執行期間將此變數固定住。  如果沒有 `fixed`，Managed 變數的指標也許沒有多大用處，因為記憶體回收可能會在非預期下重新配置變數。  C\# 編譯器只能讓您將指標指派到 `fixed` 陳述式中的 Managed 變數。  
  
 [!CODE [csrefKeywordsFixedLock#1](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsFixedLock#1)]  
  
 您可以使用陣列、字串、固定大小的緩衝區或變數的位址初始化指標。  下列範例說明變數位址、陣列和字串的用法。  如需關於固定大小緩衝區的詳細資訊，請參閱[固定大小的緩衝區](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).  
  
 [!CODE [csrefKeywordsFixedLock#2](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsFixedLock#2)]  
  
 只要都有相同的型別，您就可以初始化多個指標。  
  
```  
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```  
  
 若要初始化不同型別的指標，只需將 `fixed` 陳述式巢狀化，如下列範例所示。  
  
 [!CODE [csrefKeywordsFixedLock#3](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsFixedLock#3)]  
  
 執行陳述式中的程式碼後，任何已固定的變數將取消固定並且交付記憶體回收。  因此請不要指向 `fixed` 陳述式之外的變數。  
  
> [!NOTE]
>  不能修改在 fixed 陳述式中初始化的指標。  
  
 在不安全模式，您可以配置在堆疊上的記憶體；那裡並不需要交付給記憶體回收，因此不需要固定。  如需詳細資訊，請參閱 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)。  
  
## 範例  
 [!CODE [csrefKeywordsFixedLock#4](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsFixedLock#4)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [固定大小的緩衝區](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)