---
title: 驗證密碼複雜性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: acfc8ab958c8671ed7f1afd245d24a43ca12be29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650279"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>逐步解說：驗證密碼確實複雜 (Visual Basic)
這個方法會檢查有某些強式密碼特性，並更新有關哪些檢查密碼失敗的資訊的字串參數。  
  
 密碼可以用在安全的系統，來授權使用者。 不過，密碼必須是難以猜測未經授權的使用者。 攻擊者能夠使用*字典攻擊*程式，可逐一查看所有字典 （或以不同語言的多個字典） 中的文字，並測試是否有任何文字做為使用者的密碼。 弱式密碼，例如"洋基隊"或"Mustang 」 可以快速猜測。 更強的密碼，例如"嗎？您 'L1N3vaFiNdMeyeP@sSWerd！"，較可能被猜到。 受密碼保護的系統，應該確保使用者選擇強式密碼。  
  
 強式密碼很複雜 （包含大寫、 小寫、 數字及特殊字元的混合），而且不是字。 此範例示範如何驗證複雜性。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 呼叫這個方法由傳遞字串，包含該密碼。  
  
 這個範例需要：  
  
-   <xref:System.Text.RegularExpressions> 命名空間成員的存取權。 新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。 如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## <a name="security"></a>安全性  
 如果您要透過網路移動密碼，您需要將資料傳輸會使用安全的方法。 如需詳細資訊，請參閱[ASP.NET Web 應用程式安全性](https://msdn.microsoft.com/library/330a99hc)。  
  
 您可以改善的精確度`ValidatePassword`函式加上額外的複雜性檢查：  
  
-   密碼和使用者的名稱、 使用者識別碼和應用程式定義的字典針對子字串比較。 此外，將看起來類似字元視為對等項目時執行的比較。 例如，視為字母"l"和"e"等於數字"1"和"3"。  
  
-   如果只有一個大寫字元，請確定它不是密碼的第一個字元。  
  
-   請確定密碼最後兩個字元的字母字元。  
  
-   不允許輸入從鍵盤的上方資料列的所有符號的密碼。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Text.RegularExpressions.Regex>  
 [ASP.NET Web 應用程式安全性](https://msdn.microsoft.com/library/330a99hc)
