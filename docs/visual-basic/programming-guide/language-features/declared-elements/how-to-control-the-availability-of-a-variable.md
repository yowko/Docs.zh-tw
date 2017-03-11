---
title: "How to: Control the Availability of a Variable (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "access levels, declared elements"
  - "Private keyword, accessing variables"
  - "access levels, variables"
  - "Public keyword, accessing variables"
  - "Friend keyword, accessing variables"
  - "variables [Visual Basic], access level"
  - "declared elements, access level"
  - "Protected keyword, accessing variables"
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Control the Availability of a Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可指定變數的「*存取層級*」\(Access Level\) 來控制變數的可用性。  存取層級會決定程式碼是否具有讀取或寫入至變數的權限。  
  
-   「*成員變數*」\(Member Variable\) \(在模組層級和任何程序以外定義\) 預設為公用存取，表示任何看到成員變數的程式碼都可加以存取。  您可以指定存取修飾詞來改變這種情況。  
  
-   「*區域變數*」\(Local Variable\) \(在程序內定義\) 在名義上雖然是公用存取，不過只有變數所屬程序中的程式碼可加以存取。  您無法變更區域變數的存取層級，但可變更包含該區域變數之程序的存取層級。  
  
 如需詳細資訊，請參閱 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## 私用和公用存取  
  
#### 若要使變數只能從其模組、類別或結構中存取  
  
1.  將變數的 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 放到模組、類別或結構內，但在任何程序以外。  
  
2.  在 `Dim` 陳述式中加入 [Private](../../../../visual-basic/language-reference/modifiers/private.md) 關鍵字。  
  
     您可從模組、類別或結構中的任何地方讀取或寫入至變數，但不能從外面存取。  
  
#### 若要使變數能夠從任何可看見變數的程式碼來存取  
  
1.  以成員變數而言，將變數的 `Dim` 陳述式放到模組、類別或結構內，但在任何程序以外。  
  
2.  在 `Dim` 陳述式中加入 [Public](../../../../visual-basic/language-reference/modifiers/public.md) 關鍵字。  
  
     您可從任何與組件相互操作的程式碼，讀取或寫入至變數。  
  
 \-或\-  
  
1.  就區域變數而言，將變數的 `Dim` 陳述式放到程序內。  
  
2.  請勿在 `Dim` 陳述式中加入 `Public` 關鍵字。  
  
     您可從程序中的任何地方讀取或寫入至變數，但不能從程序外面存取。  
  
## 保護存取和 Friend 存取  
 您可將變數的存取層級限制為其類別和任何衍生類別或組件。  也可以將這些限制指定為等位條件，允許從任何衍生類別的程式碼中存取，或從相同組件中的任何其他位置存取。  可以在同一宣告中結合使用 `Protected` 和 `Friend` 關鍵字，來指定此等位條件。  
  
#### 若要使變數只能從其類別和任何衍生類別中存取  
  
1.  將變數的 `Dim` 陳述式放到類別內，但在任何程序外。  
  
2.  在 `Dim` 陳述式中加入 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) 關鍵字。  
  
     您可從類別和任何衍生類別中的任何地方讀取或寫入至變數，但不能從衍生鏈結中的任何類別以外存取。  
  
#### 若要使變數只能從相同組件中存取  
  
1.  將變數的 `Dim` 陳述式放到模組、類別或結構內，但在任何程序以外。  
  
2.  在 `Dim` 陳述式中加入 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) 關鍵字。  
  
     您可從模組、類別或結構中的任何地方及從相同組件中的任何程式碼讀取或寫入至變數，但不能從組件外面存取。  
  
## 範例  
 下列範例顯示使用 `Public`、`Protected`、`Friend`、`Protected Friend` 和 `Private` 存取層級宣告變數。  請注意，當 `Dim` 陳述式指定存取層級時，您不需要加入 `Dim` 關鍵字。  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## .NET Framework 安全性  
 變數的存取層級約束愈多，惡意程式碼不當使用該變數的機會愈小。  
  
## 請參閱  
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Public](../../../../visual-basic/language-reference/modifiers/public.md)   
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)   
 [Private](../../../../visual-basic/language-reference/modifiers/private.md)