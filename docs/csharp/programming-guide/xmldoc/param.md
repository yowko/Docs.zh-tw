---
title: '<param> -C # 程式設計指南'
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 396ed716c246091a674268020261069f36dd2be8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287320"
---
# <a name="param-c-programming-guide"></a>\<param>（C # 程式設計手冊）

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

`<param>`標記應該用於方法宣告的批註中，以描述方法的其中一個參數。 若要記錄多個參數，請使用多個 `<param>` 標記。

標記的文字 `<param>` 會顯示在 IntelliSense、物件瀏覽器和程式碼批註 Web 報告中。

使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。

## <a name="example"></a>範例

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
