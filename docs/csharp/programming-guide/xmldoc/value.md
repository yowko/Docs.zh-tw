---
title: '<value> -C # 程式設計指南'
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: bd6630a8d5894fda39ad289c8dd584f6d84e5490
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287190"
---
# <a name="value-c-programming-guide"></a>\<value>（C # 程式設計手冊）

## <a name="syntax"></a>語法

```xml
<value>property-description</value>
```

## <a name="parameters"></a>參數

- `property-description`

  屬性的描述。

## <a name="remarks"></a>備註

`<value>`標記可讓您描述屬性所代表的值。 當您透過 Visual Studio .NET 開發環境中的程式碼 wizard 加入屬性時，會加入 [\<summary>](./summary.md) 新屬性的標記。 接著，您應該手動加入 `<value>` 標記來描述屬性所代表的值。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
