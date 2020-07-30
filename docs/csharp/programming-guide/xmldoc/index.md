---
title: 'XML 檔批註-c # 程式設計指南'
description: 瞭解 XML 檔批註。 您可以藉由在特殊批註欄位中包含 XML 元素，來建立程式碼的檔。
ms.date: 07/20/2015
f1_keywords:
- cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
ms.openlocfilehash: fbdeb53331d9fc63d24a3322ea13863d7c0a3630
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381875"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>XML 檔批註（c # 程式設計手冊）

在 c # 中，您可以建立程式碼的檔，方法是將原始程式碼中的 XML 專案（以三個斜線表示）直接包含在程式碼區塊中（例如，在批註所參考的程式碼區塊之前）。

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

當您使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)選項進行編譯時，編譯器會搜尋原始程式碼中的所有 xml 標記，並建立 xml 檔檔。 若要依據編譯器產生的檔案來建立最終文件，您可以建立自訂工具，或者是使用 [DocFX](https://dotnet.github.io/docfx/) 或 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類工具。

若要參考 XML 項目，例如，您的函式處理要在 XML 文件註解中描述的特定 XML 項目，您可以使用標準引號機制 (`<` 和 `>`)。  若要參照程式碼參考 (`cref`) 項目中的泛型識別碼，您可以使用逸出字元 (例如 `cref="List&lt;T&gt;"`) 或大括號 (`cref="List{T}"`)。  視為特殊案例的情形是，編譯器將大括號剖析為角括號，如此在參考泛型識別項時，文件註解撰寫起來就變得不那麼複雜。

> [!NOTE]
> XML 文件註解並不是中繼資料，這些註解不會包含在編譯的組件內，因此不能透過反映存取。

## <a name="in-this-section"></a>本節內容

- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)

- [處理 XML 檔案](./processing-the-xml-file.md)

- [文件標籤的分隔符號](./delimiters-for-documentation-tags.md)

- [如何使用 XML 文件功能](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a>相關章節

如需詳細資訊，請參閱

- [-doc （處理檔批註）](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
