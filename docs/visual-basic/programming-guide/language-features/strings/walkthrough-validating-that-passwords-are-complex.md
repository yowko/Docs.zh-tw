---
title: 驗證密碼複雜性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 829d6485acdca22fbf10160c734e5c7f931dd855
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824932"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>逐步解說：驗證密碼確實複雜 (Visual Basic)
這個方法會檢查一些強式密碼的特性，並以了解哪種檢查密碼失敗的資訊更新字串參數。  
  
 密碼可以用在安全的系統，來授權使用者。 不過，密碼必須很難猜出未經授權的使用者。 攻擊者可以使用*字典攻擊*的程式，可逐一查看所有字典 （或不同的語言中的多個字典） 中的文字，並測試是否有任何文字做為使用者的密碼。 弱式密碼，例如"洋基隊 」 或 「 Mustang 」 可以快速地猜到。 強式密碼，例如"？您 'L1N3vaFiNdMeyeP@sSWerd！ 」，比較不容易猜到。 受密碼保護的系統應該確保使用者選擇強式密碼。  
  
 強式密碼很複雜 （包含大寫、 小寫、 數字和特殊字元的混合），而且不是一個字。 此範例示範如何驗證複雜性。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 呼叫這個方法，傳遞包含該密碼的字串。  
  
 這個範例需要：  
  
-   <xref:System.Text.RegularExpressions> 命名空間成員的存取權。 新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。 如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## <a name="security"></a>安全性  
 如果您要透過網路移動的密碼，您需要將資料傳輸會使用安全的方法。 如需詳細資訊，請參閱 < [ASP.NET Web 應用程式安全性](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))。
  
 您可以改善的精確度`ValidatePassword`加上額外的複雜性檢查函式：  
  
-   密碼和使用者的名稱、 使用者識別碼和應用程式定義的字典的子字串比較。 執行比較時，此外，將視為對等項目看起來類似的字元。 比方說，視為字母"l"和"e"等於"1"和"3"的數字。  
  
-   如果只有一個大寫字元，請確定它不是密碼的第一個字元。  
  
-   請確定密碼的最後兩個字元的字母字元。  
  
-   不允許在其中從鍵盤上方資料列輸入所有符號的密碼。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Text.RegularExpressions.Regex>
- [ASP.NET Web 應用程式安全性](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))
