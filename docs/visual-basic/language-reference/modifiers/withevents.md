---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 41d38dcb3f44ccda19253adcd39401b0ac8dfb02
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647646"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
指定一或多個宣告的成員變數會參照可引發事件的類別的執行個體。  
  
## <a name="remarks"></a>備註  
 當使用定義的變數`WithEvents`，您可以宣告方式指定，則方法會處理使用的變數的事件`Handles`關鍵字。  
  
 您可以使用`WithEvents`只能在類別或模組層級。 這表示的宣告內容`WithEvents`變數必須是類別或模組，而且不能是原始程式檔、 命名空間、 結構或程序。  
  
 您無法使用`WithEvents`結構成員上。  
  
 您可以宣告個別的變數，不陣列 — 使用`WithEvents`。  
  
## <a name="rules"></a>規則  
  
- **項目型別。** 您必須宣告`WithEvents`變數是物件變數，以便它們可以接受類別執行個體。 不過，您無法將它們宣告為`Object`。 您必須宣告為可引發事件的特定類別。  
  
 `WithEvents`修飾詞，請使用此內容中：[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
