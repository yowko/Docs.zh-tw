---
title: "Name &#39;&lt;name&gt;&#39; is not declared | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30451"
  - "vbc30451"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30451"
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Name &#39;&lt;name&gt;&#39; is not declared
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

陳述式 \(Statement\) 參考某個程式設計項目，但編譯器 \(Compiler\) 找不到有相同名稱的項目。  
  
 **錯誤 ID：**BC30451  
  
### 若要更正這個錯誤  
  
1.  請檢查參考陳述式中的名稱拼寫是否正確無誤。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 不區分大小寫，但其他的拼寫變化會視為完全不同的名稱。  請注意底線 \(`_`\) 屬於名稱的一部分，因此也必須拼寫正確。  
  
2.  請檢查在物件及其成員之間是否有成員存取運算子 \(`.`\)。  例如，如果有 <xref:System.Windows.Forms.TextBox> 控制項名為 `TextBox1`，要存取其 <xref:System.Windows.Forms.TextBoxBase.Text%2A> 屬性時，您應該輸入 `TextBox1.Text`。  如果您輸入的卻是 `TextBox1Text`，就會建立另一個名稱。  
  
3.  如果拼寫正確無誤，而且任何物件成員存取的語法都正確，請確認已經宣告該項目。  如需詳細資訊，請參閱 [Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)。  
  
4.  如果已經宣告程式設計項目，請檢查該項目是否在範圍中。  如果參考陳述式位於宣告程式設計項目的區域以外，您可能需要限定該項目名稱。  如需詳細資訊，請參閱 [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。  
  
## 請參閱  
 [Declarations and Constants Summary](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)