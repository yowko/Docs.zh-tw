---
title: <typeparam> - C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793358"
---
# <a name="typeparam-c-programming-guide"></a>\<類型參數>（C# 程式設計指南）

## <a name="syntax"></a>語法

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a>參數

- `name`

  型別參數的名稱。 以雙引號 (" ") 將名稱括起來。

- `description`

  型別參數的描述。

## <a name="remarks"></a>備註

`<typeparam>` 標記應該用於泛型型別或方法宣告的註解中，以描述型別參數。 新增泛型型別或方法之每個型別參數的標記。

如需詳細資訊，請參閱[泛型](../generics/index.md)。

`<typeparam>` 標記的文字將會顯示於 IntelliSense，即 [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) (物件瀏覽器視窗) 程式碼註解 Web 報告。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)編譯，以處理檔的文檔注釋。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../../language-reference/index.md)
- [C# 程式設計指南](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
