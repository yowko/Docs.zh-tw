---
title: 使用 XML 在程式碼中加入文件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 58c8716450fd8310b81050c86dc297c5b7527761
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524500"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>使用 XML 在程式碼中加入文件 (Visual Basic)

在 Visual Basic 中，您可以使用 XML 記錄您的程式碼

## <a name="xml-documentation-comments"></a>XML 文件註解

Visual Basic 提供簡單的方式來自動建立專案的 XML 檔。 您可以自動產生類型和成員的 XML 基本架構，然後提供摘要、每個參數的描述性檔，以及其他備註。 使用適當的設定時，XML 檔會自動發出至與您的專案同名的 XML 檔案和 .xml 副檔名。 如需詳細資訊，請參閱 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)。

您可以使用 xml 檔案，或以 XML 的方式操作。 這個檔案位於與專案的輸出 .exe 或 .dll 檔案相同的目錄中。

XML 檔的開頭為 `'''`。 這些註解在處理時有一些限制：

- 文件必須是語式正確的 XML。 如果 XML 的格式不正確，則會產生警告，而且檔檔案會包含批註，指出發生錯誤。

- 開發人員可以自由建立自己的標記集合。 有一組建議的標記（請參閱本主題中的「相關章節」）。 其中一些建議的標記具有特殊意義：

  - \<param> 標記是用來描述參數。 如果使用，編譯器會驗證參數存在，而且所有參數在文件中都有描述。 如果驗證失敗，編譯器會發出警告。

  - `cref` 屬性可以附加至任何標記，以提供程式碼項目的參考。 編譯器會驗證此程式碼項目存在。 如果驗證失敗，編譯器會發出警告。 在尋找 `cref` 屬性中所描述的類型時，編譯器也會遵循任何 `Imports` 語句。

  - Visual Studio 中的 IntelliSense 會使用 \<summary > 標記來顯示類型或成員的其他資訊。

## <a name="related-sections"></a>相關章節

如需有關建立含有檔批註之 XML 檔案的詳細資訊，請參閱下列主題：

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

- [處理 XML 檔案](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [Visual Studio 中的 XML 工具](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>請參閱

- [使用 Visual Basic 開發應用程式](../../../visual-basic/developing-apps/index.md)
- [Visual Basic 程式設計指南](../../../visual-basic/programming-guide/index.md)
