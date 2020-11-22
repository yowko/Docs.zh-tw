---
title: XML 文件
description: '瞭解 F # 中的支援，以從批註產生檔。'
ms.date: 09/15/2020
ms.openlocfilehash: 24d9dbfb5e28d39e224ef9428f025298464fc7f4
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099005"
---
# <a name="document-your-code-with-xml-comments"></a>使用 XML 批註記錄您的程式碼

您可以從三斜線產生檔 (//) F # 中的程式碼批註。 XML 批註可以在程式碼檔中的宣告之前 (. fs) 或簽章 (. fsi) 檔。

XML 文件註解是一種特殊類型的註解，新增於任何使用者定義型別或成員的定義上方。
XML 文件註解具特殊性，因為編譯器可以處理它們以在編譯時期產生 XML 文件檔案。
編譯器產生的 XML 檔案可以與您的 .NET 元件一起散發，讓 Ide 可以使用工具提示來顯示類型或成員的快速資訊。 此外，XML 檔案可以透過 [fsdocs](http://fsprojects.github.io/FSharp.Formatting/) 之類的工具來執行，以產生 API 參考網站。

XML 檔批註（如同所有其他批註）將會被編譯器忽略，除非已啟用以下所述的選項，以便在編譯時期檢查批註的有效性和完整性。

您可以執行下列其中一項動作，以在編譯時期產生 XML 檔案︰

- 您可以在 `GenerateDocumentationFile` 專案檔的 `<PropertyGroup>` 區段中加入 `.fsproj` 專案，這會在專案目錄中產生 XML 檔案，該檔案的根檔案名與元件相同。 例如：

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

- 如果您正在使用 Visual Studio 開發應用程式，請以滑鼠右鍵按一下專案，然後選取 [屬性]。 在屬性對話方塊中，選取 [建置] 索引標籤，然後檢查 [XML 文件檔案]。 您也可以變更編譯器寫入檔案的位置。

有兩種方式可以撰寫 XML 檔批註： with 和不含 XML 標記。 兩者都使用三斜線批註。

## <a name="comments-without-xml-tags"></a>沒有 XML 標記的批註

如果 `///` 批註的開頭不是，則 `<` 會將整個註解文字視為程式碼結構的摘要檔（緊接在後面）。 當您只想撰寫每個結構的簡短摘要時，請使用這個方法。

批註會在檔準備期間編碼為 XML，因此 `<` `>` 不需要將字元（如、和）編碼 `&` 。 如果您未明確指定摘要標記，則不應指定 **其他標記，** 例如 **param** 或傳回標記。

下列範例顯示不含 XML 標記的替代方法。 在此範例中，批註中的整個文字都會被視為摘要。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="comments-with-xml-tags"></a>具有 XML 標記的批註

如果批註主體的開頭是 `<` (一般 `<summary>`) ，則會使用 xml 標記將它視為 xml 格式的批註主體。 第二個可讓您指定簡短摘要的個別附注、其他備註、每個參數的檔、類型參數和所擲回的例外狀況，以及傳回值的描述。

以下是簽章檔案中的一般 XML 檔批註：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="recommended-tags"></a>建議的標記

如果您使用 XML 標記，下表描述 F # XML 程式碼批註中所識別的外部標記。

| 標記語法                                  | Description |
|---------------------------------------------|-----------|
| `<summary>`**_文本_**`</summary>`           | 指定 *文字* 是程式元素的簡短描述。 描述通常是一或兩個句子。|
| `<remarks>`**_文本_**`</remarks>`           | 指定 *文字* 包含程式元素的補充資訊。|
| `<param name="`**_名稱_** `">`**_描述_**`</param>` | 指定函數或方法參數的名稱和描述。|
| `<typeparam name="`**_名稱_** `">`**_描述_**`</typeparam>` | 指定型別參數的名稱和描述。|
| `<returns>`**_文本_**`</returns>`           | 指定 *文字* 描述函數或方法的傳回值。|
| `<exception cref="`**_類型_** `">`**_描述_**`</exception>` |指定可以產生的例外狀況類型，以及擲回它的情況。|
| `<seealso cref="`**_參考_**`"/>`      | 指定另一種類型之檔的 [另一個] 連結。 *參考* 是 XML 檔檔案中顯示的名稱。 另請參閱檔頁面底部的連結。|

下表描述在 [描述] 區段內使用的標記：

| 標記語法                                | Description |
|-------------------------------------------|-------------|
| `<para>`**_文本_**`</para>`               | 指定文欄位落。 這是用來分隔 **備註** 標記內的文字。|
| `<code>`**_文本_**`</code>`               | 指定 *文字* 是多行程式碼。 檔產生器可以使用這個標記，以適用于程式碼的字型來顯示文字。|
| `<paramref name="`**_名字_**`"/>`         | 指定相同檔批註中的參數參考。|
| `<typeparamref name="`**_名字_**`"/>`     | 在相同的檔批註中指定類型參數的參考。|
| `<c>`**_文本_**`</c>`                     | 指定 *文字* 為內嵌程式碼。 檔產生器可以使用這個標記，以適用于程式碼的字型來顯示文字。|
| `<see cref="`**_參考_** `">`**_文字_**`</see>` | 指定另一個程式元素的內嵌連結。 *參考* 是 XML 檔檔案中顯示的名稱。 *文字* 是連結中所顯示的文字。|

### <a name="user-defined-tags"></a>使用者定義標記

先前的標記代表 F # 編譯器和一般 F # 編輯器工具所能辨識的標記。 不過，使用者可以定義自己的標記。
Fsdocs 之類的工具可為您提供額外標記的支援 [\<namespacedoc>](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1031-xmldoc-extensions.md) 。
自訂或內部文件產生工具也可以與標準標記搭配使用，而且可以支援從 HTML 到 PDF 的多個輸出格式。

## <a name="compile-time-checking"></a>編譯時間檢查

當 `--warnon:3390` 啟用時，編譯器會驗證 XML 的語法和和標記中參考的參數 `<param>` `<paramref>` 。

## <a name="documenting-f-constructs"></a>記載 F # 結構

F # 結構（例如模組、成員、聯集案例和記錄欄位）會在 `///` 其宣告之前立即以批註記載。
如有需要，會在 `///` 引數清單之前提供批註，以記載類別的隱含函式。 例如：

```fsharp
/// This is the type
type SomeType
      /// This is the implicit constructor
      (a: int, b: int) =

    /// This is the member
    member _.Sum() = a + b
```

## <a name="limitations"></a>限制

C # 中不支援 XML 檔的某些功能（c # 和其他 .NET 語言）。

- 例如，在 F # 中，交互參考必須使用對應符號的完整 XML 簽章 `cref="T:System.Console"` 。
  簡單的 c # 樣式交互參考（例如） `cref="Console"` 不會針對完整的 XML 簽章進行詳細檢查，而且 F # 編譯器不會檢查這些元素。 某些檔工具可能會允許後續處理使用這些交叉參考，但是應該使用完整簽章。

- `<include>` `<inheritdoc>` F # 編譯器不支援這些標記。 如果使用它們，則不會提供任何錯誤，但會直接複製到產生的檔檔，而不會影響所產生的檔。

- F # 編譯器不會檢查交互參考，即使使用時也一樣 `-warnon:3390` 。

- `<typeparam>` `<typeparamref>` F # 編譯器不會檢查標記中使用的名稱，即使使用時也不會檢查 `--warnon:3390` 。

- 如果遺漏檔，則不會提供任何警告，即使使用時也不會出現 `--warnon:3390` 。

## <a name="recommendations"></a>建議

有許多原因，建議您記錄程式碼。 以下是一些最佳作法、一般使用案例，以及在 F # 程式碼中使用 XML 檔標記時應該知道的事項。

- `--warnon:3390`在您的程式碼中啟用選項，以協助確保您的 xml 檔是有效的 xml。

- 請考慮新增簽章檔案，以便將大型 XML 檔批註與您的實作分開。

- 為保持一致性，應該記錄所有公開可見的類型和其成員。 如果您必須執行它，則請執行。

- 最小的模組、類型和其成員應具有純文字 `///` 批註或 `<summary>` 標記。 這會顯示在 F # 編輯工具的自動完成工具提示視窗中。

- 應該使用結尾為句號的完整句子來撰寫文件文字。

## <a name="see-also"></a>另請參閱

- C [# XML 檔批註 &#40;c&#35; 程式設計指南&#41;](../../csharp/programming-guide/xmldoc/index.md)。
- [F # 語言參考](index.md)
- [編譯器選項](compiler-options.md)
