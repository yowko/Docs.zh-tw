---
title: "概念和術語 （功能轉換） (Visual Basic) |Microsoft 文件"
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
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9c4716765199798e50c4318b290f8a2d76ef5841
ms.lasthandoff: 03/13/2017


---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>概念和術語 （功能轉換） (Visual Basic)
本主題說明純功能性轉換的概念與術語。 轉換資料的功能性轉換方法所產生的程式碼通常比更傳統的命令性程式設計可以更快速地進行程式設計、更明確，而且更容易進行偵錯與維護。  
  
 請注意，本節中的主題用意不在於完整說明功能性程式設計。 而在於識別更容易將 XML 從一個組織結構轉換為另一個組織結構的某些功能性程式設計能力。  
  
## <a name="what-is-pure-functional-transformation"></a>何謂純功能性轉換？  
 在*純功能性轉換*，一組函式，呼叫*純虛擬函式*，定義如何將一組結構化資料從其原始格式轉換成另一種形式。 「 純 」 這個字表示的功能是*組合*，需要它們是︰  
  
-   *獨立*，以便他們可以自由地排序和重新整理，而不牽連或程式的其餘部分。 純轉換與其環境無關，也不會影響其環境。 也就是用於轉換的函式沒有任何*副作用*。  
  
-   *無狀態*，以便在相同的輸入上執行相同的函數或特定一組函數永遠會導致相同的輸出。 純轉換絲毫不會記得其先前的用途。  
  
> [!IMPORTANT]
>  在本教學課程的其餘部分，「純虛擬函式」這個名詞用於一般含意，表示程式設計方法而非特定的語言功能。  
>   
>  請注意，必須實作純虛擬函式做為 Visual Basic 中的函式。  
>   
>  同時，您不應將純虛擬函式誤解為 C++ 的純虛擬方法。 後者表示包含的類別是抽象的，而且不會提供任何方法主體。  
  
### <a name="functional-programming"></a>功能性程式設計  
 *功能性程式設計*是一種程式設計方法可直接支援純功能性轉換。  
  
 在過去，一般用途的功能性程式設計語言，例如 ML、 配置、 Haskell 與 F # 中，已主要的學術團體的關心。 雖然它一直可以在 Visual Basic 中撰寫純功能性轉換，困難度因此未進行其大部分的程式設計人員的理想選擇。 更新版本的 Visual Basic 中，不過，新語言建構例如 lambda 運算式和型別推斷讓功能性程式設計更容易且更具生產力。  
  
 如需函式程式設計的詳細資訊，請參閱[功能性程式設計與。命令式程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)。  
  
#### <a name="domain-specific-fp-languages"></a>網域指定的 FP 語言  
 雖然目前尚未廣泛採用一般功能性程式設計語言，但是特定網域指定的功能性程式設計語言比較受歡迎。 例如，階層式樣式表 (CSS) 用於決定許多網頁的外觀及操作，而可延伸樣式表語言轉換 (XSLT) 樣式表則廣泛用於 XML 資料操作。 如需 XSLT 的詳細資訊，請參閱[XSLT 轉換](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03)。  
  
## <a name="terminology"></a>用語  
 下表定義與功能性轉換相關的一些辭彙。  
  
 高順序 (第一級) 函式  
 可以視為程式設計物件的函式。 例如，高順序函式可以傳遞到其他函式，或從其他函式傳回。 在 Visual Basic 中，委派和 lambda 運算式，都是支援高順序函式的語言功能。 若要撰寫高順序函式，您可以宣告一或多個引數以取得委派，而且在呼叫高順序函式時，您通常可以使用 Lambda 運算式。 許多標準查詢運算子都是高順序函式。  
  
 如需詳細資訊，請參閱[標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
 Lambda 運算式  
 基本上，這是可用於任何需要委派型別之處的內嵌匿名函式。 這是 Lambda 運算式的簡化定義，但這適用於此教學課程的用途。  
  
 如需詳細資訊，請參閱[Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 集合  
 一組結構化的資料，通常屬於統一的型別。 若要與 LINQ 相容，集合必須實作<xref:System.Collections.IEnumerable>介面或<xref:System.Linq.IQueryable>介面 (或其泛型對應項目，其中<xref:System.Collections.Generic.IEnumerator%601>或<xref:System.Linq.IQueryable%601>)。</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerator%601> </xref:System.Linq.IQueryable> </xref:System.Collections.IEnumerable>  
  
 Tuple (匿名型別)  
 這是一個數學概念，一個 Tuple 表示一個有限的物件順序，每個都有特定的型別。 Tuple 也稱為排序清單。 匿名型別為此概念的語言實作，可以宣告未具名的類別型別，並同時具現化該類別的物件。  
  
 如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
 型別推斷 (隱含型別)  
 編譯器在沒有明確的型別宣告時，判斷變數型別的能力。  
  
 如需詳細資訊，請參閱[本機的型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
 延後執行與延遲評估  
 延後運算式的評估，直到實際需要其解決的值為止。 在集合中，支援延後執行。  
  
 如需詳細資訊，請參閱[基本查詢作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)和[延後執行與 LINQ to XML (Visual Basic) 中的延遲評估](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)。  
  
 這些語言功能將用於本節的所有程式碼範例中。  
  
## <a name="see-also"></a>另請參閱  
 [純功能性轉換 (Visual Basic) 簡介](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)   
 [函數式程式設計與命令式程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
