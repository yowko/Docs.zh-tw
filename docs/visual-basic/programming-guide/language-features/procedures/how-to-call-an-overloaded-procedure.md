---
title: 如何：呼叫多載程序
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 68b8a9898cba846b63ed8ce9d8329516f12e90cb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075170"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>如何：呼叫多載程序 (Visual Basic)

多載程式的優點是可以彈性地呼叫。 呼叫程式碼可以取得傳遞給程式所需的資訊，然後呼叫單一程式名稱，不論其傳遞的引數為何。  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>呼叫已定義一個以上版本的程式  
  
1. 在呼叫程式碼中，決定要傳遞給程式的資料。  
  
2. 以一般方式撰寫程序呼叫，並將資料呈現在引數清單中。 請確定引數符合為程式所定義的其中一個版本中的參數清單。  
  
3. 您不需要決定要呼叫的程式版本。 Visual Basic 會將控制項傳遞至符合您引數清單的版本。  
  
     下列範例會呼叫 `post` [如何：定義程式的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)中所宣告的程式。 它會取得客戶識別、判斷它是 `String` 或 `Integer` ，然後在任何一種情況下呼叫相同的程式。  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [程序多載化](./procedure-overloading.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [如何：定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載化程序的考慮因素](./considerations-in-overloading-procedures.md)
- [多載解析](./overload-resolution.md)
- [多載](../../../language-reference/modifiers/overloads.md)
