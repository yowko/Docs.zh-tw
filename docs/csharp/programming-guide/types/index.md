---
title: "類型 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "實值類型 [C#]"
  - "參考類型 [C#]"
  - "類型 [C#]"
  - "C# 語言，資料類型"
  - "一般類型系統 [C#]"
  - "資料類型 [C#]"
  - "C# 語言，類型"
  - "強式類型 [C#]"
ms.assetid: f782d7cc-035e-4500-b1b1-36a9881130ad
caps.latest.revision: 53
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 53
---
# 類型 (C# 程式設計手冊)
## 類型、變數和值  
 C\# 是一種強類型 \(Strongly Typed\) 語言。  任何變數和常數都有一個類型，與所有運算式都會評估為某個值一樣。  每個方法簽章都會為每個輸入參數和傳回值指定類型。  .NET Framework 類別庫 \(Class Library\) 定義了一組內建的數字類型 \(Numeric Type\) 和更複雜的類型，以表示各類邏輯建構，例如檔案系統、網路連線、集合物件和陣列物件，以及日期。  典型的 C\# 程式會使用類別庫的類型和使用者定義的類型，針對程式之問題網域的特定概念建立模型。  
  
 類型中儲存的資訊可以包含下列各項：  
  
-   類型的變數所需的儲存空間。  
  
-   它可以表示的最大值和最小值。  
  
-   其中內含的成員 \(方法、欄位、事件等等\)。  
  
-   其繼承的基底類型 \(Base Type\)。  
  
-   於執行階段將配置之變數的記憶體位置。  
  
-   允許的作業種類。  
  
 編譯器 \(Compiler\) 會使用類型資訊，確認程式碼中執行的所有作業是否符合「*類型安全*」\(Type Safe\)。  例如，如果變數的類型宣告為 [int](../../../csharp/language-reference/keywords/int.md)，編譯器就允許您將變數用來進行加減運算。  但如果嘗試對類型為 [bool](../../../csharp/language-reference/keywords/bool.md) 的變數執行加減運算，編譯器就會產生錯誤，如下列範例所示：  
  
 [!code-cs[csProgGuideTypes#42](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/index_1.cs)]  
  
> [!NOTE]
>  C 和 C\+\+ 開發人員請注意，C\# 中的 [bool](../../../csharp/language-reference/keywords/bool.md) 無法轉換為 [int](../../../csharp/language-reference/keywords/int.md)。  
  
 編譯器會將該類型資訊內嵌到可執行檔中，做為中繼資料 \(Metadata\)。  Common Language Runtime \(CLR\) 在執行階段會使用該中繼資料，進一步確保配置和回收記憶體時的類型安全。  
  
### 在變數宣告中指定類型  
 在程式中宣告變數或常數時，必須指定其類型，或者是使用 [var](../../../csharp/language-reference/keywords/var.md) 關鍵字讓編譯器推斷類型。  下列範例顯示的部分變數宣告，會使用內建數字類型 \(Numeric Type\) 以及複雜的使用者定義類型：  
  
 [!code-cs[csProgGuideTypes#36](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/index_2.cs)]  
  
 方法參數和傳回值的類型是在方法簽章中指定的。  下列簽章會說明需要以 [int](../../../csharp/language-reference/keywords/int.md) 做為輸入引數，並且會傳回字串的方法：  
  
 [!code-cs[csProgGuideTypes#35](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/index_3.cs)]  
  
 宣告變數後，就無法以新類型重新宣告，也不能指派與其宣告類型不相容的值給它。  例如，您不能宣告 [int](../../../csharp/language-reference/keywords/int.md)，然後將值為 [true](../../../csharp/language-reference/keywords/true-literal.md) 的布林值指派給它。  然而，值可以轉換為其他類型，例如，為這些值指派新變數，或將這些值當做方法的引數傳遞。  編譯器會自動執行不會導致資料遺失的「*類型轉換*」\(Type Conversion\)。  可能會導致資料遺失的轉換需要在原始程式碼中使用「*轉型*」\(Cast\)。  
  
 如需詳細資訊，請參閱 [轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)。  
  
## 內建類型  
 C\# 提供一組標準的內建數字類型，以表示整數、浮點數、布林運算式、文字字元、十進位值和其他資料類型。  同時也有內建的 `string` 和 `object` 類型。  您可以在任何 C\# 程式中使用這些項目。  如需內建類型的詳細資訊，請參閱[類型的參考表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)。  
  
## 自訂類型  
 您可以使用[結構](../../../csharp/language-reference/keywords/struct.md)、[類別](../../../csharp/language-reference/keywords/class.md)、[介面](../../../csharp/language-reference/keywords/interface.md)和[列舉](../../../csharp/language-reference/keywords/enum.md)建構函式建立自己的自訂類型。  .NET Framework 類別庫本身是由 Microsoft 所提供的自訂類型集合，您可以用於自己的應用程式中。  根據預設，您可以在任何 C\# 程式中使用類別庫內最常用到的類型。  對於其他類型，則只有在明確加入組件 \(其中已定義這些類型\) 的專案參考時，才可以使用這些類型。  在編譯器具有組件的參考後，您就可以在原始程式碼中，宣告組件中已宣告之類型的變數 \(和常數\)。  如需詳細資訊，請參閱 [.NET Framework 類別程式庫](http://go.microsoft.com/fwlink/?LinkID=217856)。  
  
## 一般類型系統  
 了解 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 中類型系統的兩個基本要點是非常重要的：  
  
-   它支援繼承 \(Inheritance\) 的準則。  類型可以衍生自其他類型 \(稱為「*基底類型*」\(Base Type\)\)。  衍生的類型會繼承基底類型的方法、屬性和其他成員，但是具有某些限制。  反之，基底類型可以衍生自某些其他類型，在這種情況下，衍生的類型會在其繼承階層架構 \(Inheritance Hierarchy\) 中，繼承兩個基底類型的成員。  包括如 <xref:System.Int32?displayProperty=fullName> \(C\# 關鍵字：[int](../../../csharp/language-reference/keywords/int.md)\) 這類的內建數字類型，所有的類型最終都是衍生自單一基底類型 \(Base Type\)，也就是 <xref:System.Object?displayProperty=fullName> \(C\# 關鍵字：[object](../../../csharp/language-reference/keywords/object.md)\)。  這個共同的類型階層架構稱為[一般類型系統](../../../standard/base-types/common-type-system.md) \(CTS\)。  如需 C\# 中繼承的詳細資訊，請參閱[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。  
  
-   CTS 中的每個類型都是以「*實值類型*」\(Value Type\) 或「*參考類型*」\(Reference Type\) 定義的。  這包含 .NET Framework 類別庫中所有的自訂類型，同時也包括您自己的使用者定義類型。  使用 [struct](../../../csharp/language-reference/keywords/struct.md) 關鍵字定義的類型是實值類型，而所有內建的數字類型是 `structs`。  使用 [class](../../../csharp/language-reference/keywords/class.md) 關鍵字定義的類型是參考類型。  參考類型和實值類型各具有不同的編譯時期規則和不同的執行階段行為。  
  
 下圖顯示 CTS 中實值類型和參考類型之間的關係。  
  
 ![實值類型和參考類型](../../../csharp/programming-guide/types/media/valuetypescts.png "ValueTypesCTS")  
CTS 中的實值類型和參考類型  
  
> [!NOTE]
>  您可以看到最常使用的類型全都已經整理在 <xref:System> 命名空間中。  然而，包含類型的命名空間，與其是否為實值類型和參考類型卻沒有關係。  
  
### 實值類型  
 實值類型衍生自 <xref:System.ValueType?displayProperty=fullName>，而該類型則衍生自 <xref:System.Object?displayProperty=fullName>。  衍生自 <xref:System.ValueType?displayProperty=fullName> 的類型，在 CLR 具有特別的行為。  實值類型變數直接包含其值，這表示在宣告任何內容的變數時，便會內嵌 \(Inline\) 配置記憶體。  沒有針對實值類型變數進行個別的堆積配置 \(Heap Allocation\) 或負荷記憶體回收。  
  
 實值類型有兩個分類：[結構](../../../csharp/language-reference/keywords/struct.md)和[列舉](../../../csharp/language-reference/keywords/enum.md)。  
  
 內建的數字類型 \(Numeric Type\) 都是結構 \(Struct\)，它們具有您可以存取的屬性和方法：  
  
```c#  
// Static method on type Byte.  
byte b = Byte.MaxValue;  
```  
  
 不過您要宣告及指派值給它們，就像它們是簡單的非彙總 \(Aggregate\) 類型一樣：  
  
```c#  
byte num = 0xA;  
int i = 5;  
char c = 'Z';  
```  
  
 實值類型是「*密封*」\(Sealed\) 的類型，舉例說明其意義，就是類型不能衍生自 <xref:System.Int32?displayProperty=fullName>，以及結構不能繼承自任何使用者定義的類別或結構，因為結構只能繼承自 <xref:System.ValueType?displayProperty=fullName>。  然而，結構可以實作一個或多個介面。  結構類型可以轉型為介面類型，這會導致 *Boxing* 作業執行，將結構包裝在 Managed 堆積 \(Heap\) 上的參考類型物件內。  將實值類型傳遞給採用 <xref:System.Object?displayProperty=fullName> 做為輸入參數的方法時，會發生 Boxing 作業。  如需詳細資訊，請參閱 [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)。  
  
 您可以使用 [struct](../../../csharp/language-reference/keywords/struct.md) 關鍵字，建立專屬自訂實值類型。  結構通常都是用來做為一小組相關變數的容器，如下列範例所示：  
  
 [!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/index_4.cs)]  
  
 如需結構的詳細資訊，請參閱[結構](../../../csharp/programming-guide/classes-and-structs/structs.md)。  如需 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 中實值類型的詳細資訊，請參閱[一般類型系統](../../../standard/base-types/common-type-system.md)。  
  
 實值類型的另一個分類是[列舉](../../../csharp/language-reference/keywords/enum.md)。  列舉可以定義一組具名的整數常數。  例如，.NET Framework 類別庫中的<xref:System.IO.FileMode?displayProperty=fullName> 列舉類型，包含一組用於指定檔案開啟方式的具名常數整數。  其定義方式如下列範例所示：  
  
 [!code-cs[csProgGuideTypes#44](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/index_5.cs)]  
  
 `System.IO.FileMode.Create` 常數的值為 2。  然而，對於我們閱讀原始程式碼而言，名稱比較具有意義，基於這個原因，最好是使用列舉類型取代常數常值數字。  如需詳細資訊，請參閱 <xref:System.IO.FileMode?displayProperty=fullName>。  
  
 所有的列舉都繼承自 <xref:System.Enum?displayProperty=fullName>，而該列舉類型則繼承自 <xref:System.ValueType?displayProperty=fullName>。  適用於結構的所有規則也適用於列舉。  如需列舉的詳細資訊，請參閱[列舉類型](../../../csharp/programming-guide/enumeration-types.md)。  
  
### 參考類型  
 定義為[類別](../../../csharp/language-reference/keywords/class.md)、[委派](../../../csharp/language-reference/keywords/delegate.md)、陣列或[介面](../../../csharp/language-reference/keywords/interface.md)的類型為「*參考類型*」\(Reference Type\)。  將變數宣告為參考類型時，變數在執行階段的一開始會包含 [null](../../../csharp/language-reference/keywords/null.md) 值，直到您使用 [new](../../../csharp/language-reference/keywords/new.md) 運算子明確建立物件的執行個體，或為其指派使用 `new, as shown in the following example:` 在其他地方所建立的物件為止，如下列範例所示：  
  
```c#  
MyClass mc = new MyClass();  
MyClass mc2 = mc;  
```  
  
 介面必須與實作該介面的類別物件一併初始化。  如果 `MyClass` 實作 `IMyInterface`，就表示您建立了 `IMyInterface` 的執行個體，如下列範例所示：  
  
```c#  
IMyInterface iface = new MyClass();  
```  
  
 建立物件時會將記憶體配置在 Managed 堆積上，而變數僅會持有物件的位置參考。  Managed 堆積上的類型在這兩種情況下都需要額外負荷，在由 CLR 自動記憶體管理功能進行配置時和回收時，後者即稱為「*記憶體回收*」\(Garbage Collection\)。  然而，記憶體回收也已經過高度最佳化，而且在大部分的案例中都不會建立效能問題。  如需記憶體回收的詳細資訊，請參閱[自動記憶體管理](../Topic/Automatic%20Memory%20Management.md)。  
  
 所有的陣列都是參考類型，即使其元素為實值類型也一樣。  陣列是隱含衍生自 <xref:System.Array?displayProperty=fullName> 類別的，但會搭配 C\# 所提供的簡化語法加以宣告和使用，如下列範例所示：  
  
 [!code-cs[csProgGuideTypes#45](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/index_6.cs)]  
  
 參考類型能夠完全支援繼承。  在您建立類別時，可以繼承自不是定義為[密封](../../../csharp/language-reference/keywords/sealed.md)的任何其他介面和類別，而其他的類別則可以繼承您的類別並覆寫您的虛擬方法。  如需如何建立自己的類別的詳細資訊，請參閱[類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)。  如需繼承和虛擬方法的詳細資訊，請參閱[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。  
  
## 常值的類型  
 C\# 中的常值會從編譯器接收類型。  您可以指定該如何套用數值常值的類型，方法是在數值尾端附加一個字母。  例如，若要指定將值 4.56 做為浮點數處理，則在數值後附加 "f" 或 "F"：`4.56f`。  如果沒有附加字母，編譯器就會推斷常值的類型。  如需哪些類型可以藉由使用字母後置字元進行指定的詳細資訊，請參閱[實值類型](../../../csharp/language-reference/keywords/value-types.md) 中個別類型的參考頁。  
  
 因為常值具有類型，而所有的類型最終都衍生自 <xref:System.Object?displayProperty=fullName>，所以您可以下列方式撰寫和編譯程式碼：  
  
 [!code-cs[csProgGuideTypes#37](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/index_7.cs)]  
  
## 泛型類型  
 您可以使用一個或多個「*類型參數*」\(Type Parameter\) 做為實際類型的替代符號 \(「*具象類型*」\(Concrete Type\)\) 來宣告類型，用戶端程式碼將會在建立類型的執行個體時提供這些替代符號。  此類類型稱為「*泛型類型*」\(Generic Type\)。  例如，.NET Framework 類型 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 具有一個類型參數，按照慣例，會命名為 *T*。  當您建立該類型的執行個體時，就要指定清單中內含的物件類型，例如字串。  
  
```c#  
List<string> strings = new List<string>();  
```  
  
 如果使用類型參數，便能重複使用相同類別來保存任何元素的類型，而不需要將每個項目都轉換為[物件](../../../csharp/language-reference/keywords/object.md)。  泛型集合類別稱為「*強類型集合*」\(Strongly\-Typed Collection\)，因為編譯器知道集合元素的特定類型。而且，假如您嘗試在上一個範例中將整數加入至 `strings` 物件，便可能會在編譯時期引發編譯器錯誤。  如需詳細資訊，請參閱 [泛型](../../../csharp/programming-guide/generics/index.md)。  
  
## 隱含類型、匿名類型和可為 Null 的類型  
 如先前所述，您可以藉由使用 [var](../../../csharp/language-reference/keywords/var.md) 關鍵字，隱含套用區域變數 \(但非類別成員\) 的類型。  變數仍然會在編譯時期接收到類型，但類型是由編譯器所提供的。  如需詳細資訊，請參閱 [隱含類型區域變數](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。  
  
 在有些案例中，對於沒有計劃要在方法界限外儲存或傳遞的一組簡單相關值而言，為其建立具名類型並不方便。  針對這個目的，您可以建立「*匿名類型*」\(Anonymous Type\)。  如需詳細資訊，請參閱[匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。  
  
 一般實值類型的值不能為 [null](../../../csharp/language-reference/keywords/null.md)。  然而藉由在類型後附加 `?`，即可以建立可為 Null 的實值類型。  例如，`int?` 這種 `int` 類型的值也可以是 [null](../../../csharp/language-reference/keywords/null.md)。  在 CTS 中，可為 Null 的類型都是泛型結構類型為 <xref:System.Nullable%601?displayProperty=fullName> 的執行個體。  當資料庫中的數值可能為 null 時，在與該資料庫進行資料來回傳遞時，可為 Null 的類型就特別地好用。  如需詳細資訊，請參閱 [可為 Null 的類型](../../../csharp/programming-guide/nullable-types/index.md)。  
  
## 相關章節  
 如需詳細資訊，請參閱下列主題：  
  
-   [轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)  
  
-   [使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md)  
  
-   [實值類型](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [參考類型](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
  
-   [泛型](../../../csharp/programming-guide/generics/index.md)  
  
-   [初探 Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214) 中的[變數與運算式](http://go.microsoft.com/fwlink/?LinkId=221228) \(英文\)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [XML 資料型別轉換](../Topic/Conversion%20of%20XML%20Data%20Types.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)