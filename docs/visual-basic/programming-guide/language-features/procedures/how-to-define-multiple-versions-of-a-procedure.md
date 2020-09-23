---
title: 如何：定義程序的多個版本
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 2661603ba33dd0bc28ac1a192794a4534225b641
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071634"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>如何：定義程序的多個版本 (Visual Basic)

您可以使用相同的名稱，但針對每個版本使用不同的參數清單，在多個版本中*定義程式。* 多載的目的是要定義多個密切相關的程式版本，而不需要依名稱來區分。  
  
 如需詳細資訊，請參閱 [Procedure Overloading](./procedure-overloading.md)。  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>若要定義程式的多個版本  
  
1. `Sub` `Function` 針對您要定義的每個程式版本，撰寫或宣告語句。 在每個宣告中使用相同的程式名稱。  
  
2. `Sub`在每個宣告中的或關鍵字之前加上 `Function` [Overloads](../../../language-reference/modifiers/overloads.md)關鍵字。 您可以選擇性地在宣告中省略 `Overloads` ，但如果您將它包含在任何宣告中，則必須將它包含在每個宣告中。  
  
3. 在每個宣告語句之後，撰寫程式程式碼來處理特定案例，其中呼叫程式碼會提供符合該版本參數清單的引數。 您不需要測試呼叫程式碼提供的參數。 Visual Basic 將控制權傳遞給程式的相符版本。  
  
4. `End Sub`請視需要使用或語句來終止程式的每個版本 `End Function` 。  
  
## <a name="example"></a>範例  

 下列範例會定義將 `Sub` 交易張貼至客戶餘額的程式。 它會使用 `Overloads` 關鍵字來定義程式的兩個版本，一個是依名稱接受客戶，另一個則依據帳戶編號。  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 呼叫程式碼可以將客戶識別取得為 `String` 或 `Integer` ，然後在任何一種情況下使用相同的呼叫語句。  
  
 如需如何呼叫這些程式版本的詳細資訊 `post` ，請參閱 [如何：呼叫](./how-to-call-an-overloaded-procedure.md)多載程式。  
  
## <a name="compile-the-code"></a>編譯程式碼  

 請確定每個多載版本都有相同的程式名稱，但有不同的參數清單。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載化程序的考慮因素](./considerations-in-overloading-procedures.md)
- [多載解析](./overload-resolution.md)
