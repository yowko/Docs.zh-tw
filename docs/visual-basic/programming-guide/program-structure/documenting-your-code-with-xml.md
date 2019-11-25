---
title: 使用 XML 加入程式碼註解
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: bdf0da7a8acc919e4a1d66b81e30c9ed912dd321
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347447"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>使用 XML 在程式碼中加入文件 (Visual Basic)

In Visual Basic, you can document your code using XML

## <a name="xml-documentation-comments"></a>XML 文件註解

Visual Basic provides an easy way to automatically create XML documentation for projects. You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks. With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension. 如需詳細資訊，請參閱 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)。

The XML file can be consumed or otherwise manipulated as XML. This file is located in the same directory as the output .exe or .dll file of your project.

XML documentation starts with `'''`. 這些註解在處理時有一些限制：

- 文件必須是語式正確的 XML。 If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.

- 開發人員可以自由建立自己的標記集合。 There is a recommended set of tags (see "Related Sections" in this topic). 其中一些建議的標記具有特殊意義：

  - \<param> 標記是用來描述參數。 如果使用，編譯器會驗證參數存在，而且所有參數在文件中都有描述。 If the verification fails, the compiler issues a warning.

  - `cref` 屬性可以附加至任何標記，以提供程式碼項目的參考。 編譯器會驗證此程式碼項目存在。 If the verification fails, the compiler issues a warning. The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.

  - The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.

## <a name="related-sections"></a>相關章節

For details on creating an XML file with documentation comments, see the following topics:

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

- [處理 XML 檔案](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [Visual Studio 中的 XML 工具](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>請參閱

- [使用 Visual Basic 開發應用程式](../../../visual-basic/developing-apps/index.md)
- [Visual Basic 程式設計指南](../../../visual-basic/programming-guide/index.md)
