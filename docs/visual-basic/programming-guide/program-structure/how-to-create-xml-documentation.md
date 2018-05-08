---
title: 如何：在 Visual Basic 中建立 XML 文件
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 7fb56da8a28367a6dcd5e28f208b4519510d7d95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>如何：在 Visual Basic 中建立 XML 文件
這個範例示範如何將 XML 文件註解加入至您的程式碼。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>若要建立 XML 文件類型或成員  
  
1.  在**程式碼編輯器**，您的游標放在您要建立的文件類型或成員的上一行。  
  
2.  型別`'''`（三個單一-引號）。  
  
     型別或成員的 XML 基本架構就會加入**程式碼編輯器**。  
  
3.  加入適當的標記之間的描述性資訊。  
  
    > [!NOTE]
    >  如果您新增其他行的 XML 文件區塊內，每一行的開頭必須`'''`。  
  
4.  加入新的 XML 文件註解中使用的型別或成員的其他程式碼。  
  
     IntelliSense 會顯示從文字\<摘要 > 標記的型別或成員。  
  
5.  編譯程式碼來產生包含文件註解的 XML 檔案。 如需詳細資訊，請參閱 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 XML 加入程式碼註解](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
