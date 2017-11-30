---
title: "命名空間或專案層級 Imports &#39; 中指定的類型&lt;完整項目名稱&gt;&#39; 沒有 &#39; t 包含任何 public 成員，或找不到"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords: BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d0a164562524af239b3b130f681dbc6eff23814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>命名空間或專案層級 Imports &#39; 中指定的類型&lt;完整項目名稱&gt;&#39; 沒有 &#39; t 包含任何 public 成員，或找不到
在專案層級 Imports' 中指定的命名空間或類型\<完整項目名稱 >' 不包含任何 public 成員，或是找不到。 請確定命名空間或類型已定義，而且包含至少一個 public 成員。 請確定別名名稱不包含其他別名。  
  
 專案匯入屬性會指定包含的項目，或是無法找到未定義任何`Public`成員。  
  
 A*包含項目的*可以是命名空間、 類別、 結構、 模組、 介面或列舉型別。 包含的項目包含成員，例如變數、 程序或其他內含項目。  
  
 匯入的目的是允許您存取命名空間或類型成員的程式碼，而不必加以限定。 若要加入的命名空間或類型的參考，可能也需要您的專案。 如需詳細資訊，請參閱 < 匯入包含項目 >[宣告之項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
 如果編譯器找不到指定的包含項目，它無法解析使用它的參考。 如果它找到的項目但項目不會公開任何`Public`成員，則任何參考可以成功。 在任一情況下是無意義的匯入的項目。  
  
 您使用**專案設計工具**來指定匯入的項目。 使用**匯入命名空間**區段**參考**頁面。 您可以取得**專案設計工具**按兩下**我的專案**中的圖示**方案總管 中**。  
  
 **錯誤 ID:** BC40057  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  開啟**專案設計工具**並切換至**參考**頁面。  
  
2.  在**匯入命名空間**區段中，確認包含的項目從您的專案可以存取。  
  
3.  請確認包含的項目會公開至少一個`Public`成員。  
  
## <a name="see-also"></a>另請參閱  
 [專案設計工具、參考頁面 (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
