---
title: "變數 &quot;&lt;variablename&gt;&quot; 已在指派值之前使用 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
dev_langs:
- VB
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 10
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
ms.openlocfilehash: 7ad1f392fae2f90e366277b7b531d96011648866
ms.lasthandoff: 03/13/2017

---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a>變數 '&lt;variablename&gt;' 已在指派值之前使用
變數 '\<variablename >' 已在指派值之前使用。 可能會在執行階段產生 null 參考例外狀況。  
  
 必須至少一個可能的路徑，在讀取變數之前的任何值指派給它的程式碼。  
  
 如果變數從未獲派值，則會持有其資料類型的預設值。 參考資料型別，該預設值是[Nothing](../../../visual-basic/language-reference/nothing.md)。 讀取的值為參考變數`Nothing`可能會導致<xref:System.NullReferenceException>在某些情況下。</xref:System.NullReferenceException>  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告，或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC42104  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   檢查控制項流程邏輯，並確定變數具有有效的值，再將控制項傳遞至讀取它的任何陳述式。  
  
-   若要保證變數的有效值方法之一是初始化為其宣告的一部分。 請參閱中的 「 初始化 」 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [變數的疑難排解](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
