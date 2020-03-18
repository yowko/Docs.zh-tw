---
title: <remarks> - C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793378"
---
# <a name="remarks-c-programming-guide"></a>\<注釋>（C# 程式設計指南）

## <a name="syntax"></a>語法

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>參數

- `Description`

  成員的描述。

## <a name="remarks"></a>備註

注釋\<>標記用於添加有關類型的資訊，以[\<摘要>](./summary.md)指定的資訊。 這項資訊會顯示在 [物件瀏覽器] 視窗中。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)編譯，以處理檔的文檔注釋。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
