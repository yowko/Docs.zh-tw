---
title: '<para> -C # 程式設計指南'
description: 瞭解 XML <para> 的相片或視訊。 此標記可讓您將結構新增至另一個標記中的文字，例如 <summary>, <remarks>或 <returns>.
ms.date: 07/20/2015
f1_keywords:
- <para>
- para
helpviewer_keywords:
- <para> C# XML tag
- para C# XML tag
ms.assetid: c74b8705-29df-40b1-bff5-237492b0e978
ms.openlocfilehash: 146078bcb556b4085724ddcdac561ea868ab0481
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381849"
---
# <a name="para-c-programming-guide"></a>\<para>（C # 程式設計手冊）

## <a name="syntax"></a>語法

```xml
<para>content</para>
```

## <a name="parameters"></a>參數

- `content`

  段落的文字。

## <a name="remarks"></a>備註

`<para>`標記用於標記內（例如 [\<summary>](./summary.md) 、 [\<remarks>](./remarks.md) 或 [\<returns>](./returns.md) ），並可讓您將結構新增至文字。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。

## <a name="example"></a>範例

如需使用的範例，請參閱 [\<summary>](./summary.md) `<para>` 。

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
