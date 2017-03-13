---
title: "部分類別和方法 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 部分類別與方法"
  - "部分類別 [C#]"
  - "部分方法 [C#]"
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
caps.latest.revision: 35
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 35
---
# 部分類別和方法 (C# 程式設計手冊)
[類別](../../../csharp/language-reference/keywords/class.md) \(Class\)、[結構](../../../csharp/language-reference/keywords/struct.md) \(Struct\)、[介面](../../../csharp/language-reference/keywords/interface.md)或方法的定義，都可以分割為兩個或兩個以上的原始程式檔 \(Source File\)。  每個原始程式檔都包含型別或方法定義的區段，而且所有部分會在應用程式進行編譯時組合起來。  
  
## 部分類別  
 適合分割類別定義的情況包括：  
  
-   在處理大型專案時，將類別分散到個別的檔案，即可讓多位程式設計人員同時在該專案上進行運作。  
  
-   使用自動產生的原始檔時，可以將程式碼加入至類別中，而無須重新建立原始程式檔。  Visual Studio 會使用這種方法建立 Windows Form、Web 服務包裝函式程式碼等。  您可以建立使用這些類別的程式碼，而不需要修改 Visual Studio 所建立的檔案。  
  
-   若要分割類別定義，請使用 [partial](../../../csharp/language-reference/keywords/partial-type.md) 關鍵字修飾詞 \(Modifier\)，如下所示：  
  
 [!code-cs[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]  
  
 `partial` 關鍵字表示可定義於命名空間 \(Namespace\) 中之類別、結構或介面的其他組件。  所有組件都必須使用 `partial` 關鍵字。  所有的組件必須都可在編譯時期提供使用，才能夠形成最後的型別。  所有的組件都必須有相同的存取範圍，例如 `public`、`private` 及其他。  
  
 如果有任何組件宣告為抽象，整個型別就會被視為抽象。  如果有任何組件宣告為密封，整個型別就會被視為密封。  如有任何組件宣告為基底型別 \(Base Type\)，整個型別就會繼承該類別。  
  
 所有指定基底類別 \(Base Class\) 的組件都必須一致，不過省略基底類別的組件仍會繼承該基底型別。  這些組件可以指定不同的基底介面，而最後的型別會實作由所有的部分宣告列出的任何介面。  在部分定義中所宣告的任何類別、結構或介面成員，都可供其他所有組件使用。  最後型別會是編譯時期中所有組件的組合。  
  
> [!NOTE]
>  委派或列舉型別宣告中不能使用 `partial` 修飾詞。  
  
 下列範例會示範巢狀型別可以是 partial，即使這些巢狀型別所包含其中的型別並非 partial。  
  
 [!code-cs[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]  
  
 在編譯時期，會合併部分型別定義的屬性。  例如，請參考下列宣告：  
  
 [!code-cs[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]  
  
 它們相當於下列宣告：  
  
 [!code-cs[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]  
  
 以下是所有部分型別定義的合併結果：  
  
-   XML 註解  
  
-   介面  
  
-   泛型型別參數屬性  
  
-   類別屬性  
  
-   members  
  
 例如，請參考下列宣告：  
  
 [!code-cs[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]  
  
 它們相當於下列宣告：  
  
 [!code-cs[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]  
  
### 限制  
 下面是要在使用部分類別定義時遵守的一些規則：  
  
-   組成相同型別的所有部分型別定義，都必須由 `partial` 修飾。  例如，下列類別宣告將會產生錯誤：  
  
     [!code-cs[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]  
  
-   `partial` 修飾詞只能緊接在關鍵字 `class`、`struct` 或 `interface` 前面。  
  
-   巢狀的部分型別允許出現在部分型別定義中，如下列範例所示，  
  
     [!code-cs[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]  
  
-   組成相同型別的所有部分型別定義，都必須在同一組件和模組 \(.exe 或 .dll 檔案\) 內定義。  部分定義無法跨多個模組。  
  
-   類別名稱和泛型型別參數在所有部分型別定義中都必須相符。  泛型型別可以是部分型別。  每個部分宣告都必須以相同順序使用相同的參數名稱。  
  
-   下列關鍵字在部分型別定義中是選擇性項目，但如果出現在某個部分型別定義內，則不可與相同型別的另一個部分定義所指定的關鍵字衝突：  
  
    -   [public](../../../csharp/language-reference/keywords/public.md)  
  
    -   [private](../../../csharp/language-reference/keywords/private.md)  
  
    -   [protected](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [internal](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   Base Class \- 基底類別  
  
    -   [new](../../../csharp/language-reference/keywords/new.md) 修飾詞 \(巢狀組件\)  
  
    -   泛型條件約束  
  
         如需詳細資訊，請參閱 [類型參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)。  
  
## 範例 1  
  
### 描述  
 在下列範例中，`CoOrds` 類別的欄位和建構函式 \(Constructor\) 會宣告於一個部分類別定義中，而其成員 `PrintCoOrds` 則宣告於另外一個部分類別定義中。  
  
### 程式碼  
 [!code-cs[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]  
  
## 範例 2  
  
### 描述  
 下列範例顯示您也可以開發部分結構和介面。  
  
### 程式碼  
 [!code-cs[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]  
  
## 部分方法  
 部分類別或結構可能會包含部分方法。  類別的其中一個部分會包含該方法的簽章。  在相同組件或其他組件中可能會定義選擇性的實作 \(Implementation\)。  如果沒有提供實作，該方法和該方法的所有呼叫便會在編譯時期移除。  
  
 部分方法讓其中一個類別部分的實作器能夠定義類似事件的方法。  其他類別部分的實作器則可判斷是否要實作該方法。  如果沒有實作方法，編譯器 \(Compiler\) 便會移除方法簽章和該方法的所有呼叫。  方法呼叫，包括任何會因呼叫中對引述的評估而發生的結果，在執行階段皆沒有任何效果。  因此，即使沒有提供實作，在部分類別中的任何程式碼都可以自由使用部分方法。  在方法有進行呼叫但未加以實作的情況下，並不會造成編譯時期或執行階段錯誤。  
  
 部分方法特別適合用來自訂產生的程式碼。  它們允許方法名稱和簽章進行保留，以便產生的程式碼可以呼叫該方法，但是開發人員仍可自行決定是否要實作該方法。  就像部分類別，部分方法讓程式碼產生器所產生的程式碼，以及人類開發人員所建立的程式碼能夠一起運作，而不會產生執行階段成本。  
  
 部分方法宣告包含了兩個組件：定義和實作。  這些組件可能位於部分類別的個別部分，或是位於相同部分。  如果此時沒有實作宣告，編譯器就會最佳化改變定義宣告和該方法的所有呼叫。  
  
```  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   部分方法宣告一定會以內容關鍵字 [partial](../../../csharp/language-reference/keywords/partial-type.md) 為開頭，而且此方法一定會傳回 [void](../../../csharp/language-reference/keywords/void.md)。  
  
-   部分方法可以有 [ref](../../../csharp/language-reference/keywords/ref.md) 參數，但是不能有 [out](../../../csharp/language-reference/keywords/out.md) 參數。  
  
-   部分方法都是隱含 [private](../../../csharp/language-reference/keywords/private.md)，因此不能是 [virtual](../../../csharp/language-reference/keywords/virtual.md)。  
  
-   部分方法不能是 [extern](../../../csharp/language-reference/keywords/extern.md)，這是因為主體的存在與否會決定它們要進行定義或是實作。  
  
-   部分方法可以有 [static](../../../csharp/language-reference/keywords/static.md) 和 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 修飾詞。  
  
-   部分方法可以是泛型的。  條件約束會在定義部分方法宣告時提出，而且可以選擇性地在實作一個宣告時重複。  實作宣告和定義宣告時的參數名稱和型別參數名稱並不一定要完全相同。  
  
-   您可以將已經定義與實作的部分方法設定為 [delegate](../../../csharp/language-reference/keywords/delegate.md)，但是對於只有經過定義的方法，則無法如此設定。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別](../../../csharp/programming-guide/classes-and-structs/classes.md)   
 [結構](../../../csharp/programming-guide/classes-and-structs/structs.md)   
 [介面](../../../csharp/programming-guide/interfaces/index.md)   
 [partial \(類型\)](../../../csharp/language-reference/keywords/partial-type.md)