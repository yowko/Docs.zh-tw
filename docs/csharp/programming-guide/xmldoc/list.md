---
title: '<list> -C # 程式設計指南'
description: 瞭解 XML <list> 的相片或視訊。 此標記用來建立資料表和定義、以點符或編號的清單，方法是使用 ' item ' 區塊。
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 361c2e6f343554a9b8519c3b2e41219b209e682d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381862"
---
# <a name="list-c-programming-guide"></a>\<list>（C # 程式設計手冊）

## <a name="syntax"></a>語法

```xml
<list type="bullet|number|table">
    <listheader>
        <term>term</term>
        <description>description</description>
    </listheader>
    <item>
        <term>term</term>
        <description>description</description>
    </item>
</list>
```

## <a name="parameters"></a>參數

- `term`

  要定義的詞彙，可定義於 `description` 中。

- `description`

  項目符號或編號清單中的項目或者 `term` 的定義。
  
## <a name="remarks"></a>備註

`<listheader>`區塊是用來定義資料表或定義清單的標題資料列。 定義資料表時，您只需要提供標題中詞彙的項目。

清單中的每個專案都是以 `<item>` 區塊來指定。 建立定義清單時，您需要同時指定 `term` 和 `description`。 不過，針對資料表、項目符號清單或編號清單，您只需要提供 `description` 的項目。

清單或資料表可以視需要擁有多個 `<item>` 區塊。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
