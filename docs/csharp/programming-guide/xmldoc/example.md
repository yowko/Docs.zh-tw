---
title: <example> - C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: 615eccbc427b6a5bbbed061acd0c8b0b9be7f46c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789808"
---
# <a name="example-c-programming-guide"></a>\<示例>（C# 程式設計指南）

## <a name="syntax"></a>語法

```xml
<example>description</example>
```

## <a name="parameters"></a>參數

- `description`

  程式碼範例的描述。

## <a name="remarks"></a>備註

\<example> 標記可讓您指定如何使用方法或其他程式庫成員的範例。 這通常涉及使用[\<代碼>](./code.md)標記。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)編譯，以處理檔的文檔注釋。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
