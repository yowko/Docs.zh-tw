---
title:
- 文章標題
description: ''
author:
- GITHUB USERNAME
ms.author:
- MICROSOFT ALIAS OF INTERNAL OWNER
ms.date:
- CREATION/UPDATE DATE - mm/dd/yyyy
ms.topic:
- TOPIC TYPE
ms.prod:
- PRODUCT VALUE
helpviewer_keywords:
- OFFLINE BOOK INDEX ENTRIES
ms.openlocfilehash: e6c912f5ff9590f3b8cbb0f7e3f88e08fa9dd556
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106905"
---
# <a name="metadata-and-markdown-template"></a>中繼資料和 Markdown 範本

此 dotnet/docs 範本包含 Markdown 語法，以及設定中繼資料的指導。 若要善加利用它，您必須檢閱[原始的 Markdown (英文)](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) 和[轉譯後的檢視 (英文)](https://github.com/dotnet/docs/blob/master/styleguide/template.md) (例如，原始的 Markdown 會顯示中繼資料區塊，而轉譯後的檢視則不會)。

在建立 Markdown 檔案的時候，您應將此範本複製到新的檔案，填入下列指定的中繼資料，將上方的 H1 標題設為文章的標題，然後刪除內容。

## <a name="metadata"></a>中繼資料

完整的中繼資料區塊如上 (以[原始的 Markdown (英文)](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) 顯示)，其中分為必要欄位和選擇性欄位。 重點提示：

- 請「務必」  在中繼資料項目的值和冒號 (:) 之間加上一個空格。
- 如果選擇性的中繼資料元素沒有值，請使用 # 將元素標記為註解，或將它移除 (請勿將它保留空白或使用 "na")。 如果您要將值新增至已設為註解的元素，請務必移除 #。
- 在值中出現冒號 (例如標題) 會中斷中繼資料剖析器。 在此情況下，請使用雙引號括住標題 (例如，`title: "Writing .NET Core console apps: An advanced step-by-step guide"`)。
- **title**：出現在搜尋引擎結果中。 此標題不應該與 H1 標題中的標題相同，且應包含最多 60 個字元。
- **description**：摘要文章的內容。 它通常顯示在 [搜尋結果] 頁面中，但不會用於搜尋排名。 其長度應該是 115-145 個字元，包括空格。
- **author** 和 **ms.author**：author 欄位應包含該作者的 **GitHub 使用者名稱**，而不是別名。  另一方面，**ms.author** 欄位應該包含 Microsoft 別名，並指出負責維護文章的人員。
- **ms.topic**：主題類型。 最常見的值是 `conceptual`，且是在全域層級設定。 其他常用的值為 `tutorial`、`overview` 和 `reference`。
- **ms.devlang** 會定義針對主題顯示的語言篩選條件。 您可以在[支援的語言](#supported-languages)一節看到支援的值清單。 只有當主題涵蓋多個程式設計語言時，才需要設定。 一般而言，我們只會在內容中使用 `csharp`、`vb`、`fsharp` 和 `cpp` 作為此值。
- **ms.prod**：用於 BI 用途的產品識別。 它們通常是在全域層級設定，因此通常不會出現在每篇文章的中繼資料區塊中。
- **ms.technology**：其他 BI 分類。 一些支援的值為 `devlang-csharp` (適用於 C# 主題)、`devlang-fsharp` (適用於 F# 主題) 和 `devlang-visual-basic` (適用於 VB 主題)。 針對其他指南，值會有所不同，因此請詢問小組成員以取得指導方針。
- **ms.date**：格式為 MM/DD/YYYY 的日期。 顯示在已發佈頁面上，以指出上次文章基本上編輯或保證為「全新」的時間 (也就是，已檢查過文章並將其視為最新)。
- **helpviewer_keywords**：項目用於離線書籍索引 (Visual Studio 中的功能)。
- **f1_keywords**：將文章連接至 F1 鍵 (Visual Studio 中的功能)。

## <a name="basic-markdown-gfm-and-special-characters"></a>基本 Markdown、GFM 和特殊字元

支援所有基本和 GitHub Flavored Markdown (GFM)。 如需詳細資訊，請參閱：

- [基準 Markdown 語法 (英文)](https://daringfireball.net/projects/markdown/syntax)
- [GFM 文件 (英文)](https://guides.github.com/features/mastering-markdown)

Markdown 使用 \*、\` 和 \# 等特殊字元來設定格式。 如果要在內容中包含這些字元，請遵循下列其中一種作法：

- 在該特殊字元前面加上反斜線來將它「逸出」(例如，\* 逸出為 `\*`)
- 使用該字元的 [HTML 實體代碼 (英文)](https://www.ascii.cl/htmlcodes.htm) (例如，&#42; 為 `&#42;`)。

## <a name="file-name"></a>檔案名稱

檔案名稱使用下列規則︰

- 只包含小寫字母、數字和連字號。
- 不使用空格或標點符號。 使用連字號來分隔檔名中的文字和數字。
- 使用明確的動作動詞，例如 develop、buy、build、troubleshoot。 不使用 -ing 字詞。
- 不使用短字詞，例如 a、and、the、in、or 等等。
- 必須為 Markdown 格式且使用副檔名 .md。
- 盡可能保持檔名簡短。 它們會是文章 URL 的一部分。

## <a name="headings"></a>標題

使用句子樣式的大寫。 下列情況一律大寫：

- 標題的第一個字。
- 標題中冒號後的第一個字 (例如，"How to:Sort an array")。

標題應使用 atx 樣式，也就是在行開頭以 1 至 6 個井字號 (#) 來表示標題，這會對應到 HTML 標題層級 H1 至 H6。 上面使用的是第一和第二層級標題的範例。

請「務必」  確定主題中只有一個第一層級標題 (H1)，該標題會顯示為頁面標題。

如果您的標題結尾是 `#` 字元，則您必須在結尾另外加上一個 `#` 以使標題正確轉譯。 例如，`# Async Programming in F# #`。

第二層級的標題會產生頁面目錄，並顯示在頁面標題下的 [本文內容] 區段中。

### <a name="third-level-heading"></a>第三層級標題
#### <a name="fourth-level-heading"></a>第四層級標題
##### <a name="fifth-level-heading"></a>第五層級標題
###### <a name="sixth-level-heading"></a>第六層級標題

## <a name="text-styling"></a>文字樣式

「斜體」  用於檔案、資料夾、路徑 (較長的項目請分割為各行)、新字詞。

**粗體** 用於 UI 元素。

`Code` 用於內嵌程式碼、語言關鍵字、NuGet 套件名稱、命令列命令、資料庫資料表和資料行名稱，以及您不想要可以點按的 URL。

## <a name="links"></a>連結

### <a name="internal-links"></a>內部連結

若要連結到同一個 Markdown 檔案中的標題 (又稱錨點連結)，您需要找出該標題的識別碼。 若要確認識別碼，請檢視轉譯文章的原始程式碼，以找出該標題的識別碼 (例如，`id="blockquote"`)，然後使用「# + 識別碼」來連結 (例如，`#blockquote`)。
此識別碼是依據標題文字而自動產生。 舉例來說，若某章節名稱為 `## Step 2`，則識別碼會是 `id="step-2"`。

- 範例：`[Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier)` 會產生[宣告具有語言識別碼的內嵌區塊](#inline-code-blocks-with-language-identifier)。

若要連結到同一個存放庫中的 Markdown 檔案，請使用[相對連結](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2)，且檔案名稱結尾包含 ".md"。

- 範例：`[Readme file](../README.md)` 會產生[讀我檔案](../README.md)。 (請注意，連結會區分大小寫。)
- 範例：`[Welcome to .NET](../docs/welcome.md)` 會產生[歡迎使用 .NET](../docs/welcome.md)。

若要連結到相同存放庫中 Markdown 檔案內的標題，請使用「相對連結 + 井字號」來連結。

- 範例：`[.NET Community](../docs/welcome.md#open-source)` 會產生 [.NET 社群](../docs/welcome.md#open-source)。

在大部分情況下，我們會使用相對連結，且不鼓勵在連結中使用 `~/`，因為相對連結會在 GitHub 上的來源中解析。 不過，每當我們連結至相依存放庫中的檔案時，我們會使用 `~/` 字元來提供路徑。 因為相依存放庫中的檔案位於 GitHub 中不同位置，所以連結不會以相對連結正確解析，不論其撰寫方式為何。

C# 語言規格和 Visual Basic 語言規格包含在 .NET 文件中，方法是包含語言存放庫中的來源。 Markdown 來源是在 [csharplang](https://github.com/dotnet/csharplang) 和 [visual basic](https://github.com/dotnet/vblang) 存放庫中進行管理。

規格連結必須指向包含這些規格的來源目錄。 對於 C#，它是 **~/_csharplang/spec**，而對於 VB 而言，它是 **~/_vblang/spec**。

- 範例：`[C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions)` 會產生 [C# 查詢運算式](~/_csharplang/spec/expressions.md#query-expressions)。

### <a name="external-links"></a>外部連結

若要連結到外部檔案，請使用完整 URL 作為連結。

- 範例：`[GitHub](https://www.github.com)` 會產生 [GitHub](https://www.github.com)。

如果 Markdown 檔案中出現 URL，系統會將它轉換成可點擊的連結。

- 範例：`<https://www.github.com>` 會產生 <https://www.github.com>。

外部連結最好使用 `https` 通訊協定。 僅針對不支援 `https` 的網站使用 `http` 連結。

### <a name="links-to-apis"></a>API 的連結

組建系統有些延伸模組可讓我們在不需使用外部連結的情況下，連結到 .NET API。
當連結到 API 時，您可以使用從原始程式碼自動產生的唯一識別碼 (UID)。

UID 等於完整型別和成員名稱。

如果您在 UID 之後新增 \* (或 %2A)，則連結會代表多載頁面，而不是特定的 API。 例如，您可以用它來以一般方式連結至 [List\<T>.BinarySearch 方法](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch)頁面，而不是使用特定的多載，例如 [List\<T>.BinarySearch(T, IComparer\<T>)](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch#System_Collections_Generic_List_1_BinarySearch__0_)。 當成員未多載時，您也可以使用 \* 連結至成員頁面；如此您便不必在 UID 中包含參數清單。

若要連結至特定方法多載，您必須包含每個方法參數的完整型別名稱。 例如，\<xref:System.DateTime.ToString> 會連結到無參數的 [DateTime.ToString](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString) 方法，而 \<xref:System.DateTime.ToString(System.String,System.IFormatProvider)> 連結到 [DateTime.ToString(String,IFormatProvider)](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString_System_String_System_IFormatProvider_) 方法。 您可以從 `https://xref.docs.microsoft.com/autocomplete` 找到特定多載成員的 UID。 查詢字串 "?text= *\<type-member-name>* " 會識別您想要查看其 UID 的型別或成員。 例如，`https://xref.docs.microsoft.com/autocomplete?text=string.format` 會擷取 [String.Format](https://docs.microsoft.com/dotnet/api/system.string.format) 多載。

若要連結到泛型型別 (例如 [System.Collections.Generic.List\<T>](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1))，請使用 ` (%60) 字元，後面接著泛型型別參數的數目。 例如，\<xref:System.Nullable%601> 會連結到 [System.Nullable\<T>](https://docs.microsoft.com/dotnet/api/system.nullable-1) 型別，而 \<xref:System.Func%602> 連結到 [System.Func\<T,TResult>](https://docs.microsoft.com/dotnet/api/system.func-2) 委派。

您可以使用下列其中一個語法：

1. 自動連結：`<xref:UID>` 或 `<xref:UID?displayProperty=nameWithType>`

   `displayProperty` 查詢參數會產生完整的連結文字。 根據預設，連結文字只會顯示成員或型別名稱。

2. Markdown 連結：`[link text](xref:UID)`

   用於您想要自訂所顯示的連結文字時。

例如：

- `<xref:System.String>` 會轉譯為 [String](https://docs.microsoft.com/dotnet/api/system.string)
- `<xref:System.String?displayProperty=nameWithType>` 會轉譯為 [System.String](https://docs.microsoft.com/dotnet/api/system.string)
- `[String class](xref:System.String)` 會轉譯為 [String 類別](https://docs.microsoft.com/dotnet/api/system.string)

如需使用此標記法的詳細資訊，請參閱[使用交互參照 (英文)](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference)。

尋找 UID 的方法有兩種：

- 查看您要連結到的 API 頁面來源並尋找 ms.assetid 值。 請注意，個別的多載值不會顯示在來源中。
- 使用下列工具來搜尋 UID： https://xref.docs.microsoft.com/autocomplete?text=tostring (以您嘗試尋找的 API 名稱部分取代 tostring)。 此工具會在 UID 的任何部分中搜尋所提供 `text` 查詢參數。 例如，您可以搜尋成員名稱 (ToString)、部分成員名稱 (ToString)、型別和成員名稱 (Double.ToString) 等。

當 UID 包含特殊字元 \`、\# 或 \* 時，該 UID 值必須分別編碼為 HTML 代碼 `%60`、`%23` 和 `%2A`。 您有時會看到括弧也經編碼，但這不是必要條件。

例如：

- System.Threading.Tasks.Task\`1 會變成 `System.Threading.Tasks.Task%601`
- System.Exception.\#ctor 會變成 `System.Exception.%23ctor`
- System.Lazy\`1.\#ctor(System.Threading.LazyThreadSafetyMode) 會變成 `System.Lazy%601.%23ctor%28System.Threading.LazyThreadSafetyMode%29`

## <a name="lists"></a>清單

### <a name="ordered-lists"></a>排序清單

1. 這
1. 是
1. 一個
1. 排序
1. 清單

#### <a name="ordered-list-with-an-embedded-list"></a>包含內嵌清單的排序清單

1. 這裡
1. 有
1. 一個
1. 內嵌
    1. Miss Scarlett
    1. Professor Plum
1. 排序
1. 清單

### <a name="unordered-lists"></a>未排序清單

- 這個
- 是
- 一個
- 項目符號
- 清單

#### <a name="unordered-list-with-an-embedded-list"></a>包含內嵌清單的未排序清單

- 這個
- 項目符號
- 清單
  - Mrs. Peacock
  - Mr. Green
- 包含
- 另一個
  1. Colonel Mustard
  1. Mrs. White
- 清單

## <a name="horizontal-rule"></a>水平線

---

## <a name="tables"></a>資料表

| 資料表        | 很           | 酷  |
| ------------- |:-------------:| -----:|
| 欄 3 為      | 靠右對齊 | $1600 |
| 欄 2 為      | 置中      |   $12 |
| 欄 1 為預設 | 靠左對齊     |    $1 |

您可以使用 [Markdown 表格產生工具 (英文)](https://www.tablesgenerator.com/markdown_tables) 來輕鬆產生表格。

## <a name="code"></a>程式碼

包含程式碼的最佳方法是加入實際範例的程式碼片段。 請遵循[參與指南](../CONTRIBUTING.md#contributing-to-samples)中的指示來建立範例。

您可以使用下列語法來包含程式碼：

```markdown
[!code-<language>[<name>](<pathToFile><queryoption><queryoptionvalue>)]
```

- `-<language>` (「選擇性」  但「建議使用」  )
  - 所參考程式碼片段的語言。 如需支援值的清單，請參閱[支援的語言](#supported-languages)。

- `<name>` (選擇性  )
  - 程式碼片段的名稱。 它對輸出 HTML 沒有任何影響，但您可以用它來改善 Markdown 原始程式的可讀性。

- `<pathToFile>` (強制  )
  - 檔案系統中的相對路徑，表示要參考的程式碼片段檔案。

- `<queryoption>` 和 `<queryoptionvalue>` (選擇性  )
  - 一起使用以指定從檔案取出程式碼的方式：
    - `#`：`#L{startlinenumber}-L{endlinenumber}` (行範圍) 「或」  `#{tagname}` (標籤名稱)。
    不建議使用行號，因為此功能不盡完善。 標籤名稱是參考程式碼片段的慣用方式。
    - `range`：`?range=1,3-5` 行範圍。 這個範例包含第 1、3、4 和 5 行。
    - `dedent`：`?dedent=8` 以數個空格將行縮排，在此案例中為 8 個空格。 這可以與 `range` 和其他查詢選項結合，以選取檔案的部分行。
    - `outdent`：`?outdent=8` 以數個空格反轉行的縮排，在此案例中為 8 個空格。 這可以與 `range` 和其他查詢選項結合，以選取檔案的部分行。

我們建議您盡可能使用標籤名稱選項。 標籤名稱是區域或程式碼註解的名稱，其格式如同在原始程式碼中出現的 `Snippettagname`。 下列範例示範如何參考標籤名稱 `1`：

```markdown
[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]
```

您可以看到程式碼片段標籤在[此原始程式檔案](https://github.com/dotnet/samples/blob/master/snippets/csharp/language-reference/keywords/throw/throw-1.cs)中的結構。 如需各語言程式碼片段原始程式檔中標籤名稱表示的詳細資料，請參閱 [DocFX 指導方針](https://dotnet.github.io/docfx/spec/docfx_flavored_markdown.html#tag-name-representation-in-code-snippet-source-file)。

包含來自完整程式的程式碼片段可確保所有程式碼都經過我們的持續整合 (CI) 系統。 不過，如果您需要顯示一些造成編譯時間或執行階段錯誤的程式碼，您可以使用內嵌程式碼區塊。

### <a name="inline-code-blocks-with-language-identifier"></a>具有語言識別碼的內嵌程式碼區塊

使用「三個反引號 (\`\`\`) + 語言識別碼」，來在程式碼區塊套用該語言的語法著色。 以下是支援的語言清單，其中顯示每個語言識別碼的 Markdown 標籤。

#### <a name="supported-languages"></a>支援的語言

|名稱|Markdown 標籤|
|-----|-------|
|ASP.NET 與 C#|aspx-csharp|
|ASP.NET 與 VB|aspx-vb|
|Azure CLI|azurecli|
|AzCopy|azcopy|
|C++|cpp|
|C#|csharp|
|瀏覽器中的 C#|csharp-interactive|
|主控台|主控台|
|F#|fsharp|
|Java|java|
|JavaScript|javascript|
|JSON|json|
|NodeJS|nodejs|
|Objective-C|objc|
|PHP|php|
|PowerShell|powershell|
|Python|Python|
|Ruby|ruby|
|SQL|sql|
|Swift|swift|
|VB|vb|
|XAML|xaml|
|XML|xml|

`csharp-interactive` 名稱會指定 C# 語言，以及從瀏覽器執行範例的能力。 這些程式碼片段會在 Docker 容器中進行編譯和執行，而該程式執行結果會顯示在使用者的瀏覽器視窗中。

下列程式碼區塊範例分別使用 C# 語言識別碼 (\`\`\`csharp)、Python 語言識別碼 (\`\`\`python) 和 PowerShell 語言識別碼 (\`\`\`powershell)。

##### <a name="c9839"></a>C&#9839;

```csharp
using System;
namespace HelloWorld
{
    class Hello
    {
        static void Main()
        {
            Console.WriteLine("Hello World!");

            // Keep the console window open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

#### <a name="python"></a>Python

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```

#### <a name="powershell"></a>PowerShell

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="generic-code-block"></a>一般程式碼區快

使用三個反引號 (&#96;&#96;&#96;) 撰寫一般程式碼區塊。

> 建議的做法是搭配語言識別碼使用程式碼區塊 (如上節所述)，以確保語法在文件網站上適當地醒目顯示。 必要時才使用一般程式碼區塊。

```
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

## <a name="blockquotes"></a>引文

> The drought had lasted now for ten million years, and the reign of the terrible lizards had long since ended. Here on the Equator, in the continent which would one day be known as Africa, the battle for existence had reached a new climax of ferocity, and the victor was not yet in sight. In this barren and desiccated land, only the small or the swift or the fierce could flourish, or even hope to survive.

## <a name="images"></a>影像

### <a name="static-image-or-animated-gif"></a>靜態影像或動畫 GIF

```markdown
![this is the alt text](../images/Logo_DotNet.png)
```

![這是替代文字](../images/Logo_DotNet.png)

### <a name="linked-image"></a>連結影像

```markdown
[![alt text for linked image](../images/Logo_DotNet.png)](https://dot.net)
```

[![連結影像的替代文字](../images/Logo_DotNet.png)](https://dot.net)

## <a name="videos"></a>視訊

目前，您可以使用下列語法內嵌 Channel 9 和 YouTube 影片：

### <a name="channel-9"></a>Channel 9

```markdown
> [!VIDEO <channel9_video_link>]
```

若要取得影片的正確 URL，請選取視訊框架下的 [內嵌]  索引標籤，然後從 `<iframe>` 元素複製 URL。 例如：

```markdown
> [!VIDEO https://channel9.msdn.com/Blogs/dotnet/NET-Core-20-Released/player]
```

### <a name="youtube"></a>YouTube

若要取得影片的正確 URL，請在影片上按一下滑鼠右鍵、選取 [複製內嵌程式碼]  ，然後從 `<iframe>` 元素複製 URL。

```markdown
> [!VIDEO <youtube_video_link>]
```

例如：

```markdown
> [!VIDEO https://www.youtube.com/embed/Q2mMbjw6cLA]
```

## <a name="docsmicrosoft-extensions"></a>docs.microsoft 延伸模組

docs.microsoft 為 GitHub Flavored Markdown 提供幾個額外的延伸模組。

### <a name="alerts"></a>警示

請務必使用下列的警示樣式，這樣它們才能在文件網站中轉譯為適當的樣式。 不過，GitHub 的轉譯引擎無法分辨這些樣式。

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

它們轉譯之後看起來像這樣：![警示樣式](../images/alerts.png)

### <a name="includes"></a>包括

您可以使用 include，將一個檔案的 Markdown 內嵌至另一個檔案。

[!INCLUDE[sample include file](../includes/sampleinclude.md)]

### <a name="checked-lists"></a>核取清單

有適用於清單的自訂樣式。 您可以轉譯具有綠色核取記號的清單。

> [!div class="checklist"]
> - 如何建立 .NET Core 應用程式
> - 如何新增 Microsoft.XmlSerializer.Generator 套件的參考
> - 如何編輯 MyApp.csproj 以新增相依性
> - 如何新增類別和 XmlSerializer
> - 如何建置和執行應用程式

您可以在 [.NET Core 文件](https://docs.microsoft.com/dotnet/core/additional-tools/xml-serializer-generator)中看到核取清單的實際範例。

### <a name="buttons"></a>按鈕

> [!div class="button"]
> [按鈕連結](../docs/core/index.md)

您可以在 [Visual Studio 文件](https://docs.microsoft.com/visualstudio/install/install-visual-studio#step-2---download-visual-studio)中看到按鈕的實際範例。

### <a name="selectors"></a>選取器

> [!div class="op_single_selector"]
- [macOS](../docs/core/tutorials/using-on-macos.md)
- [Windows](../docs/core/tutorials/with-visual-studio.md)

您可以在 [Azure 文件](https://docs.microsoft.com/azure/expressroute/expressroute-howto-circuit-classic)中看到選取器的實際範例。

### <a name="step-by-steps"></a>逐步執行

>[!div class="step-by-step"]
>[上一頁](../docs/csharp/expression-trees-interpreting.md)
>[下一頁](../docs/csharp/expression-trees-translating.md)

您可以在 [C# 指南](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/program-structure)中看到逐步執行的實際範例。
