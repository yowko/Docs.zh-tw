---
title: '<see>-C # 程式設計指南'
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 0f10feb0931c6d38c817fdecb925f68d439abb59
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287242"
---
# <a name="see-c-programming-guide"></a>\<see>（C # 程式設計手冊）

## <a name="syntax"></a>語法

```xml
<see cref="member"/>
```

## <a name="parameters"></a>參數

- cref = " `member` "

  可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。 將 *member* 置於雙引號 (" ") 內。

## <a name="remarks"></a>備註

`<see>`標記可讓您指定文字中的連結。 用 [\<seealso>](./seealso.md) 來指示文字應該放在 [另請參閱] 區段中。 使用 [cref 屬性](./cref-attribute.md)，建立程式碼項目之文件頁面的內部超連結。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。

下列範例會顯示 `<see>` 摘要區段內的標記。

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
