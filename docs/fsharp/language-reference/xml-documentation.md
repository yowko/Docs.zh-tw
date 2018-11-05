---
title: XML 文件 (F#)
description: 從註解產生文件，以了解 F# 中的支援。
ms.date: 05/16/2016
ms.openlocfilehash: 1a4cb132e65b630821e5eb2b39276c1de99aff80
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "45641621"
---
# <a name="xml-documentation"></a>XML 文件

您可以產生從三個斜線 （/ /） 的文件程式碼在 F# 中的註解。 XML 註解可以在程式碼檔 (.fs) 或簽章 (.fsi) 檔案中的宣告之前。

## <a name="generating-documentation-from-comments"></a>從註解產生文件

F# 中產生文件註解中的支援處於相同其他.NET Framework 語言。 如同其他.NET Framework 語言， [-doc 編譯器選項](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04)可讓您產生 XML 檔案，其中包含您可以使用 Sandcastle 等工具來轉換文件的資訊。 通常以其他.NET Framework 語言撰寫的組件搭配使用所設計的工具所產生的文件產生的檢視以 F# 建構之編譯形式為基礎的 Api。 除非工具是專門為了支援 F#，這些工具所產生的文件不符合 [F#] 檢視的 API。

如需如何從 XML 產生文件的詳細資訊，請參閱[XML 文件註解&#40;C&#35;程式設計指南&#41;](https://msdn.microsoft.com/library/b2s063f7)。

## <a name="recommended-tags"></a>建議的標記

有兩種方式可撰寫 XML 文件註解。 其中一個是只要直接在三個斜線註解中撰寫的文件，而不使用 XML 標記。 如果您這麼做時，整個註解文字會被視為緊接在後面的程式碼建構的摘要文件中。 當您想要撰寫的簡短摘要每個建構時，請使用這個方法。 另一種方法是使用 XML 標記來提供更結構化文件。 第二個方法可讓您指定個別的簡短摘要、 其他備註、 文件針對每個參數和型別參數和擲回的例外狀況和傳回值的描述資訊。 下表描述會辨識為 F# XML 程式碼註解的 XML 標記。

|標記語法|描述|
|----------|-----------|
|**&lt;c&gt;***文字***&lt;/c&gt;**|指定*文字*是程式碼。 這個標記可以供文件產生器，以適用於程式碼的字型顯示文字。|
|**&lt;摘要&gt;***文字*** &lt; /摘要&gt;**|指定*文字*是簡短的程式項目。 描述通常是一或兩個句子。|
|**&lt;備註&gt;***文字***&lt;/&gt;**|指定*文字*包含的程式元素的增補資訊。|
|**&lt;參數名稱 ="***名稱***"&gt;***描述***&lt;/param&gt;**|指定的名稱和函式或方法參數的描述。|
|**&lt;typeparam 名稱 ="***名稱***"&gt;***描述***&lt;/typeparam&gt;**|指定的名稱和型別參數的描述。|
|**&lt;會傳回&gt;***文字*** &lt; /returns>&gt;**|指定*文字*描述函式或方法的傳回值。|
|**&lt;例外狀況 cref ="***型別***"&gt;***描述***&lt;/exception&gt;**|指定可以產生的例外狀況的情況下它會擲回的類型。|
|**&lt;cref ="***參考***"&gt;***文字*** &lt; /請參閱&gt;**|指定內嵌連結至另一個程式項目。 *參考*是它會出現在 XML 文件檔案的名稱。 *文字*是連結中所顯示的文字。|
|**&lt;seealso cref ="***參考***"/&gt;**|指定另一種類型的文件的 < 另請參閱連結。 *參考*是它會出現在 XML 文件檔案的名稱。 另請參閱通常會出現在文件頁面底部的連結。|
|**&lt;para&gt;***文字***&lt;/para&gt;**|指定文字的段落。 這用來分隔文字內**備註**標記。|

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
