---
title: "名稱 &quot;&lt;名稱&gt;&quot; 未宣告 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
dev_langs:
- VB
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 81b6862a7f8ceb7998b2ea53336ed3af46b1db5f
ms.lasthandoff: 03/13/2017

---
# <a name="name-39ltnamegt39-is-not-declared"></a>名稱 '&lt;名稱&gt;' 未宣告
陳述式參考程式設計項目，但編譯器找不到具有相同名稱的項目。  
  
 **錯誤識別碼︰** BC30451  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查參考陳述式中的名稱拼寫。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]不區分大小寫，但其他的拼字變化會視為完全不同的名稱。 請注意，底線 (`_`) 是名稱的一部分，因此也是拼字的一部分。  
  
2.  請檢查您是否具有成員存取運算子 (`.`) 之間的物件和其成員。 例如，如果您有<xref:System.Windows.Forms.TextBox>控制項，名為`TextBox1`，以存取其<xref:System.Windows.Forms.TextBoxBase.Text%2A>屬性應該輸入`TextBox1.Text`。</xref:System.Windows.Forms.TextBoxBase.Text%2A> </xref:System.Windows.Forms.TextBox> 如果您改為輸入 `TextBox1Text`，便會建立不同的名稱。  
  
3.  如果拼字正確，且任何物件的成員存取的語法正確，請確認已宣告的項目。 如需詳細資訊，請參閱[宣告項目](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)。  
  
4.  如果已宣告的程式設計項目，請檢查它位於範圍內。 如果參考陳述式外部宣告的程式設計項目區域中，您可能需要限定的項目名稱。 如需詳細資訊，請參閱[Visual Basic 中的範圍](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。  
  
## <a name="see-also"></a>另請參閱  
 [宣告和常數摘要](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)   
 [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
