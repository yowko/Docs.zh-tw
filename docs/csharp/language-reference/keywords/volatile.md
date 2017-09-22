---
title: "volatile (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- volatile_CSharpKeyword
- volatile
dev_langs:
- CSharp
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c8f9fba15991197be885a973435089098a57db87
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="volatile-c-reference"></a>volatile (C# 參考)
`volatile` 關鍵字指出某個欄位可能是由同時執行的多個執行緒所修改。 宣告 `volatile` 的欄位並不適用編譯器最佳化，因為編譯器最佳化是假設由單一執行緒進行存取。 這樣可確保欄位中永遠出現最新的值。  
  
 針對多個執行緒存取的欄位，通常會使用 `volatile` 修飾詞，而不必使用 [lock](../../../csharp/language-reference/keywords/lock-statement.md) 陳述式來序列化存取。  
  
 `volatile` 關鍵字可以套用至下列類型的欄位：  
  
-   參考型別。  
  
-   指標類型 (在不安全的內容中)。 請注意，雖然指標本身可為 volatile，但它所指向的物件不得為 volatile。 換句話說，您無法將指標宣告為 volatile。  
  
-   byte、byte、short、ushort、int、uint、char、float 和 bool 等類型。  
  
-   具有 byte、sbyte、short、ushort、int 或 uint 基底類型之一的列舉類型。  
  
-   已知為參考型別的泛型型別參數。  
  
-   <xref:System.IntPtr> 和 <xref:System.UIntPtr>。  
  
 volatile 關鍵字只能套用至類別或結構的欄位。 區域變數不可以宣告為 `volatile`。  
  
## <a name="example"></a>範例  
 下列範例示範如何將公用欄位變數宣告為 `volatile`。  
  
 [!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a>範例  
 下列範例示範如何建立和使用輔助或背景工作執行緒，以運用主執行緒的輔助或背景工作執行緒來執行平行處理。 如需多執行緒的背景資訊，請參閱 [Managed 執行緒處理](../../../standard/threading/index.md)和[執行緒](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)。  
  
 [!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)

