---
title: XML 檔批註- C#程式設計指南
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
ms.openlocfilehash: f5a507bc35b0cc0a679fd055bfc255bb3cb9a090
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789787"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>XML 檔批註（C#程式設計手冊）

在C#中，您可以建立程式碼的檔，方法是將原始程式碼中的 XML 專案（以三個斜線表示）直接包含在程式碼區塊中，而這些專案是由批註所參考，例如。

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

- [建議使用的檔註解標記](./recommended-tags-for-documentation-comments.md)

- [處理 XML 檔案](./processing-the-xml-file.md)

- [檔標記的分隔符號](./delimiters-for-documentation-tags.md)

- [如何使用 XML 檔功能](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a>相關章節

如需詳細資訊，請參閱＜＞。

- [-doc （處理檔批註）](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../index.md)
