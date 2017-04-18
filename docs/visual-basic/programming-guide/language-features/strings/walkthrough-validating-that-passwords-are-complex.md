---
title: "驗證密碼複雜性 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- String data type, validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e899900d60bddb83fb640abcc7f11f333c1af870
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>逐步解說：驗證密碼確實複雜 (Visual Basic)
這個方法會檢查有部份特性的強式密碼，並更新字串參數的檢查密碼失敗的資訊。  
  
 密碼可以用在安全的系統，來授權使用者。 不過，密碼必須是難猜出未經授權的使用者。 攻擊者可以使用*字典攻擊*的程式，可逐一查看所有字典 （或多個字典，以不同的語言） 中的字數，並測試是否有任何文字做為使用者的密碼。 弱式密碼，例如 「 洋基 」 或 「 Mustang 」 可以快速地猜到了。 更嚴密的密碼，例如"嗎？您 'L1N3vaFiNdMeyeP@sSWerd！ 」，更不容易猜到。 密碼保護的系統應該確定使用者選擇強式密碼。  
  
 強式密碼很複雜 （包含大寫、 小寫、 數字和特殊字元的混合），而且不是字。 這個範例示範如何驗證複雜度。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbcnRegEx #&1;](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 呼叫這個方法，傳遞包含該密碼的字串。  
  
 這個範例需要：  
  
-   存取的成員<xref:System.Text.RegularExpressions>命名空間。</xref:System.Text.RegularExpressions> 新增`Imports`陳述式，如果您不完整限定成員名稱在您的程式碼。 如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## <a name="security"></a>安全性  
 如果您要透過網路移動密碼，您需要使用安全的方法來傳送資料。 如需詳細資訊，請參閱[ASP.NET Web 應用程式安全性](https://msdn.microsoft.com/library/330a99hc)。  
  
 您可以改善的精確度`ValidatePassword`藉由新增額外的複雜性檢查函式︰  
  
-   密碼和使用者的名稱、 使用者識別碼和應用程式定義的字典的子字串比較。 執行比較時，此外，將視為對等項目看起來類似的字元。 例如，視為字母"l"和"e"等於"1"和"3"的數字。  
  
-   如果只有一個大寫字元，請確定它不是密碼的第一個字元。  
  
-   請確定密碼的最後兩個字元的字母字元。  
  
-   不允許輸入從鍵盤的上方資料列的所有符號的密碼。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Text.RegularExpressions.Regex></xref:System.Text.RegularExpressions.Regex>   
 [ASP.NET Web 應用程式安全性](https://msdn.microsoft.com/library/330a99hc)
