---
title: '<c>-C # 程式設計指南'
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
ms.openlocfilehash: a09bcd069e2f85f4a21736cb218c42c0e481d70b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287463"
---
# <a name="c-c-programming-guide"></a>\<c>（C # 程式設計手冊）

## <a name="syntax"></a>語法

```xml
<c>text</c>
```

## <a name="parameters"></a>參數

- `text`

  您要指定為程式碼的文字。

## <a name="remarks"></a>備註

`<c>`標記可讓您指定描述中的文字應該標記為程式碼。 用 [\<code>](./code.md) 來指示多行作為程式碼。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
