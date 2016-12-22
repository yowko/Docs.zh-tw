---
title: "字串 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "C# 語言, 字串"
  - "字串 [C#]"
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
caps.latest.revision: 41
caps.handback.revision: 41
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 字串 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

字串是型別 <xref:System.String> 的物件，其值為文字。  在內部，文字會儲存為 <xref:System.Char> 物件的循序唯讀集合。  C\# 字串尾端沒有 null 結尾字元，因此 C\# 字串可以包含任何數目的內嵌 null 字元 \('\\0'\)。  字串的 <xref:System.String.Length%2A> 屬性代表字串中包含的 `Char` 物件數，而不是 Unicode 字元數。  若要存取字串中個別的 Unicode 字碼指標，請使用 <xref:System.Globalization.StringInfo> 物件。  
  
## string 與System.String  
 C\# 中的 `string` 關鍵字是 <xref:System.String> 的別名。  因此，`String` 和 `string` 是對等用法，而您可以依偏好使用其中一個命名慣例。  `String` 類別提供許多方法，讓您可以安全地建立、處理和比較字串。  除此之外，C\# 語言可以多載部分運算子，進而簡化一般字串作業。  如需關鍵字的詳細資訊，請參閱 [字串](../../../csharp/language-reference/keywords/string.md)。  如需型別和其方法的詳細資訊，請參閱 <xref:System.String>。  
  
## 宣告和初始化字串  
 您可以使用許多方式宣告和初始化字串，如下列範例所示：  
  
 [!code-cs[csProgGuideStrings#1](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_1.cs)]  
  
 請注意，除了使用字元陣列初始化字串之外，其他情況下並不是使用 [new](../../../csharp/language-reference/keywords/new-operator.md) 運算子來建立字串物件。  
  
 使用 <xref:System.String.Empty> 常數值初始化字串，可以建立字串長度為零的新 <xref:System.String> 物件。  零長度字串的字串常值 \(String Literal\) 表示為 ""。  藉由使用 <xref:System.String.Empty> 值而非 [null](../../../csharp/language-reference/keywords/null.md) 來初始化字串，可以降低發生 <xref:System.NullReferenceException> 的機會。  請在嘗試存取字串值前，先使用 <xref:System.String.IsNullOrEmpty%28System.String%29> 方法驗證該值。  
  
## 字串物件的不變性  
 字串物件是「*不可變*」\(Immutable\)：一旦建立就無法變更。  看起來好像會修改字串的所有 <xref:System.String> 方法和 C\# 運算子，其實是傳回新字串物件的結果。  下列範例中，在串連 `s1` 和 `s2` 的內容以構成單一字串時，並不會修改這兩個原始字串。  `+=` 運算子會建立包含組合內容的新字串。  該新物件會指派給變數 `s1`，並會將指派給 `s1` 的原始物件釋放以供記憶體回收，這是因為沒有其他的變數會參考到該原始物件。  
  
 [!code-cs[csProgGuideStrings#2](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_2.cs)]  
  
 因為字串的「修改」實際上是新字串的建立，所以在建立字串參考時，您必須特別小心。  如果您建立字串的參考，然後「修改」原始字串，此參考將會繼續指向原始的物件，而不是指向修改該字串後所建立的新物件。  下列程式碼會說明這個行為：  
  
 [!code-cs[csProgGuideStrings#25](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_3.cs)]  
  
 如需如何依據修改建立新字串 \(例如對原始字串進行搜尋和取代的作業\) 的詳細資訊，請參閱 [如何：修改字串內容](../Topic/How%20to:%20Modify%20String%20Contents%20\(C%23%20Programming%20Guide\).md)。  
  
## 規則和逐字翻譯字串的常值  
 在必須內嵌 C\# 所提供的逸出字元 \(Escape Character\) 時，請使用規則字串常值，如下列範例所示：  
  
 [!code-cs[csProgGuideStrings#3](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_4.cs)]  
  
 在字串文字包含反斜線字元時，例如檔案路徑，為了方便好讀，請使用逐字翻譯字串。  因為逐字翻譯字串會保留字串文字中的新行字元，所以可以用來初始化多行字串。  請使用雙引號內嵌逐字翻譯字串中的引號。  下列範例顯示逐字翻譯字串的一些常見用法：  
  
 [!code-cs[csProgGuideStrings#4](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_5.cs)]  
  
## 字串逸出序列  
  
|逸出序列|字元名稱|Unicode 編碼|  
|----------|----------|----------------|  
|\\'|單引號|0x0027|  
|\\"|雙引號|0x0022|  
|\\\\|反斜線|0x005C|  
|\\0|Null|0x0000|  
|\\a|警示|0x0007|  
|\\b|退格鍵|0x0008|  
|\\f|換頁字元|0x000C|  
|\\n|新行|0x000A|  
|\\r|歸位字元|0x000D|  
|\\t|水平 Tab|0x0009|  
|\\U|Surrogate 字組的 Unicode 逸出序列|\\Unnnnnnnn|  
|\\u|Unicode 逸出序列|\\u0041 \= "A"|  
|\\v|垂直 Tab|0x000B|  
|\\x|類似 "\\u" 的 Unicode 逸出序列，但具有可變長度|\\x0041 \= "A"|  
  
> [!NOTE]
>  在編譯時期，逐字翻譯字串會轉換為一般字串再加上所有相同的逸出序列。  因此，如果在偵錯工具監看式視窗中檢視逐字翻譯字串，就會看到編譯器加入的逸出字元，而不是原始程式碼中的逐字翻譯版本。  例如，逐字翻譯字串 @"C:\\files.txt" 在監看式視窗中會顯示為 "C:\\\\files.txt"。  
  
## 格式字串  
 格式字串 \(Format String\) 這種字串的內容，可以在執行階段動態決定。  建立格式字串的方式，是藉由使用靜態 <xref:System.String.Format%2A> 方法，並以大括號內嵌要在執行階段以其他值取代的替代符號 \(Placeholder\)。  下列範例會使用格式字串，以輸出迴圈 \(Loop\) 中每次反覆運算的結果。  
  
 [!code-cs[csProgGuideStrings#26](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_6.cs)]  
  
 <xref:System.Console.WriteLine%2A> 方法有一個多載會採用格式字串做為參數。  因此，您只要內嵌格式字串常值，而不用明確呼叫方法。  然而，如果是使用 <xref:System.Diagnostics.Trace.WriteLine%2A> 方法在 Visual Studio \[**輸出**\] 視窗中顯示偵錯輸出，則必須明確呼叫 <xref:System.String.Format%2A> 方法，因為 <xref:System.Diagnostics.Trace.WriteLine%2A> 只接受字串，而非格式字串。  如需格式字串的詳細資訊，請參閱[格式化類型](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md)。  
  
## 子字串  
 子字串是包含在字串中的任何字元序列。  使用 <xref:System.String.Substring%2A> 方法可以從原始字串的一部分建立新字串。  藉由使用 <xref:System.String.IndexOf%2A> 方法，您可以搜尋子字串的一個或多個出現項目。  使用 <xref:System.String.Replace%2A> 方法則會以新字串取代指定子字串的所有出現項目。  跟 <xref:System.String.Substring%2A> 方法一樣，<xref:System.String.Replace%2A> 實際上會傳回新字串，而不會修改原始字串。  如需詳細資訊，請參閱 [如何：使用字串方法搜尋字串](../../../csharp/programming-guide/strings/how-to-search-strings-using-string-methods.md) 和 [如何：修改字串內容](../Topic/How%20to:%20Modify%20String%20Contents%20\(C%23%20Programming%20Guide\).md)。  
  
 [!code-cs[csProgGuideStrings#7](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_7.cs)]  
  
## 存取個別字元  
 您可以使用陣列標記法搭配索引值，取得個別字元的唯讀存取，如下列範例所示：  
  
 [!code-cs[csProgGuideStrings#9](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_8.cs)]  
  
 在修改字串中的個別字元時，如果 <xref:System.String> 方法沒有提供您必須擁有的功能，則可以使用 <xref:System.Text.StringBuilder> 物件「就地」修改個別字元，然後再使用 <xref:System.Text.StringBuilder> 方法建立新字串以儲存結果。  在下列範例中，假設您必須以特殊方式修改原始字串，並儲存該結果供日後使用：  
  
 [!code-cs[csProgGuideStrings#8](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_9.cs)]  
  
## Null 字串和空字串  
 空字串是 <xref:System.String?displayProperty=fullName> 物件的執行個體 \(Instance\)，其中包含零個字元。  空字串經常用於各種程式設計案例，以代表空白的文字欄位。  您可以在空字串上呼叫方法，因為其為有效的 <xref:System.String?displayProperty=fullName> 物件。  空字串的初始化方式如下：  
  
```  
string s = String.Empty;  
```  
  
 相較之下，null 字串不會參考 <xref:System.String?displayProperty=fullName> 物件的執行個體，嘗試在 null 字串上呼叫方法會導致 <xref:System.NullReferenceException>。  不過，您可以使用 null 字串與其他字串進行串連和比較作業。  下列範例說明參考 null 字串會不會導致例外狀況 \(Exception\) 擲回的一些案例：  
  
 [!code-cs[csProgGuideStrings#27](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_10.cs)]  
  
## 使用 StringBuilder 快速建立字串  
 .NET 的字串作業是經過高度最佳化的，而且在絕大部分的情況下不會大幅影響到效能。  然而，在有些案例下的字串作業可能會影響到效能，例如會執行數千百次的緊密迴圈。  如果程式會執行許多字串處理，<xref:System.Text.StringBuilder> 類別可以建立字串緩衝區以提供更好的效能。  <xref:System.Text.StringBuilder> 字串也可以讓您重新指派內建字串資料型別不支援的某些個別字元。  例如，這個程式碼會在不建立新字串的情況下變更字串內容：  
  
 [!code-cs[csProgGuideStrings#20](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_11.cs)]  
  
 在這個範例中，會使用 <xref:System.Text.StringBuilder> 物件從一組數字型別 \(Numeric Type\) 中建立字串：  
  
 [!code-cs[csProgGuideStrings#15](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_12.cs)]  
  
## 字串、擴充方法和 LINQ  
 因為 <xref:System.String> 型別會實作 <xref:System.Collections.Generic.IEnumerable%601>，您可以對字串使用 <xref:System.Linq.Enumerable> 類別中定義的擴充方法。  為了看起來不會過於雜亂，<xref:System.String> 型別的 IntelliSense 會排除這些方法，但是，您仍然可以使用這些方法。  您也可以對字串使用 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] 查詢運算式。  如需詳細資訊，請參閱 [LINQ and Strings](../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)。  
  
## 相關主題  
  
|主題|描述|  
|--------|--------|  
|[如何：修改字串內容](../Topic/How%20to:%20Modify%20String%20Contents%20\(C%23%20Programming%20Guide\).md)|提供說明如何修改字串內容的程式碼範例。|  
|[如何：串連多個字串](../../../csharp/programming-guide/strings/how-to-concatenate-multiple-strings.md)|說明如何使用 `+` 運算子和 `Stringbuilder` 類別，於編譯時期和執行階段聯結字串。|  
|[如何：比較字串](../../../csharp/programming-guide/strings/how-to-compare-strings.md)|說明如何執行字串的序數比較。|  
|[如何：使用 String.Split 剖析字串 ](../../../csharp/programming-guide/strings/how-to-parse-strings-using-string-split.md)|包含說明如何使用 `String.Split` 方法剖析字串的程式碼範例。|  
|[如何：使用字串方法搜尋字串](../../../csharp/programming-guide/strings/how-to-search-strings-using-string-methods.md)|說明如何使用特定方法搜尋字串。|  
|[如何：使用規則運算式搜尋字串](../../../csharp/programming-guide/strings/how-to-search-strings-using-regular-expressions.md)|說明如何使用規則運算式搜尋字串。|  
|[如何：判斷字串是否表示數值](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)|說明如何安全剖析字串，判斷字串是否包含有效的數值。|  
|[如何：將字串轉換為 DateTime](../../../csharp/programming-guide/strings/how-to-convert-a-string-to-a-datetime.md)|說明如何將字串 \(例如 "01\/24\/2008"\) 轉換為 <xref:System.DateTime?displayProperty=fullName> 物件。|  
|[基本字串作業](../Topic/Basic%20String%20Operations%20in%20the%20.NET%20Framework.md)|提供主題連結，這些主題會使用 <xref:System.String?displayProperty=fullName> 和 <xref:System.Text.StringBuilder?displayProperty=fullName> 方法來執行基本字串作業。|  
|[剖析字串](../Topic/Parsing%20Strings%20in%20the%20.NET%20Framework.md)|描述如何將字元或空格插入字串中。|  
|[比較字串](../Topic/Comparing%20Strings%20in%20the%20.NET%20Framework.md)|包含如何比較字串的詳細資訊並提供 C\# 和 Visual Basic 的範例。|  
|[使用 StringBuilder 類別](../Topic/Using%20the%20StringBuilder%20Class%20in%20the%20.NET%20Framework.md)|描述如何使用 <xref:System.Text.StringBuilder> 類別建立和修改動態字串物件。|  
|[LINQ and Strings](../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)|提供如何使用 LINQ 查詢執行各種字串作業的詳細資訊。|  
|[C\# 程式設計手冊](../../../csharp/programming-guide/index.md)|提供說明 C\# 中程式設計建構的主題連結。|  
  
## 精選書籍章節  
 [更多關於變數](完整.嗎？LinkId%20=%20221230) 在 [開頭 2010 視覺化 C\#](完整.嗎？LinkId%20=%20221214)