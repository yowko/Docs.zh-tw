---
title: 如何：在 Visual Basic 中建立 XML 文件
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 3dfec94a3dd1b8da5d371529b91b47f018bb3843
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527592"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>如何：在 Visual Basic 中建立 XML 文件
此範例示範如何將 XML 文件註解新增至您的程式碼。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>若要建立的型別或成員的 XML 文件  
  
1.  在 **程式碼編輯器**，您的游標放在上面類型或成員的項目，您要建立文件行。  
  
2.  型別`'''`（三個單引號）。  
  
     型別或成員的 XML 基本架構中新增**程式碼編輯器**。  
  
3.  新增適當的標記之間的描述性資訊。  
  
    > [!NOTE]
    >  如果您新增其他行，XML 文件區塊內，每一行的開頭必須`'''`。  
  
4.  新增額外的程式碼會使用新的 XML 文件註解中的型別或成員。  
  
     IntelliSense 會顯示從文字\<摘要 > 標記的型別或成員。  
  
5.  編譯程式碼以產生包含文件註解的 XML 檔案。 如需詳細資訊，請參閱 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 XML 加入程式碼註解](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
