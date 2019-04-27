---
title: XML 文件 (F#)
description: 了解支援F#從註解產生文件。
ms.date: 05/16/2016
ms.openlocfilehash: c5305dea8832112644710b2863269ef00feddd10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902170"
---
# <a name="xml-documentation"></a>XML 文件

您可以產生從三個斜線 （/ /） 的文件程式碼中的註解F#。 XML 註解可以在程式碼檔 (.fs) 或簽章 (.fsi) 檔案中的宣告之前。

## <a name="generating-documentation-from-comments"></a>從註解產生文件

中的支援F#從註解產生文件是以其他.NET Framework 語言相同。 如同其他.NET Framework 語言， [-doc 編譯器選項](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04)可讓您產生 XML 檔案，其中包含您可以使用一種工具，例如轉換文件的資訊[DocFX](https://dotnet.github.io/docfx/)或[Sandcastle](https://github.com/EWSoftware/SHFB)。 通常以其他.NET Framework 語言撰寫的組件搭配使用所設計的工具所產生的文件時產生的 Api 為基礎的編譯形式檢視F#建構。 除非工具是專門為了支援F#，這些工具所產生的文件不符合F#檢視的 API。

如需如何從 XML 產生文件的詳細資訊，請參閱[XML 文件註解&#40;C&#35;程式設計指南&#41;](https://msdn.microsoft.com/library/b2s063f7)。

## <a name="recommended-tags"></a>建議的標記

有兩種方式可撰寫 XML 文件註解。 其中一個是只要直接在三個斜線註解中撰寫的文件，而不使用 XML 標記。 如果您這麼做時，整個註解文字會被視為緊接在後面的程式碼建構的摘要文件中。 當您想要撰寫的簡短摘要每個建構時，請使用這個方法。 另一種方法是使用 XML 標記來提供更結構化文件。 第二個方法可讓您指定個別的簡短摘要、 其他備註、 文件針對每個參數和型別參數和擲回的例外狀況和傳回值的描述資訊。 下表描述中可以辨識的 XML 標記F#XML 程式碼註解。

|標記語法|描述|
|----------|-----------|
|**\<c\>**_text_**\</c\>**|指定*文字*是程式碼。 這個標記可以供文件產生器，以適用於程式碼的字型顯示文字。|
|**\<summary\>**_text_**\</summary\>**|指定*文字*是簡短的程式項目。 描述通常是一或兩個句子。|
|**\<remarks\>**_text_**\</remarks\>**|指定*文字*包含的程式元素的增補資訊。|
|**\<param name="**_name_**"\>**_description_**\</param\>**|指定的名稱和函式或方法參數的描述。|
|**\<typeparam name="**_name_**"\>**_description_**\</typeparam\>**|指定的名稱和型別參數的描述。|
|**\<returns\>**_text_**\</returns\>**|指定*文字*描述函式或方法的傳回值。|
|**\<exception cref="**_type_**"\>**_description_**\</exception\>**|指定可以產生的例外狀況的情況下它會擲回的類型。|
|**\<see cref="**_reference_**"\>**_text_**\</see\>**|指定內嵌連結至另一個程式項目。 *參考*是它會出現在 XML 文件檔案的名稱。 *文字*是連結中所顯示的文字。|
|**\<seealso cref="**_reference_**"/\>**|指定另一種類型的文件的 < 另請參閱連結。 *參考*是它會出現在 XML 文件檔案的名稱。 另請參閱通常會出現在文件頁面底部的連結。|
|**\<para\>**_text_**\</para\>**|指定文字的段落。 這用來分隔文字內**備註**標記。|

## <a name="example"></a>範例

### <a name="description"></a>描述

以下是典型的 XML 文件註解，在簽章檔案中。

### <a name="code"></a>程式碼

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例顯示的替代方法，而不需要 XML 標記。 在此範例中，完整的註解中的文字會被視為摘要。 請注意，如果您未明確指定摘要的標記，您應該不指定其他的標記，例如**param**或是**傳回**標記。

### <a name="code"></a>程式碼

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [編譯器選項](compiler-options.md)
