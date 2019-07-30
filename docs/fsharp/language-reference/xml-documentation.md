---
title: XML 文件 (F#)
description: 深入瞭解中F#的支援, 以從批註產生檔。
ms.date: 05/16/2016
ms.openlocfilehash: b89ab4117f4dd71126f8e203f4a5271ab3c30021
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630827"
---
# <a name="xml-documentation"></a>XML 文件

您可以從中F#的三個斜線 (////) 程式碼批註產生檔。 XML 批註可以在程式碼檔 (. fs) 或簽章 (. fsi.exe) 檔案中的宣告之前。

## <a name="generating-documentation-from-comments"></a>從批註產生檔

從批註產生F#檔的支援與其他 .NET Framework 語言相同。 如同其他 .NET Framework 語言, [-doc 編譯器選項](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04)可讓您產生 XML 檔案, 其中包含您可以使用[DocFX](https://dotnet.github.io/docfx/)或[sandcastle 這類](https://github.com/EWSoftware/SHFB)等工具轉換成檔的資訊。 使用設計來搭配以其他 .NET Framework 語言撰寫之元件使用的工具所產生的檔, 通常會根據編譯的F#結構形式來產生 api 的觀點。 除非工具特別支援F#, 否則這些工具所產生的檔不符合F# API 的觀點。

如需如何從 xml 產生檔的詳細資訊, 請參閱[xml 檔&#40;批註&#35; C 程式&#41;設計指南](https://msdn.microsoft.com/library/b2s063f7)。

## <a name="recommended-tags"></a>建議的標記

有兩種方式可以撰寫 XML 檔批註。 其中一個是直接在三斜線的批註中撰寫檔, 而不使用 XML 標記。 如果您這樣做, 則會將整個註解文字視為程式碼結構的摘要檔, 這會緊接在之後。 當您想要只寫入每個結構的簡短摘要時, 請使用這個方法。 另一個方法是使用 XML 標記來提供更多結構化檔。 第二種方法可讓您針對簡短摘要、其他備註、每個參數和型別參數的檔和擲回的例外狀況, 以及傳回值的描述, 指定個別的附注。 下表描述 xml 程式碼批註中F#可辨識的 xml 標記。

|標記語法|說明|
|----------|-----------|
|**\<c\>** _text_ **\</c\>**|指定*文字*為程式碼。 檔產生器可以使用這個標記, 以適合程式碼的字型來顯示文字。|
|**\<summary\>** _text_ **\</summary\>**|指定*文字*是程式元素的簡短描述。 描述通常是一或兩個句子。|
|**備註文字\>/remarks \<**  **\< \>**|指定*文字*包含程式元素的補充資訊。|
|**\<param name="** _name_ **"\>** _description_ **\</param\>**|指定函式或方法參數的名稱和描述。|
|**\<typeparam name="** _name_ **"\>** _description_ **\</typeparam\>**|指定類型參數的名稱和描述。|
|**\<returns\>** _text_ **\</returns\>**|指定*文字*描述函數或方法的傳回值。|
|**\<exception cref="** _type_ **"\>** _description_ **\</exception\>**|指定可以產生的例外狀況類型, 以及擲回的情況。|
|**\>** **請參閱\> cref=\<**  "reference" 文字/see **\<**|指定另一個程式元素的內嵌連結。 *參考*是出現在 XML 檔檔中的名稱。 *文字*是連結中顯示的文字。|
|**\>** seealso cref = "reference"/ **\<**|指定另一個類型之檔的 [另請參閱] 連結。 *參考*是出現在 XML 檔檔中的名稱。 另請參閱連結通常會出現在檔頁面的底部。|
|**\<para\>** _text_ **\</para\>**|指定文字的段落。 這是用來分隔 [**備註**] 標記內的文字。|

## <a name="example"></a>範例

### <a name="description"></a>描述

以下是簽章檔案中的典型 XML 檔批註。

### <a name="code"></a>程式碼

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例顯示不含 XML 標記的替代方法。 在此範例中, 批註中的完整文字會被視為摘要。 請注意, 如果您未明確指定摘要標記, 則不應指定其他標記, 例如**param**或傳回標記  。

### <a name="code"></a>程式碼

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [編譯器選項](compiler-options.md)
