---
title: XML 文件 (F#)
description: 了解支援F#從註解產生文件。
ms.date: 05/16/2016
ms.openlocfilehash: a1fb5eb682ff1188136b31b64e2d7c537d2c9a0e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153640"
---
# <a name="xml-documentation"></a>XML 文件

您可以產生從三個斜線 （/ /） 的文件程式碼中的註解F#。 XML 註解可以在程式碼檔 (.fs) 或簽章 (.fsi) 檔案中的宣告之前。

## <a name="generating-documentation-from-comments"></a>從註解產生文件

中的支援F#從註解產生文件是以其他.NET Framework 語言相同。 如同其他.NET Framework 語言， [-doc 編譯器選項](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04)可讓您產生 XML 檔案，其中包含您可以使用 Sandcastle 等工具來轉換文件的資訊。 通常以其他.NET Framework 語言撰寫的組件搭配使用所設計的工具所產生的文件時產生的 Api 為基礎的編譯形式檢視F#建構。 除非工具是專門為了支援F#，這些工具所產生的文件不符合F#檢視的 API。

如需如何從 XML 產生文件的詳細資訊，請參閱[XML 文件註解&#40;C&#35;程式設計指南&#41;](https://msdn.microsoft.com/library/b2s063f7)。

## <a name="recommended-tags"></a>建議的標記

有兩種方式可撰寫 XML 文件註解。 其中一個是只要直接在三個斜線註解中撰寫的文件，而不使用 XML 標記。 如果您這麼做時，整個註解文字會被視為緊接在後面的程式碼建構的摘要文件中。 當您想要撰寫的簡短摘要每個建構時，請使用這個方法。 另一種方法是使用 XML 標記來提供更結構化文件。 第二個方法可讓您指定個別的簡短摘要、 其他備註、 文件針對每個參數和型別參數和擲回的例外狀況和傳回值的描述資訊。 下表描述中可以辨識的 XML 標記F#XML 程式碼註解。

|標記語法|描述|
|----------|-----------|
|**\<c\>**_文字_**\</c\>**|指定*文字*是程式碼。 這個標記可以供文件產生器，以適用於程式碼的字型顯示文字。|
|**\<摘要\>**_文字_ **\< /摘要\>**|指定*文字*是簡短的程式項目。 描述通常是一或兩個句子。|
|**\<備註\>**_文字_**\</\>**|指定*文字*包含的程式元素的增補資訊。|
|**\<參數名稱 ="**_名稱_**」\>**_描述_**\</param\>**|指定的名稱和函式或方法參數的描述。|
|**\<typeparam 名稱 ="**_名稱_**」\>**_描述_**\</typeparam\>**|指定的名稱和型別參數的描述。|
|**\<會傳回\>**_文字_ **\< /returns>\>**|指定*文字*描述函式或方法的傳回值。|
|**\<例外狀況 cref ="**_型別_**」\>**_描述_**\</exception\>**|指定可以產生的例外狀況的情況下它會擲回的類型。|
|**\<cref ="**_參考_**」\>**_文字_ **\< /請參閱\>**|指定內嵌連結至另一個程式項目。 *參考*是它會出現在 XML 文件檔案的名稱。 *文字*是連結中所顯示的文字。|
|**\<seealso cref ="**_參考_**"/\>**|指定另一種類型的文件的 < 另請參閱連結。 *參考*是它會出現在 XML 文件檔案的名稱。 另請參閱通常會出現在文件頁面底部的連結。|
|**\<para\>**_文字_**\</para\>**|指定文字的段落。 這用來分隔文字內**備註**標記。|

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
