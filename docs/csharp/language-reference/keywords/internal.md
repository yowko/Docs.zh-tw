---
title: "internal (C# 參考) | Microsoft Docs"
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
  - "internal_CSharpKeyword"
  - "internal"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "internal 關鍵字 [C#]"
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# internal (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`internal` 關鍵字是型別和型別成員 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) 。  內部型別或內部成員只能在相同組件中的檔案內存取，如本範例所示：  
  
```  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  
  
 具有存取修飾詞 `protected internal` 的型別或成員可以從目前組件中存取，或是透過衍生自包含類別的型別存取。  
  
 如需 `internal` 與其他存取修飾詞的比較，請參閱[存取層級](../../../csharp/language-reference/keywords/accessibility-levels.md) 和[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 如需組件的詳細資訊，請參閱[組件和全域組件快取](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 內部存取的常見用法是以元件為基礎的開發上，因為它使得元件群組以私用的方式相互合作，無須公開其他部分的應用程式碼。  例如，建立圖形使用者介面的架構可以提供 `Control` 和 `Form` 類別，這兩個類別會以內部存取的方式使用成員相互合作。  因為這些成員是內部的，他們不公開給使用架構的程式碼。  
  
 在定義型別或成員的組件外部，以內部存取方式來參考此型別或成員是錯誤的做法。  
  
## 範例  
 這個範例包含兩個檔案，`Assembly1.cs` 和 `Assembly1`\_`a.cs`。  第一個檔案包含內部基底類別，`BaseClass`。  如果在第二個檔案中嘗試產生 \(Instantiate\) `BaseClass`，將會產生錯誤。  
  
```  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## 範例  
 在這個範例中，請使用在範例 1 中所用的相同檔案，並將 `BaseClass` 的存取範圍層級變更為 `public`。  同時將成員 `IntM` 的存取範圍層級變更為 `internal`。  如此一來您可以將類別具現化，但無法存取內部成員。  
  
```  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [存取層級](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)