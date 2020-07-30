---
title: '<returns> -C # 程式設計指南'
description: 瞭解 XML <returns> 的相片或視訊。 此標記會用於方法宣告的批註中，以描述傳回值。
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: e461d46df619a351048ae7942e59847d39e490f9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381394"
---
# <a name="returns-c-programming-guide"></a>\<returns>（C # 程式設計手冊）

## <a name="syntax"></a>語法

```xml
<returns>description</returns>
```

## <a name="parameters"></a>參數

- `description`

  傳回值的描述。

## <a name="remarks"></a>備註

`<returns>`標記應該用於方法宣告的批註中，以描述傳回值。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
