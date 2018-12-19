---
title: XML 文件註解 - C# 程式設計指南
ms.custom: seodec18
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
ms.openlocfilehash: a2957150ace7dbf342047e88451e1e76e097f941
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235562"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>XML 文件註解 (C# 程式設計手冊)
在 Visual C# 中，您可以加入程式碼的文件，加入的方法是在原始程式碼中，於註解所參考程式碼區塊之前的特殊註解欄位 (以三個斜線表示) 中加入 XML 項目，例如：  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass {}  
```  
  
 當您使用 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 選項編譯時，編譯器將會搜尋原始程式碼中的所有 XML 標記，然後建立 XML 文件檔。 若要依據編譯器產生的檔案來建立最終文件，您可以建立自訂工具，或者是使用 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類工具。  
  
 若要參考 XML 項目，例如，您的函式處理要在 XML 文件註解中描述的特定 XML 項目，您可以使用標準引號機制 (`<` 和 `>`)。  若要參照程式碼參考 (`cref`) 項目中的泛型識別碼，您可以使用逸出字元 (例如 `cref="List&lt;T&gt;"`) 或大括號 (`cref="List{T}"`)。  視為特殊案例的情形是，編譯器將大括號剖析為角括號，如此在參考泛型識別項時，文件註解撰寫起來就變得不那麼複雜。  
  
> [!NOTE]
>  XML 文件註解並不是中繼資料，這些註解不會包含在編譯的組件內，因此不能透過反映存取。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [處理 XML 檔案](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [文件標籤的分隔符號](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [如何：使用 XML 文件功能](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊，請參閱:  
  
-   [/doc (處理文件註解)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
