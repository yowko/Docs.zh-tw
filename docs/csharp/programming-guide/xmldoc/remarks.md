---
title: '<remarks> -C # 程式設計指南'
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 739027786e02e559d86f990bf614e261b497c76f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287281"
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
