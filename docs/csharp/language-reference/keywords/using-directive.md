---
title: "using 指示詞 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "using 指示詞 [C#]"
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# using 指示詞 (C# 參考)
`using` 指示詞有三個用途：  
  
-   若要允許在命名空間中使用類型，使得您不需限定在該命名空間中使用的類型：  
  
    ```c#  
    using System.Text;  
    ```  
  
-   若要允許您存取類型的靜態成員，而不需以類型名稱限定存取：  
  
    ```c#  
    using static System.Math;  
    ```  
  
-   若要建立命名空間或類型的別名。  這稱為 *using alias 指示詞*。  
  
    ```c#  
    using Project = PC.MyCompany.Project;  
    ```  
  
 `using` 關鍵字也用來建立 *using 陳述式*，協助確保能夠正確處理 <xref:System.IDisposable> 物件 \(例如檔案和字型\)。  如需詳細資訊，請參閱[使用陳述式](../../../csharp/language-reference/keywords/using-statement.md)。  
  
## 使用靜態類型  
 您可以存取類型的靜態成員，而不需以類型名稱限定存取：  
  
```c#  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
  
```  
  
 `Using static` 只會匯入指定的類型中宣告的可存取靜態成員和巢狀類型。  不會匯入繼承的成員。  您可以使用 using 靜態指示詞從任何具名類型匯入，包括 Visual Basic 模組。  如果 F\# 最上層函式出現在中繼資料中，做為具名類型的靜態成員，其名稱是有效的 C\# 識別項，則可以匯入 F\# 函式。  
  
 `Using static` 讓您在可供擴充方法查閱使用的指定類型中宣告擴充方法。  不過，擴充方法的名稱不會匯入程式碼中未限定參考的範圍。  
  
 在相同編譯單位或命名空間中透過不同 using 靜態指示詞從不同的類型匯入、具有相同名稱的方法會形成方法群組。  這些方法群組內的多載解析會遵循一般的 C\# 規則。  
  
## 備註  
 `using` 指示詞的範圍僅限於其出現的檔案。  
  
 建立 `using` 別名，讓您更輕鬆地將識別項限定在命名空間或類型。  using alias 指示詞的右邊一律必須是完整限定的類型，不論在它前面的 using 指示詞為何。  
  
 建立 `using` 指示詞，以在命名空間中使用類型，而無需指定命名空間。  `using` 指示詞不會授予巢狀於您指定的命名空間中的任何命名空間的存取權。  
  
 命名空間有兩種類型：使用者定義和系統定義。  使用者定義的命名空間是在程式碼中定義的命名空間。  如需系統定義的命名空間的清單，請參閱 [.NET Framework 類別庫](http://go.microsoft.com/fwlink/?LinkID=227195)。  
  
 如需參考其他組件中的方法的範例，請參閱[建立和使用 C\# DLL](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 範例 1  
  
### 描述  
 下列範例示範如何定義和使用命名空間的 `using` 別名：  
  
### 程式碼  
 [!code-cs[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
### 註解  
 using alias 指示詞的右邊不能有開放式的泛型類型。  例如，您無法為 List\<T\> 建立 using alias，但是您可以為 List\<int\> 建立。  
  
## 範例 2  
  
### 描述  
 下列範例示範如何定義類別的 `using` 指示詞和 `using` 別名：  
  
### 程式碼  
 [!code-cs[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [使用命名空間](../../../csharp/programming-guide/namespaces/using-namespaces.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [命名空間關鍵字](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [命名空間](../../../csharp/programming-guide/namespaces/index.md)   
 [Using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)