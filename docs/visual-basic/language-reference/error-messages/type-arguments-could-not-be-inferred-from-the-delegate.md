---
title: 無法從委派推斷型別引數
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 57a3a24af32d9eb85a0f905aa3a73a956723b6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>無法從委派推斷型別引數
指派陳述式使用 `AddressOf` 將泛型程序的位址指派給委派，但未將任何類型引數提供給泛型程序。  
  
 通常，當您叫用泛型類型時，會針對泛型類型所定義的每個類型參數提供類型引數。 如果您未提供任何類型引數，編譯器會嘗試推斷要傳遞給類型參數的類型。 如果內容未提供足夠的資訊讓編譯器推斷類型，則會產生錯誤。  
  
 **錯誤 ID:** BC36564  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   在 `AddressOf` 運算式中指定泛型程序的類型引數。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [在 Visual Basic 中的泛型程序](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [類型清單](../../../visual-basic/language-reference/statements/type-list.md)  
 [擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
