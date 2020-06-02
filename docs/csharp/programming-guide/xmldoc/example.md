---
title: '<example> -C # 程式設計指南'
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: e8d26f82562cc5140662f5b32ea9fedf5481d8f8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287377"
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
