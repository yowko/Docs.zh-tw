---
title: '<example> -C # 程式設計指南'
description: 瞭解 XML <example> 的相片或視訊。 此標記可讓您指定如何使用方法或其他程式庫成員的範例。
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: dd529e8f2a54cf9086d0d8c555dd1adb70b99126
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381524"
---
# <a name="example-c-programming-guide"></a>\<example>（C # 程式設計手冊）

## <a name="syntax"></a>語法

```xml
<example>description</example>
```

## <a name="parameters"></a>參數

- `description`

  程式碼範例的描述。

## <a name="remarks"></a>備註

`<example>`標記可讓您指定如何使用方法或其他程式庫成員的範例。 這通常牽涉到使用 [\<code>](./code.md) 標記。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
