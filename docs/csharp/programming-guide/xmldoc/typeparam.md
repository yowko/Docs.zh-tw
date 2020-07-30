---
title: '<typeparam> -C # 程式設計指南'
description: 瞭解 XML <typeparam> 的相片或視訊。 這個標記用於泛型型別或方法宣告的批註中，以描述型別參數。
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 5e5333e384e8c77b500f74ab7c6038146df6e2c0
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380783"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam>（C # 程式設計手冊）

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

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../../language-reference/index.md)
- [C# 程式設計手冊](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
