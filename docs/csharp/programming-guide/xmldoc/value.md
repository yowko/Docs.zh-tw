---
title: <value> - C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793356"
---
# <a name="value-c-programming-guide"></a>\<值>（C# 程式設計指南）

## <a name="syntax"></a>語法

```xml
<value>property-description</value>
```

## <a name="parameters"></a>參數

- `property-description`

  屬性的描述。

## <a name="remarks"></a>備註

\<value> 標記可讓您描述屬性所代表的值。 請注意，當您在 Visual Studio .NET 開發環境中通過代碼嚮導添加屬性時，它將為新屬性添加[\<摘要>](./summary.md)標記。 您接著應該手動新增 \<value> 標記，來描述屬性所代表的值。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)編譯，以處理檔的文檔注釋。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
