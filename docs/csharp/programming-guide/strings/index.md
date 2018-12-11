---
title: 字串 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: 7034d37c141d79301bf108b9e7b41ab3e27e2572
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143918"
---
# <a name="strings-c-programming-guide"></a>字串 (C# 程式設計手冊)
字串是 <xref:System.String> 類型的物件，其值為文字。 就內部而言，文字會儲存為 <xref:System.Char> 物件的循序唯讀集合。 C# 字串的結尾沒有終止的 Null 字元，因此 C# 字串可以包含任何數目的內嵌 Null 字元 ('\0')。 字串的 <xref:System.String.Length%2A> 屬性代表它包含的 `Char` 物件數目，而非 Unicode 字元的數目。 若要存取字串中的個別 Unicode 字碼指標，請使用 <xref:System.Globalization.StringInfo> 物件。  
  
## <a name="string-vs-systemstring"></a>字串與System.String  
 在 C# 中，`string` 關鍵字是 <xref:System.String> 的別名。 因此 `String` 和 `string` 為相等，而您可以使用您偏好的命名慣例。 `String` 類別提供許多方法來安全地建立、操作和比較字串。 此外，C# 語言會多載一些運算子，以簡化常見的字串作業。 如需關鍵字的詳細資訊，請參閱[字串](../../../csharp/language-reference/keywords/string.md)。 如需類型和其方法的詳細資訊，請參閱 <xref:System.String>。  
  
## <a name="declaring-and-initializing-strings"></a>宣告並初始化字串  
 您可以透過多種方式宣告並初始化字串，如下列範例所示：  
  
 [!code-csharp[csProgGuideStrings#1](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_1.cs)]  
  
 請注意，除了使用字元陣列初始化字串以外，您不能使用 [new](../../../csharp/language-reference/keywords/new-operator.md) 運算子建立字串物件。  
  
 使用 <xref:System.String.Empty> 常數值初始化字串，以建立字串長度為零的新 <xref:System.String> 物件。 零長度字串的字串常值表示法是 ""。 使用 <xref:System.String.Empty> 值初始化字串，而非 [null](../../../csharp/language-reference/keywords/null.md)，即可降低發生 <xref:System.NullReferenceException> 的機會。 使用靜態 <xref:System.String.IsNullOrEmpty%28System.String%29> 方法，先驗證字串的值，再嘗試進行存取。  
  
## <a name="immutability-of-string-objects"></a>字串物件的不變性  
 字串物件為「不可變」：它們在建立之後將無法變更。 所有看似會修改字串的 <xref:System.String> 方法和 C# 運算子，實際上會以新的字串物件傳回結果。 在下列範例中，當 `s1` 和 `s2` 的內容串連以組成單一字串時，兩個原始字串將不會被修改。 `+=` 運算子會建立新的字串，其中包含結合的內容。 新的物件會指派給變數 `s1`，而先前指派給 `s1` 的原始物件將會被釋放以進行記憶體回收，因為已經沒有其他具有其參考的變數。  
  
 [!code-csharp[csProgGuideStrings#2](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_2.cs)]  
  
 因為對字串的「修改」實際上是建立新的字串，當您建立對字串的參考時，必須特別謹慎。 如果您建立對字串的參考，然後「修改」原始字串，該參考將會繼續指向原始物件，而非修改字串時所建立的新物件。 下列程式碼說明這個行為：  
  
 [!code-csharp[csProgGuideStrings#25](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_3.cs)]  
  
 如需如何建立以修改為基礎 (例如原始字串上的搜尋與取代作業) 之新字串的詳細資訊，請參閱[如何：修改字串內容](../../how-to/modify-string-contents.md)。  
  
## <a name="regular-and-verbatim-string-literals"></a>一般和逐字字串常值  
 當您必須內嵌由 C# 所提供的逸出字元時，請使用一般字串常值，如下列範例所示︰  
  
 [!code-csharp[csProgGuideStrings#3](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_4.cs)]  
  
 當字串文字包含反斜線字元時 (例如檔案路徑)，基於方便性和可讀性，請使用逐字字串。 因為逐字字串會將新行字元保留為字串文字的一部分，因此可以將它們用來初始化多行字串。 使用雙引號在逐字字串中內嵌引號。 下列範例示範一些逐字字串的常見用法︰  
  
 [!code-csharp[csProgGuideStrings#4](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_5.cs)]  
  
## <a name="string-escape-sequences"></a>字串逸出序列  
  
|逸出序列|字元名稱|Unicode 編碼|  
|---------------------|--------------------|----------------------|  
|\\'|單引號|0x0027|  
|\\"|雙引號|0x0022|  
|\\\\ |反斜線|0x005C|  
|\0|Null|0x0000|  
|\a|警示|0x0007|  
|\b|退格鍵|0x0008|  
|\f|換頁字元|0x000C|  
|\n|換行|0x000A|  
|\r|歸位字元|0x000D|  
|\t|水平 Tab|0x0009|  
|\U|Surrogate 字組的 Unicode 逸出序列。|\Unnnnnnnn|  
|\u|Unicode 逸出序列|\u0041 = "A"|  
|\v|垂直 Tab|0x000B|  
|\x|類似 "\u" (除了變數長度之外) 的 Unicode 逸出序列。|\x0041 或 \x41 = "A"|  
  
> [!NOTE]
>  在編譯時期，逐字字串會轉換為具有所有相同逸出序列的一般字串。 因此，如果您在偵錯工具監看式視窗中檢視逐字字串，您會看到由編譯器新增的逸出字元，而非來自於您原始程式碼的逐字版本。 例如，逐字字串 @"C:\files.txt" 會在監看式視窗中顯示為 "C:\\\files.txt"。  
  
## <a name="format-strings"></a>格式字串  
 格式字串是可在執行階段動態決定其內容的字串。 格式字串是透過內嵌「插入的運算式」或字串內大括弧內的預留位置來建立的。 大括弧 (`{...}`) 內的所有內容都會被解析為一個值並在執行階段以格式化字串形式輸出。 有兩種方式可用來建立格式字串：字串插補與複合格式設定。

### <a name="string-interpolation"></a>字串插值
C# 6.0 與更新版本中提供的[*插補字串*](../../language-reference/tokens/interpolated.md)可透過 `$` 特殊字元識別，而且在大括弧中包括插補運算式。 如果您是字串插補的新手，請參閱[字串插補 - C# 互動式教學課程](../../tutorials/intro-to-csharp/interpolated-strings.yml)以取得快速概觀。

使用字串插補來改進您程式碼的可讀性與可維護性。 字串插補可達成與 `String.Format` 方法相同的結果，但可改進使用方便性與內嵌簡潔度。

[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringInterpolation)]

### <a name="composite-formatting"></a>複合格式設定
<xref:System.String.Format%2A?displayProperty=nameWithType> 利用大括弧內的預留位置來建立格式字串。 此範例可產生與上面使用之字串插補方法類似的輸出。
  
[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringFormat)]

如需設定 .NET 類型格式的詳細資訊，請參閱 [.NET 中的格式設定類型](../../../standard/base-types/formatting-types.md)。
  
## <a name="substrings"></a>子字串  
 子字串是包含在字串中的任何字元序列。 使用 <xref:System.String.Substring%2A> 方法，來從原始字串的一部分建立新的字串。 您可以使用 <xref:System.String.IndexOf%2A> 方法，來搜尋子字串的一或多個出現位置。 使用 <xref:System.String.Replace%2A> 方法，以新字串取代所有指定的子字串。 與 <xref:System.String.Substring%2A> 方法類似，<xref:System.String.Replace%2A> 實際上會傳回新字串，並不會修改原始字串。 如需詳細資訊，請參閱[如何︰搜尋字串](../../how-to/search-strings.md)以及[如何︰修改字串內容](../../how-to/modify-string-contents.md)。  
  
 [!code-csharp[csProgGuideStrings#7](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_7.cs)]  
  
## <a name="accessing-individual-characters"></a>存取個別字元  
 您可以搭配索引值使用陣列標記法來取得個別字元的唯讀存取權，如下列範例所示：  
  
 [!code-csharp[csProgGuideStrings#9](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_8.cs)]  
  
 如果 <xref:System.String> 方法不提供修改字串中個別字元的必要功能，您可以使用 <xref:System.Text.StringBuilder> 物件「就地」修改個別字元，然後使用 <xref:System.Text.StringBuilder> 方法建立新的字串來儲存結果。 在下列範例中，假設您必須以特定方式修改原始字串，並儲存結果以供日後使用︰  
  
 [!code-csharp[csProgGuideStrings#8](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_9.cs)]  
  
## <a name="null-strings-and-empty-strings"></a>Null 字串和空字串  
 空字串是 <xref:System.String?displayProperty=nameWithType> 物件的執行個體，其中包含零個字元。 空字串經常用於各種程式設計案例中，來表示空白的文字欄位。 您可以對空字串呼叫方法，因為它們是有效的 <xref:System.String?displayProperty=nameWithType> 物件。 空字串會以下列方式初始化︰  
  
```  
string s = String.Empty;  
```  
  
 相較之下，Null 字串指的不是 <xref:System.String?displayProperty=nameWithType> 物件執行個體，而且對 Null 字串呼叫方法的任何嘗試都會導致 <xref:System.NullReferenceException>。 不過，您可以在搭配其他字串的串連和比較作業中使用 Null 字串。 下列範例說明對 Null 字串的參考會造成 (以及不會造成) 擲回例外狀況的一些情況︰  
  
 [!code-csharp[csProgGuideStrings#27](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_10.cs)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>使用 StringBuilder 進行快速字串建立  
 .NET 中的字串作業已高度最佳化，在大部分的情況下不會大幅影響效能。 不過，在部分案例中 (例如執行數百或數千次的緊密迴圈)，字串作業可能會影響效能。 <xref:System.Text.StringBuilder> 類別會建立一個字串緩衝區，能在您的程式執行許多字串操作的情況下提供較佳的效能。 <xref:System.Text.StringBuilder> 字串也可讓您重新指派內建字串資料類型所不支援的個別字元。 例如，下列程式碼能在不建立新字串的情況下變更字串內容：  
  
 [!code-csharp[csProgGuideStrings#20](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_11.cs)]  
  
 在下列範例中，將使用 <xref:System.Text.StringBuilder> 物件從一組數字類型建立字串：  
  
 [!code-csharp[csProgGuideStrings#15](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_12.cs)]  
  
## <a name="strings-extension-methods-and-linq"></a>字串、擴充方法和 LINQ  
 因為 <xref:System.String> 類型會實作 <xref:System.Collections.Generic.IEnumerable%601>，所以您可以對字串使用 <xref:System.Linq.Enumerable> 類別中所定義的擴充方法。 為了避免視覺雜亂，這些方法會從 <xref:System.String> 類型的 IntelliSense 中排除，不過您還是可以使用它們。 您也可以在字串上使用 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式。 如需詳細資訊，請參閱 [LINQ 和字串](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|主題|描述|  
|-----------|-----------------|  
|[如何：修改字串內容](../../how-to/modify-string-contents.md)|說明轉換字串及修改字串內容的技術。|  
|[如何：比較字串](../../how-to/compare-strings.md)|示範如何執行字串的序數與文化特定比較。|  
|[如何：串連多個字串](../../how-to/concatenate-multiple-strings.md)|示範如何將多個字串聯結成一個的各種方式。|
|[如何：使用 String.Split 剖析字串](../../how-to/parse-strings-using-split.md)|包含說明如何使用 `String.Split` 方法剖析字串的程式碼範例。|  
|[如何：搜尋字串](../../how-to/search-strings.md)|說明如何對字串中的特定文字或模式使用搜尋。|  
|[如何：判斷字串是否表示數值](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)|示範如何安全地剖析字串，以查看它是否有有效的數值。|  
|[字串內插補點](../../language-reference/tokens/interpolated.md)|描述可提供方便語法以設定格式字串的字串內插補點功能。|
|[基本字串作業](../../../../docs/standard/base-types/basic-string-operations.md)|提供使用 <xref:System.String?displayProperty=nameWithType> 和 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 方法執行基本字串作業之主題的連結。|  
|[剖析字串](../../../standard/base-types/parsing-strings.md)|描述如何將.NET 基底類型的字串表示轉換成對應類型的執行個體。|  
|[在 .NET 中剖析日期和時間字串](../../../standard/base-types/parsing-datetime.md)|示範如何將 "01/24/2008" 這類字串轉換為 <xref:System.DateTime?displayProperty=nameWithType> 物件。|  
|[比較字串](../../../../docs/standard/base-types/comparing.md)|包含如何比較字串的相關資訊，並提供以 C# 和 Visual Basic 撰寫的範例。|  
|[使用 StringBuilder 類別](../../../standard/base-types/stringbuilder.md)|描述如何使用 <xref:System.Text.StringBuilder> 類別來建立及修改動態字串物件。|  
|[LINQ 和字串](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)|提供如何使用 LINQ 查詢來執行各種字串作業的相關資訊。|  
|[C# 程式設計指南](../../../csharp/programming-guide/index.md)|提供說明 C# 中程式設計建構的主題連結。|  
