---
title: <seealso> - C# 程式設計指南
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
ms.openlocfilehash: e24d5910ab21f01aebb5a32ce7646cf56886a81a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093457"
---
# <a name="seealso-c-programming-guide"></a>\<另請參閱>（C# 程式設計指南）

## <a name="syntax"></a>語法

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>參數

- cref = " `member`"

  可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。`member` 必須出現在雙引號 (" ") 內。

  有關如何創建對泛型型別的 cref 引用的資訊，請參閱[cref 屬性](./cref-attribute.md)。

## <a name="remarks"></a>備註

\<seealso> 標記可讓您指定要顯示在＜請參閱＞一節中的文字。 使用[\<請參閱>](./see.md)從文本中指定連結。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)編譯，以處理檔的文檔注釋。

## <a name="example"></a>範例

有關使用\<see 也>的示例，請參閱[\<摘要>。](./summary.md)

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
