---
title: 前置字元 &#39;。&#39;或 &#39; ！&#39;只可以出現 &#39;使用 &#39;陳述式
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 961f2d737123ab68b200d5fc7658cb81291a5de6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>前置字元 &#39;。&#39;或 &#39; ！&#39;只可以出現 &#39;使用 &#39;陳述式
句號 （.） 或驚嘆號 （！） 不是內部`With`區塊，就會發生在左邊沒有運算式。 成員存取 (`.`) 和字典成員存取 (`!`) 需要一個運算式來指定包含該成員的項目。 這必須立即出現左側子的存取，或做為目標的`With`記錄檔區塊內含成員存取。  
  
 **錯誤 ID:** BC30157  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確認`With`區塊已正確地格式化。  
  
2.  如果沒有任何`With`封鎖，請將運算式加入已定義的項目，包含成員的存取子，評估結果的左邊。  
  
## <a name="see-also"></a>另請參閱  
 [程式碼中的特殊字元](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [With...End With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
