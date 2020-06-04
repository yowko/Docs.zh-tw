---
title: 如何：建立 XML 文件
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 1421cc85beba42b3cf3656c34b1d02347fbaf164
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403235"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>如何：在 Visual Basic 中建立 XML 文件

這個範例會示範如何將 XML 檔批註加入至您的程式碼。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a>若要建立類型或成員的 XML 檔

1. 在 [程式**代碼編輯器**] 中，將游標放在您想要建立檔的類型或成員上的那一行。

2. 輸入 `'''` （三個單引號）。

    在程式**代碼編輯器**中，會加入類型或成員的 XML 基本架構。

3. 在適當的標記之間新增描述性資訊。

    > [!NOTE]
    > 如果您在 XML 檔區塊內新增額外的行，則每一行必須以開頭 `'''` 。

4. 使用新的 XML 檔批註，加入使用類型或成員的其他程式碼。

    IntelliSense 會顯示 \<summary> 標記中類型或成員的文字。

5. 編譯器代碼，以產生包含檔批註的 XML 檔案。 如需詳細資訊，請參閱[-doc](../../reference/command-line-compiler/doc.md)。

## <a name="see-also"></a>另請參閱

- [使用 XML 加入程式碼註解](documenting-your-code-with-xml.md)
- [XML 註解標籤](../../language-reference/xmldoc/index.md)
- [-doc](../../reference/command-line-compiler/doc.md)
