---
title: '<typeparamref>-C # 程式設計指南'
description: 瞭解 XML <typeparamref> 標記。 此標記可讓檔檔案的取用者以某種不同的方式來格式化單字，例如以斜體表示。
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: a39e896f1242452c7bcc94faa1e7ef3086ae2149
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380718"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref>（C # 程式設計手冊）

## <a name="syntax"></a>語法

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>參數

- `name`

  型別參數的名稱。 以雙引號 (" ") 將名稱括起來。

## <a name="remarks"></a>備註

如需泛型型別和方法中型別參數的詳細資訊，請參閱[泛型](../generics/index.md)。

使用這個標記，讓文件檔案的取用者以某種明顯方式格式化單字，例如斜體。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
