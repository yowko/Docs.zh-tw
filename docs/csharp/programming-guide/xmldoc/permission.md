---
title: <permission> - C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 4f76d28d5531c1b9f01fa950589407934cc1244a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093470"
---
# <a name="permission-c-programming-guide"></a>\<許可權>（C# 程式設計指南）

## <a name="syntax"></a>語法

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>參數

- cref = " `member`"

  可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。 member** 必須出現在雙引號 (" ") 內。

  有關如何創建對泛型型別的 cref 引用的資訊，請參閱[cref 屬性](./cref-attribute.md)。

- `description`

  成員存取權的描述。

## <a name="remarks"></a>備註

\<permission> 標記可讓您記載成員存取權。 <xref:System.Security.PermissionSet> 類別可讓您指定成員存取權。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)編譯，以處理檔的文檔注釋。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
