---
title: '<seealso> -C # 程式設計指南'
description: 瞭解如何使用 XML <seealso> 的相片或視訊。 此標籤可讓您指定您可能想要出現在「另請參閱」一節中的文字。
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e8618ef352a4fa7f0fd4c88733c6568b0e12e376
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380640"
---
# <a name="seealso-c-programming-guide"></a>\<seealso>（C # 程式設計手冊）

## <a name="syntax"></a>語法

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>參數

- cref = " `member`"

  可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。`member` 必須出現在雙引號 (" ") 內。

  如需有關如何建立泛型型別之 cref 參考的詳細資訊，請參閱[cref 屬性](./cref-attribute.md)。

## <a name="remarks"></a>備註

標籤 `<seealso>` 可讓您指定您可能想要出現在 [另請參閱] 區段中的文字。 用 [\<see>](./see.md) 來指定文字內的連結。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。

## <a name="example"></a>範例

如需使用的範例，請參閱 [\<summary>](./summary.md) \<seealso> 。

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
