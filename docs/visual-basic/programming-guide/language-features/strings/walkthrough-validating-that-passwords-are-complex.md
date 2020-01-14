---
title: 驗證密碼複雜性
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 49e6f79c13c94a3f2f6891b259c4bb2bec54ae6f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344527"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>逐步解說：驗證密碼確實複雜 (Visual Basic)
這個方法會檢查是否有一些強式密碼特性，並使用檢查密碼失敗的相關資訊來更新字串參數。  
  
 密碼可以在安全的系統中用來授權使用者。 不過，未經授權的使用者可能不容易猜到密碼。 攻擊者可以使用*字典攻擊*程式，逐一查看字典中的所有單字（或不同語言的多個字典），並測試任何單字是否做為使用者的密碼。 弱式密碼（例如 "洋基隊" 或 "Mustang"）可能很快就會被猜到。 更強的密碼，例如「？您的「L1N3vaFiNdMeyeP@sSWerd！」很少被猜到。 受密碼保護的系統應確保使用者選擇強式密碼。  
  
 強式密碼很複雜（包含大寫、小寫、數位和特殊字元的混合），而且不是單字。 這個範例會示範如何驗證複雜度。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 藉由傳遞包含該密碼的字串來呼叫這個方法。  
  
 這個範例需要：  
  
- <xref:System.Text.RegularExpressions> 命名空間成員的存取權。 新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。 如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## <a name="security"></a>安全性  
 如果您要在網路上移動密碼，則需要使用安全的方法來傳輸資料。 如需詳細資訊，請參閱[ASP.NET Web 應用程式安全性](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))。
  
 您可以藉由新增額外的複雜性檢查，來改善 `ValidatePassword` 函式的精確度：  
  
- 根據使用者的名稱、使用者識別碼和應用程式定義的字典來比較密碼和子字串。 此外，執行比較時，將視覺效果相似的字元視為對等。 例如，將字母 "l" 和 "e" 視為等於數位 "1" 和 "3"。  
  
- 如果只有一個大寫字元，請確定它不是密碼的第一個字元。  
  
- 請確定密碼的最後兩個字元是字母字元。  
  
- 不允許從鍵盤頂端資料列輸入所有符號的密碼。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Text.RegularExpressions.Regex>
- [ASP.NET Web 應用程式安全性](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))
