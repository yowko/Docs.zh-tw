---
title: "Namespace Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Namespace"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "namespaces, root"
  - "Namespace statement"
  - "namespaces, nested"
  - "declaring namespaces, syntax"
  - "namespaces, declaring"
  - "root namespaces"
  - "declarations, namespaces"
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
caps.latest.revision: 39
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 39
---
# Namespace Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

宣告命名空間的名稱，並將要在該命名空間內編譯的原始程式碼置於宣告之後。  
  
## 語法  
  
```  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## 組件  
 Global  
 選擇項。  可讓您定義專案的根命名空間的命名空間。  請參閱 [Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
 `name`  
 必要項。  識別命名空間的唯一名稱。  必須是有效的 Visual Basic 識別項。  如需詳細資訊，請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 `componenttypes`  
 選擇項。  組成命名空間的項目。  這些包括，但不是限於，列舉型別、 結構、 介面、 類別、 模組、 委派和其他命名空間。  
  
 `End Namespace`  
 結束 `Namespace` 區塊。  
  
## 備註  
 命名空間是當做組織系統使用，  並且會提供方法以分類和呈現公開給其他程式和應用程式的程式設計項目。  請注意，命名空間不*型別*是類別或結構的角度來說，您不能宣告程式設計項目具有命名空間的資料型別。  
  
 在 `Namespace` 陳述式之後宣告的所有程式設計項目都屬於該命名空間。  除非 Visual Basic 遇到 `End Namespace` 陳述式或另一個 `Namespace` 陳述式，否則它會繼續將項目編譯至最後宣告的命名空間。  
  
 ：如果已定義命名空間 \(即使是在專案外部\)，仍可加入程式設計項目至這個命名空間中。  若要執行這項操作，請使用`Namespace`陳述式來指示 Visual Basic 來編譯該命名空間中的項目。  
  
 只有在檔案或命名空間層級才可以使用 `Namespace` 陳述式。  這表示命名空間的「*宣告內容*」必須是原始程式檔 \(Source File\) 或另一個命名空間，且不可以是類別、結構、模組、介面或程序。  如需詳細資訊，請參閱[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 ：可以在另一個命名空間內宣告某個命名空間。  您可宣告的巢狀層級並沒有嚴格限制，但請記住，其他程式碼存取最內層命名空間中所宣告的項目時，它必須使用限定性條件字串，而該字串則包含在巢狀階層中的所有命名空間名稱。  
  
## 存取層級  
 命名空間會視為具有`Public`存取層級。  可從相同專案內、從參考該專案的其他專案和從該專案所建置的組件內的任何地方存取命名空間。  
  
 在命名空間層級上宣告的程式設計項目 \(表示在命名空間內，但不在其他任何項目內\) 可具有 `Public` 或 `Friend` 的存取權限。  如果未指定，則這類項目的存取層級會預設使用 `Friend`。  可在命名空間層級宣告的項目包含類別、結構、模組、介面、列舉型別 \(Enumeration\) 和委派 \(Delegate\)。  如需詳細資訊，請參閱[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
## 根 Namespace  
 專案中的所有命名空間名稱都是依據「*根命名空間*」\(Root Namespace\) 而命名。  Visual Studio 會根據專案內的所有程式碼，將專案名稱指定為預設根命名空間的名稱。  例如，如果專案已命名為 `Payroll`，則它的程式設計項目會屬於命名空間 `Payroll`。  如果宣告 `Namespace funding`，則該命名空間的完整名稱是 `Payroll.funding`。  
  
 如果想要在 `Namespace` 陳述式中指定現有的命名空間 \(例如在泛型清單類別範例中\)，可以將根命名空間設定成 null 值。  若要執行這項作業，請按一下 \[**專案**\] 功能表中的 \[**專案屬性**\]，再清除 \[**根命名空間**\] 項目，讓方塊空白。  如果在泛型清單類別範例中不這樣做，則 Visual Basic 編譯器會將 `System.Collections.Generic` 當做專案 `Payroll` 內的新命名空間，而這個命名空間的完整名稱則為 `Payroll.System.Collections.Generic`。  
  
 或者可以使用 `Global` 關鍵字，以參考在專案外部定義的命名空間項目。  這樣做可以讓您保留專案名稱做為根命名空間的名稱。  這會減少意外合併程式設計項目與現有命名空間之程式設計項目的機會。  如需詳細資訊，請參閱 「 全域關鍵字以完整名稱 」 一節[Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
 `Global`關鍵字也可以用於 Namespace 陳述式。  這可讓您定義專案的根命名空間的命名空間。  如需詳細資訊，請參閱 「 全域關鍵字在 Namespace 陳述 」 一節[Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
 **疑難排解。** ：根命名空間會導致未預期的命名空間名稱串連。  如果參考定義在專案外部的命名空間，則 Visual Basic 編譯器會將它們當做是根命名空間內的巢狀命名空間。  在這類情況下，編譯器無法辨識已定義在外部命名空間中的任何型別。  若要避免這個問題，請設為 null 的值"根 Namespace，」 所述將根命名空間，或使用`Global`關鍵字來存取外部命名空間的項目。  
  
## 屬性和修飾詞  
 \(Attribute\)：不可將屬性套用至命名空間。  屬性會將資訊提供給組件的中繼資料 \(Metadata\)，這對來源 Classifier \(例如命名空間\) 不具任何意義。  
  
 \(Modifier\)：不可將任何存取或程序修飾詞 \(或其他任何修飾詞\) 套用至命名空間。  因為它不是型別，所以這些修飾詞不具意義。  
  
## 範例  
 下列範例會宣告兩個命名空間，其中一個會巢狀於另一個命名空間內。  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/namespace-statement_1.vb)]  
  
## 範例  
 下列範例會在單行中宣告多個巢狀命名空間，這與上面的範例相同。  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/namespace-statement_2.vb)]  
  
## 範例  
 下列範例會存取在上面範例中所定義的類別。  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/namespace-statement_3.vb)]  
  
## 範例  
 下列範例定義新泛型清單類別的基本架構，並將它加入至 <xref:System.Collections.Generic?displayProperty=fullName> 命名空間。  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## 請參閱  
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)