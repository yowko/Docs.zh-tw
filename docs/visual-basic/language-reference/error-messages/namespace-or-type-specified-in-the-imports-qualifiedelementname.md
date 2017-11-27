---
title: "命名空間或類型指定在匯入 &#39;&lt;完整項目名稱&gt;&#39; 沒有 &#39; t 包含任何 public 成員，或找不到"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords: BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 49cd9fa5d5182b2cf2d7fc4623bc8e9aa02bf85e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>命名空間或類型指定在匯入 &#39;&lt;完整項目名稱&gt;&#39; 沒有 &#39; t 包含任何 public 成員，或找不到
中的匯入的命名空間或類型指定\<完整項目名稱 >' 不包含任何 public 成員，或是找不到。 請確定命名空間或類型已定義，而且包含至少一個 public 成員。 請確定別名名稱不包含其他別名。  
  
 `Imports`陳述式會指定包含的項目，或是無法找到未定義任何`Public`成員。  
  
 A*包含項目的*可以是命名空間、 類別、 結構、 模組、 介面或列舉型別。 包含的項目包含成員，例如變數、 程序或其他內含項目。  
  
 匯入的目的是允許您存取命名空間或類型成員的程式碼，而不必加以限定。 若要加入的命名空間或類型的參考，可能也需要您的專案。 如需詳細資訊，請參閱 < 匯入包含項目 >[宣告之項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
 如果編譯器找不到指定的包含項目，它無法解析使用它的參考。 如果它找到的項目但項目不會公開任何`Public`成員，則任何參考可以成功。 在任一情況下是無意義的匯入的項目。  
  
 請記住，如果您匯入包含項目，並將匯入別名指派給它，您便無法使用該匯入別名匯入另一個項目。 下列程式碼會產生編譯器錯誤。  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **錯誤 ID:** BC40056  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確認包含的項目是從您的專案存取。  
  
2.  確認包含的項目規格不會包含從另一個匯入任何匯入別名。  
  
3.  請確認包含的項目會公開至少一個`Public`成員。  
  
## <a name="see-also"></a>另請參閱  
 [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Namespace 陳述式](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
