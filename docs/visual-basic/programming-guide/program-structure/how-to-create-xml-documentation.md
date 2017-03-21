---
title: "如何︰ 在 Visual Basic 中建立 XML 文件 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML comments
- XML documentation, creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 363a20c0fce05566b61e764d05932a9dfb779f90
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>如何：在 Visual Basic 中建立 XML 文件
這個範例示範如何將 XML 文件註解加入至您的程式碼。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>若要建立 XML 文件類型或成員  
  
1.  在**程式碼編輯器**，將游標位置的上一行類型或成員的項目，您要建立文件。  
  
2.  型別`'''`（三個單引號）。  
  
     型別或成員的 XML 基本架構中加入**程式碼編輯器**。  
  
3.  新增適當的標記之間的描述性資訊。  
  
    > [!NOTE]
    >  如果您新增其他行的 XML 文件區塊內，每一行開頭必須`'''`。  
  
4.  新增額外的程式碼會使用新的 XML 文件註解的型別或成員。  
  
     IntelliSense 中顯示的文字\<摘要 > 標記的型別或成員。  
  
5.  編譯程式碼以產生包含文件註解的 XML 檔案。 如需詳細資訊，請參閱[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [記錄與 XML 程式碼](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)   
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
