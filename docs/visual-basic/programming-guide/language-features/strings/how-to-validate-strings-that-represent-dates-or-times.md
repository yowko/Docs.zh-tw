---
title: 如何：驗證代表日期或時間的字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5321e7a85c45ddb6ce17433bd25ce9ca2165f0a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348406"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>如何：驗證代表日期或時間的字串 (Visual Basic)
下列程式碼範例會設定 `Boolean` 值，指出字串是否代表有效的日期或時間。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 以您想要驗證的日期和時間取代 `("01/01/03")` 和 `"9:30 PM"`。 您可以使用另一個硬式編碼字串、`String` 變數或傳回字串的方法（例如 `InputBox`）來取代字串。  
  
## <a name="robust-programming"></a>最佳化程式設計  
 嘗試將 `String` 轉換成 `DateTime` 變數之前，請使用這個方法來驗證字串。 藉由先檢查日期或時間，您可以避免在執行時間產生例外狀況。  
  
## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [在 Visual Basic 中驗證字串](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
