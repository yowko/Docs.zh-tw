---
title: "常數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 常數"
  - "常數 [C#]"
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# 常數 (C# 程式設計手冊)
常數是在編譯時期才得到的不可變值，且在程式的存留期中不會改變。  常數會使用 [const](../../../csharp/language-reference/keywords/const.md) 修飾詞宣告。  只有 C\# 內建型別 \(不包括 <xref:System.Object?displayProperty=fullName>\) 能宣告為 `const`。  如需內建型別的清單，請參閱[內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)。  使用者定義的型別，包括類別、結構 \(Struct\) 與陣列，都不能為 `const`。  建立在執行階段會初始化一次 \(例如在建構函式 \(Constructor\) 中\)，之後即不能變更的類別、結構或陣列時，請使用 [readonly](../../../csharp/language-reference/keywords/readonly.md) 修飾詞。  
  
 C\# 不支援 `const` 方法、屬性或事件。  
  
 列舉型別能讓您定義整數內建型別的具名常數 \(例如 `int`、`uint`、`long` 等等\)。  如需詳細資訊，請參閱 [enum](../../../csharp/language-reference/keywords/enum.md)。  
  
 常數必須初始化為宣告的型態。  例如：  
  
 [!code-cs[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/constants_1.cs)]  
  
 在這個範例中，常數 `months` 永遠會是 12，而且即使是類別本身也不能加以改變。  實際上，當編譯器在 C\# 原始程式檔中遇到常數識別項 \(例如 `months`\) 時，會直接將常值取代為其產生的中繼語言 \(Intermediate Language，IL\) 程式碼。  由於在執行階段，常數沒有相關聯的變數位址，參考因此無法傳遞 `const` 欄位，且在運算式中不能顯示為左值 \(L\-Value\)。  
  
> [!NOTE]
>  當您參考以其他程式碼 \(例如 DLL\) 定義的常數值時，請特別小心。  如果有新版本的 DLL 為常數定義了新值，您的程式仍會保留舊的常值，直到程式以新的版本重新編譯為止。  
  
 您可以同時宣告同一型別的多個常數，例如：  
  
 [!code-cs[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/constants_2.cs)]  
  
 如果不會造成循環參考，用來初始化常數的運算式也可參考其他的常數。  例如：  
  
 [!code-cs[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/constants_3.cs)]  
  
 常數可以標記為 [public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md) 或 `protected` `internal`。  這些存取修飾詞將定義類別使用者如何存取常數。  如需詳細資訊，請參閱 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 常數會當做[靜態](../../../csharp/language-reference/keywords/static.md)欄位存取，因為常數的值在型別的所有執行個體中都一樣。  您不能使用 `static` 關鍵字進行宣告。  不在定義常數之類別中的運算式，就必須使用類別名稱、句號和常數的名稱來存取常數。  例如：  
  
 [!code-cs[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/constants_4.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [類型](../../../csharp/programming-guide/types/index.md)   
 [readonly](../../../csharp/language-reference/keywords/readonly.md)   
 [C\# 的不變性 \- 第一部：不變性的種類](http://go.microsoft.com/fwlink/?LinkId=112379)