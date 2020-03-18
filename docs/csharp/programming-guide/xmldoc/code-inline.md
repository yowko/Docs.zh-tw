---
title: <c>- C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: d5b28ee6db52d191f8454592d792ac0a1e1dc73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793459"
---
# <a name="c-c-programming-guide"></a>\<c>（C# 程式設計指南）

## <a name="syntax"></a>語法

```xml
<c>text</c>
```

## <a name="parameters"></a>參數

- `text`

  您要指定為程式碼的文字。

## <a name="remarks"></a>備註

\<c> 標記可讓您在一段描述中指出應該標記為程式碼的文字。 使用[\<代碼>](./code.md)指示多行為代碼。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)編譯，以處理檔的文檔注釋。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
