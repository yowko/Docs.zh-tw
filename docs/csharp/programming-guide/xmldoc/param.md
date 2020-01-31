---
title: <param> - C#程式設計指南
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789765"
---
# <a name="param-c-programming-guide"></a>\<param > （C#程式設計手冊）

## <a name="syntax"></a>語法

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>參數

- `name`

  方法參數的名稱。 以雙引號 (" ") 將名稱括起來。

- `description`

  參數的描述。

## <a name="remarks"></a>備註

\<param> 標記應該在方法宣告的註解中用來描述參數的其中一個方法。 若要記錄多個參數，請使用多個 \<param > 標記。

\<param> 標記的文字將會顯示於 IntelliSense (即物件瀏覽器) 以及程式碼結構 Web 報告中。

使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 編譯可處理檔案的文件註解。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../index.md)
- [建議使用的檔註解標記](./recommended-tags-for-documentation-comments.md)
