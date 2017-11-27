---
title: "用來做為選擇性參數類型的泛型參數必須受到類別條件約束"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords: BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a13ea66f12e54db4e585577e20e1f5396669f1a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>用來做為選擇性參數類型的泛型參數必須受到類別條件約束
程序的宣告會使用不限於是參考類型的型別參數的選擇性參數。  
  
 您一律必須提供每個選擇性參數的預設值。 如果參數是參考類型，選擇性的值必須是`Nothing`，這是任何參考類型的有效值。 不過，如果參數是實值類型，該類型必須是由 Visual Basic 預先定義的基本資料類型。 這是因為複合值型別，例如使用者定義的結構，具有沒有有效的預設值。  
  
 當您使用的型別參數的選擇性參數時，您必須保證它是參考類型，可避免沒有有效的預設值的實值類型。 這表示您必須將限制型別參數與`Class`關鍵字或特定類別的名稱。  
  
 **錯誤 ID:** BC32124  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   限制類型參數僅接受參考類型，或請勿使用它在選擇性參數。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [類型清單](../../../visual-basic/language-reference/statements/type-list.md)  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
 [選擇性參數](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)
