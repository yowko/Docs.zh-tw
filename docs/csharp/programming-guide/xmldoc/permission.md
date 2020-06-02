---
title: '<permission> -C # 程式設計指南'
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: bb7172042f0b472d03c3fa2d9dbd0d4d4265076b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287268"
---
# <a name="permission-c-programming-guide"></a>\<permission>（C # 程式設計手冊）

## <a name="syntax"></a>語法

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>參數

- cref = " `member`"

  可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。 member** 必須出現在雙引號 (" ") 內。

  如需有關如何建立泛型型別之 cref 參考的詳細資訊，請參閱[cref 屬性](./cref-attribute.md)。

- `description`

  成員存取權的描述。

## <a name="remarks"></a>備註

`<permission>`標記可讓您記錄成員的存取權。 <xref:System.Security.PermissionSet> 類別可讓您指定成員存取權。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
