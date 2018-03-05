---
title: "C# 編碼慣例 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a8806ddb0a9cc62fe68dc9d558917ee2d532e7f
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/24/2018
---
# <a name="c-coding-conventions-c-programming-guide"></a>C# 編碼慣例 (C# 程式設計手冊)
 編碼慣例有下列用途：  
  
-   建立外觀一致的程式碼，讓讀者可以專注於內容，而非版面配置。  
  
-   讓讀者可以依據先前的經驗做出假設，更快速地了解程式碼。  
  
-   有助於複製、變更及維護程式碼。  
  
-   示範 C# 的最佳作法。  

 Microsoft 會利用本主題中的指導方針來開發範例與文件。  
  
## <a name="naming-conventions"></a>命名規範  
  
-   在不包含 [using 指示詞](../../../csharp/language-reference/keywords/using-directive.md)的簡短範例中，使用命名空間限定。 如果您知道專案中預設會匯入命名空間，則無須完整限定該命名空間的名稱。 如果限定的名稱太長無法顯示在同一行，則可以在點 (.) 之後中斷名稱，如下範例所示。  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   您無須變更使用 Visual Studio 設計工具所建立的物件之名稱，使其符合其他指導方針。  
  
## <a name="layout-conventions"></a>版面配置慣例  
 好的版面配置使用格式設定，來強調程式碼的結構，並讓程式碼更易於閱讀。 Microsoft 範例遵循以下慣例：  
  
-   使用預設程式碼編輯器設定 (智慧型縮排、四個字元縮排、定位點儲存為空格)。 如需詳細資訊，請參閱[選項、文字編輯器、C#、格式](/visualstudio/ide/reference/options-text-editor-csharp-formatting)。  
  
-   每行只撰寫一個陳述式。  
  
-   每行只撰寫一個宣告。  
  
-   如果連續行不會自動縮排，則縮排一個定位停駐點 (四個空格)。  
  
-   在方法定義與屬性定義之間新增至少一個空白行。  
  
-   使用括號清楚分隔運算式中的子句，如下列程式碼所示。  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a>註解慣例  
  
-   將註解置於單獨的一行，不在程式碼行結尾處。  
  
-   以大寫字母開始註解文字。  
  
-   以句號結束註解文字。  
  
-   註解分隔符號 (//) 與註解文字之間插入一個空格，如下列範例所示。  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   不要在註解周圍建立格式化的星號區塊。  
  
## <a name="language-guidelines"></a>語言指導方針  
 下列各節說明 C# 小組在準備程式碼範例時應遵循的作法。  
  
### <a name="string-data-type"></a>String 資料類型  
  
-   使用 `+` 運算子串連短字串，如下列程式碼所示。  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   若要在迴圈中附加字串，特別是正在使用大量文字時，請使用 <xref:System.Text.StringBuilder> 物件。  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a>隱含類型區域變數  
  
-   如果區域變數的類型明顯來自指派的右側，或精確類型並不重要，請針對該變數使用[隱含類型](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   當類型不是明顯來自指派的右側時，請不要使用 [var](../../../csharp/language-reference/keywords/var.md)。  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   請勿依賴變數名稱，指定變數的類型。 有可能會不正確。  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   避免使用 `var` 取代 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)。  
  
-   使用隱含類型，確定 [for](../../../csharp/language-reference/keywords/for.md) 和 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 迴圈中迴圈變數的類型。  
  
     下列範例在 `for` 陳述式中使用隱含類型。  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     下列範例在 `foreach` 陳述式中使用隱含類型。  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a>不帶正負號的資料類型  
  
-   一般而言，請使用 `int` 而非不帶正負號的類型。 `int` 的使用在 C# 中非常普遍，當您使用 `int` 時，可更易於與其他程式庫互動。  
  
### <a name="arrays"></a>陣列  
  
-   當您在宣告行上初始化陣列時，請使用簡潔的語法。  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a>委派  
  
-   您可以使用簡潔的語法，建立委派類型的執行個體。  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>例外狀況處理中的 try-catch 和 using 陳述式  
  
-   針對大部分例外狀況處理，請使用 [try-catch](../../../csharp/language-reference/keywords/try-catch.md) 陳述式。  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   使用 C# [using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)，可簡化程式碼。 如果您有 [try-finally](../../../csharp/language-reference/keywords/try-finally.md) 陳述式，而其中 `finally` 區塊內唯一的程式碼是 <xref:System.IDisposable.Dispose%2A> 方法的呼叫，則請改用 `using` 陳述式。  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a>&& 和 &#124;&#124; 運算子  
  
-   為避免發生例外狀況，並略過不必要的比較來提升效能，請在執行比較時使用 [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) 而非 [&](../../../csharp/language-reference/operators/and-operator.md)，並使用 [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) 而非 [&#124;](../../../csharp/language-reference/operators/or-operator.md)，如下列範例所示。  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a>New 運算子  
  
-   使用物件執行個體化的簡潔形式，搭配隱含類型，如下宣告所示。  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     前一行相當於下列宣告。  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   使用物件初始設定式，簡化物件的建立。  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a>事件處理  
  
-   如果要定義稍後不需要移除的事件處理常式，請使用 Lambda 運算式。  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a>靜態成員  
  
-   使用類別名稱 *ClassName.StaticMember*，呼叫 [static](../../../csharp/language-reference/keywords/static.md) 成員。 這種作法可讓靜態存取更加清晰，從而讓程式碼更易於閱讀。  請勿使用衍生類別的名稱，限定在基底類別中定義的靜態成員。  編譯該程式碼時，如果將具有相同名稱的靜態成員加入衍生類別，則會破壞程式碼的清楚程度，且程式碼之後可能會在中斷。  
  
### <a name="linq-queries"></a>LINQ 查詢  
  
-   請為查詢變數使用有意義的名稱。 下列範例對位於西雅圖的客戶，使用 `seattleCustomers`。  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   使用別名，確保匿名類型的屬性名稱使用 Pascal 大小寫慣例，大寫正確。  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   當結果中的屬性名稱可能會造成混淆時，請重新命名屬性。 例如，如果查詢傳回了客戶名稱與經銷商 ID，但沒有在結果在將它們保留為 `Name` 和 `ID`，請對它們重新命名，以釐清 `Name` 是客戶的名稱，而 `ID` 是經銷商的 ID。  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   在查詢變數和範圍變數的宣告中使用隱含類型。  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   在 [from](../../../csharp/language-reference/keywords/from-clause.md) 子句下對齊查詢子句，如先前範例所示。  
  
-   在其他查詢子句前，使用 [where](../../../csharp/language-reference/keywords/where-clause.md) 子句以確保之後的查詢子句，會對已經過篩選而減少數量的一組資料進行操作。  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   使用多個 `from` 子句來存取內部集合，而非使用 [join](../../../csharp/language-reference/keywords/join-clause.md) 子句。 例如，`Student` 物件的集合可能每一個都包含測驗分數的集合。 執行下列查詢時，會傳回每個超過 90 的分數，以及取得該分數的學生姓氏。  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a>安全性  
 請遵循[安全程式碼撰寫方針](../../../standard/security/secure-coding-guidelines.md)中的指引。  
  
## <a name="see-also"></a>請參閱  
 [Visual Basic 編碼慣例](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 [安全程式碼撰寫方針](../../../standard/security/secure-coding-guidelines.md)
