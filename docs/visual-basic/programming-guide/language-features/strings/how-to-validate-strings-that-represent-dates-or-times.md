---
title: HOW TO：驗證代表日期或時間的字串 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 1a838d9d156ad9c05a70a4d4d72db1a288731c9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685395"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>HOW TO：驗證代表日期或時間的字串 (Visual Basic)
下列程式碼範例將`Boolean`值，指出字串是否表示有效的日期或時間。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 取代`("01/01/03")`和`"9:30 PM"`與您想要驗證的時間與日期。 您可以用來取代以硬式編碼的另一個字串，字串`String`變數，或使用方法傳回字串，例如`InputBox`。  
  
## <a name="robust-programming"></a>穩固程式設計  
 使用這個方法來驗證該字串，然後再嘗試轉換`String`至`DateTime`變數。 藉由先檢查日期或時間，您可以避免產生在執行階段發生例外狀況。  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [在 Visual Basic 中驗證字串](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
