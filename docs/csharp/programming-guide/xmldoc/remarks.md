---
title: '<remarks> -C # 程式設計指南'
description: 瞭解 XML <remarks> 的相片或視訊。 此標記用來新增類型的相關資訊，並補充以下列方式指定的資訊： <summary>.
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: d38905d100e24158e7a1412f6be9f01a7ced2382
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381498"
---
# <a name="remarks-c-programming-guide"></a>\<remarks>（C # 程式設計手冊）

## <a name="syntax"></a>語法

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>參數

- `Description`

  成員的描述。

## <a name="remarks"></a>備註

`<remarks>`標記是用來加入類型的相關資訊，並補充以指定的資訊 [\<summary>](./summary.md) 。 這項資訊會顯示在 [物件瀏覽器] 視窗中。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
