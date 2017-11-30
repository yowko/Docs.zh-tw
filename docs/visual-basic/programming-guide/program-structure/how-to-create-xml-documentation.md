---
title: "如何：在 Visual Basic 中建立 XML 文件"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 63b6485de5aba2ca49d54a057045bec2062d12dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
