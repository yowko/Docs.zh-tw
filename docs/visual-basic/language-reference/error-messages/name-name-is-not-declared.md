---
title: 名稱&#39;&lt;名稱&gt;&#39;未宣告
ms.date: 07/20/2015
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: e17017e84720a2581abc5115338352aacc02d473
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594815"
---
# <a name="name-39ltnamegt39-is-not-declared"></a>名稱&#39;&lt;名稱&gt;&#39;未宣告
陳述式參考了程式設計項目，但編譯器找不到具有相同名稱的項目。  
  
 **錯誤 ID:** BC30451  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查參考陳述式中的名稱拼寫。 Visual Basic 不區分大小寫，但拼字的任何其他變化會視為完全不同的名稱。 請注意，底線 (`_`) 是名稱的一部分，因此也是拼字的一部分。  
  
2.  檢查您是否有成員存取運算子 (`.`) 之間的物件和其成員。 例如，如果您有 <xref:System.Windows.Forms.TextBox> 控制項，名為 `TextBox1`，那麼要存取它的 <xref:System.Windows.Forms.TextBoxBase.Text%2A> 屬性，您應該輸入 `TextBox1.Text`。 如果您改為輸入 `TextBox1Text`，便會建立不同的名稱。  
  
3.  如果拼字正確，且任何物件成員存取語法正確，請確認已宣告項目。 如需詳細資訊，請參閱[宣告項目](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)。  
  
4.  如果已宣告的程式設計項目，請檢查它位於範圍內。 如果參考陳述式外部宣告的程式設計項目區域中，您可能需要限定項目名稱。 如需詳細資訊，請參閱[在 Visual Basic 中的範圍](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。  
  
## <a name="see-also"></a>另請參閱  
 [宣告和常數摘要](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
