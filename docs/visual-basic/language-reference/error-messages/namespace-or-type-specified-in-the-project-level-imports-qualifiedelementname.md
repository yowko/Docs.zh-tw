---
title: "在專案層級匯入的命名空間或類型指定&lt;qualifiedelementname&gt;&quot; 不包含任何 public 成員，或是找不到 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40057
- bc40057
dev_langs:
- VB
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 5dae6f92f573a57d0974c860500bc7420f55a94f
ms.lasthandoff: 03/13/2017

---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>在專案層級匯入的命名空間或類型指定&lt;qualifiedelementname&gt;' 不包含任何 public 成員，或是找不到
在專案層級匯入的命名空間或類型指定\<qualifiedelementname >' 不包含任何 public 成員，或是找不到。 確定命名空間或型別定義，而且包含至少一個 public 成員。 請確定別名名稱不包含其他別名。  
  
 專案匯入屬性會指定包含的項目無法找到或未定義任何`Public`成員。  
  
 A*包含項目的*可以是命名空間、 類別、 結構、 模組、 介面或列舉型別。 包含的項目包含成員，例如變數、 程序或其他包含的項目。  
  
 匯入的目的是要允許存取命名空間或類型成員程式碼，而不必加以限定。 若要加入的命名空間或型別參考，可能也需要您的專案。 如需詳細資訊，請參閱 「 匯入包含項目 」 中[宣告之項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
 如果編譯器找不到指定的包含項目，所以無法解析使用它的參考。 如果它找到的項目，但此項目不會公開任何`Public`成員，則任何參考可成功。 在任一情況下並沒有任何意義，匯入之項目的項目。  
  
 您使用**專案設計工具**來指定要匯入的項目。 使用**匯入命名空間**區段**參考**頁面。 您可以取得**專案設計工具**按兩下**我的專案**圖示**方案總管 中**。  
  
 **錯誤識別碼︰** BC40057  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  開啟**專案設計工具**並切換至**參考**頁面。  
  
2.  在**匯入命名空間**區段中，確認包含的項目是從您的專案。  
  
3.  請確認包含的項目會公開至少一個`Public`成員。  
  
## <a name="see-also"></a>另請參閱  
 [專案設計工具、參考頁 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)   
 [NIB 如何︰ 修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [公用](../../../visual-basic/language-reference/modifiers/public.md)   
 [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
