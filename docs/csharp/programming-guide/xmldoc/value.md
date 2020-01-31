---
title: <value> - C#程式設計指南
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793356"
---
# <a name="value-c-programming-guide"></a>\<值 > （C#程式設計手冊）

## <a name="syntax"></a>語法

```xml
<value>property-description</value>
```

## <a name="parameters"></a>參數

- `property-description`

  屬性的描述。

## <a name="remarks"></a>備註

\<value> 標記可讓您描述屬性所代表的值。 請注意，當您在 Visual Studio .NET 開發環境中透過程式碼精靈新增屬性時，會新增新屬性的 [\<summary>](./summary.md) 標記。 您接著應該手動新增 \<value> 標記，來描述屬性所代表的值。

使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 編譯可處理檔案的文件註解。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../index.md)
- [建議使用的檔註解標記](./recommended-tags-for-documentation-comments.md)
