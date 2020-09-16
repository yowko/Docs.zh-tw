---
title: XML 文件
description: '瞭解 F # 中的支援，以從批註產生檔。'
ms.date: 05/16/2016
ms.openlocfilehash: 03d14cef910d149f0c7a2f3a49c8cf4606ac5305
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556573"
---
# <a name="xml-documentation"></a>XML 文件

您可以從三斜線產生檔 (//) F # 中的程式碼批註。 XML 批註可以在程式碼檔中的宣告之前 (. fs) 或簽章 (. fsi) 檔。

## <a name="generating-documentation-from-comments"></a>從批註產生檔

F # 中用來產生註釋檔的支援，與其他 .NET Framework 語言的支援相同。 如同其他 .NET Framework 語言， [-doc 編譯器選項](./compiler-options.md) 可讓您產生 XML 檔案，其中包含您可以使用 [DocFX](https://dotnet.github.io/docfx/) 或 [>sandcastle](https://github.com/EWSoftware/SHFB)等工具轉換成檔的資訊。 使用設計用於以其他 .NET Framework 語言撰寫之元件的工具所產生的檔，通常會產生以 F # 結構的編譯形式為基礎之 Api 的觀點。 除非工具特別支援 F #，否則這些工具所產生的檔不會與 API 的 F # 視圖相符。

如需有關如何從 XML 產生檔的詳細資訊，請參閱 [Xml 檔批註 &#40;C&#35; 程式設計指南&#41;](../../csharp/programming-guide/xmldoc/index.md)。

## <a name="recommended-tags"></a>建議的標記

有兩種方式可以撰寫 XML 檔批註。 其中一種方式就是直接以三斜線批註撰寫檔，而不使用 XML 標記。 如果您這麼做，就會將整個註解文字視為程式碼結構的摘要檔，緊接在後面。 當您只想撰寫每個結構的簡短摘要時，請使用這個方法。 另一種方法是使用 XML 標記來提供更結構化的檔。 第二個方法可讓您指定簡短摘要的個別附注、其他備註、每個參數的檔、類型參數和所擲回的例外狀況，以及傳回值的描述。 下表描述 F # XML 程式碼批註中可辨識的 XML 標記。

|標記語法|描述|
|----------|-----------|
|**\<c\>**_文本_**\</c\>**|指定 *文字* 為程式碼。 檔產生器可以使用這個標記，以適用于程式碼的字型來顯示文字。|
|**\<summary\>**_文本_**\</summary\>**|指定 *文字* 是程式元素的簡短描述。 描述通常是一或兩個句子。|
|**\<remarks\>**_文本_**\</remarks\>**|指定 *文字* 包含程式元素的補充資訊。|
|**\<param name="**_name_**"\>**_描述_**\</param\>**|指定函數或方法參數的名稱和描述。|
|**\<typeparam name="**_name_**"\>**_描述_**\</typeparam\>**|指定型別參數的名稱和描述。|
|**\<returns\>**_文本_**\</returns\>**|指定 *文字* 描述函數或方法的傳回值。|
|**\<exception cref="**_type_**"\>**_描述_**\</exception\>**|指定可以產生的例外狀況類型，以及擲回它的情況。|
|**\<see cref="**_reference_**"\>**_文本_**\</see\>**|指定另一個程式元素的內嵌連結。 *參考*是 XML 檔檔案中顯示的名稱。 *文字*是連結中所顯示的文字。|
|**\<seealso cref="**_reference_**"/\>**|指定另一種類型之檔的 [另一個] 連結。 *參考*是 XML 檔檔案中顯示的名稱。 另請參閱檔頁面底部的連結。|
|**\<para\>**_文本_**\</para\>**|指定文欄位落。 這是用來分隔 **備註** 標記內的文字。|

## <a name="example"></a>範例

### <a name="description"></a>描述

以下是簽章檔案中的一般 XML 檔批註。

### <a name="code"></a>程式碼

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例顯示不含 XML 標記的替代方法。 在此範例中，批註中的整個文字都會被視為摘要。 請注意，如果您未明確指定摘要標記，則不應指定**其他標記，** 例如**param**或傳回標記。

### <a name="code"></a>程式碼

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [編譯器選項](compiler-options.md)
