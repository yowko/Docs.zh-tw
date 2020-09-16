---
title: 驗證密碼複雜度
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 8cb04286e98cf78f0fb66dde92002ee09e2ea0f5
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556241"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>逐步解說：驗證密碼確實複雜 (Visual Basic)
這個方法會檢查是否有一些強式密碼特性，並以檢查密碼失敗的相關資訊來更新字串參數。  
  
 密碼可以在安全的系統中用來授權使用者。 不過，密碼必須很難猜測未經授權的使用者。 攻擊者可以使用 *字典攻擊* 程式，來逐一查看字典中的所有文字 (或不同語言的多個字典) 並測試是否有任何單字做為使用者的密碼。 弱式密碼（例如 "洋基隊" 或 "Mustang"）可以快速地猜測。 更強的密碼，例如 "？您的 ' L1N3vaFiNdMeyeP@sSWerd ！ "不太可能被猜測。 受密碼保護的系統應確保使用者選擇強式密碼。  
  
 強式密碼是複雜的 (，其中包含大寫、小寫、數位和特殊字元的混合) 而不是單字。 此範例示範如何驗證複雜度。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 藉由傳遞包含該密碼的字串來呼叫這個方法。  
  
 這個範例需要：  
  
- <xref:System.Text.RegularExpressions> 命名空間成員的存取權。 新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。 如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## <a name="security"></a>安全性  
 如果您要在網路上移動密碼，則需要使用安全的方法來傳輸資料。 如需詳細資訊，請參閱 [ASP.NET Web 應用程式安全性](/previous-versions/aspnet/330a99hc(v=vs.100))。
  
 您可以藉 `ValidatePassword` 由新增額外的複雜性檢查來改善函式的精確度：  
  
- 根據使用者的名稱、使用者識別碼和應用程式定義的字典，比較密碼和其子字串。 此外，執行比較時，將視覺效果類似的字元視為相等。 例如，將字母 "l" 和 "e" 視為等於數位 "1" 和 "3"。  
  
- 如果只有一個大寫字元，請確定它不是密碼的第一個字元。  
  
- 請確定密碼的最後兩個字元是字母字元。  
  
- 不允許從鍵盤頂端資料列輸入所有符號的密碼。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Text.RegularExpressions.Regex>
- [ASP.NET 網路應用程式安全性](/previous-versions/aspnet/330a99hc(v=vs.100))
