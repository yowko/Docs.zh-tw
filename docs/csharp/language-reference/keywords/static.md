---
title: "static (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "static"
  - "static_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "static 關鍵字 [C#]"
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# static (C# 參考)
`static` 修飾詞 \(Modifier\) 可用來宣告靜態成員，此成員屬於型別本身，並不隸屬任何一個物件。  `static` 修飾詞可以用於類別、欄位、方法、屬性、運算子、事件及建構函式 \(Constructor\)，但是不能用於索引子 \(Indexer\)、解構函式 \(Destructor\) 或類別以外的型別。  如需詳細資訊，請參閱 [靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
## 範例  
 下列類別是宣告為 `static`，而且只包含 `static` 方法：  
  
 [!code-cs[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#18)]  
  
 常數或型別宣告隱含靜態成員。  
  
 靜態成員無法經由執行個體來參考。  相反地，它需要經由型別名稱來參考。  例如，請參考下列類別：  
  
 [!code-cs[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#19)]  
  
 若要參考靜態成員 `x`，請使用完整的名稱 `MyBaseC.MyStruct.x`，除非它是從相同範圍來存取：  
  
```c#  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 雖然一個類別的執行個體包含類別所有執行個體欄位的分別複本，但是每一個靜態欄位只有一個複本。  
  
 不可以使用[這個](../../../csharp/language-reference/keywords/this.md)參考靜態方法或屬性存取子。  
  
 如果類別套用了 `static` 關鍵字，則此類別的所有成員必定為靜態。  
  
 類別和靜態類別都可能具有靜態建構函式。  靜態建構函式會在程式啟動與類別具現化 \(Instantiated\) 之間的某個時間點進行呼叫。  
  
> [!NOTE]
>  `static` 關鍵字的用法比在 C\+\+ 中具有更多限制。  若要與 C\+\+ 關鍵字進行比較，請參閱 [Static](/visual-cpp/misc/static-cpp)。  
  
 為了示範靜態成員，以代表公司員工的類別為例。  假設此類別包含一方法來計算員工人數和一個欄位來儲存員工人數。  此方法和欄位不屬於任何執行個體員工。  相反的，他們屬於公司類別。  因此，他們應該宣告成類別的靜態成員。  
  
## 範例  
 這個範例讀取新員工的名字和 ID、然後累加員工人數，並且顯示此新員工的資訊以及員工新人數。  為了簡化，這個程式從鍵盤讀取目前的員工人數。  在實際應用上，這項資訊應從檔案讀取。  
  
 [!code-cs[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#20)]  
  
## 範例  
 這個範例會示範，雖然您可以使用其他尚未宣告的靜態欄位來初始化靜態欄位，但是在明確指派值給該靜態欄位之前，結果都會是未定義的。  
  
 [!code-cs[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#21)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)