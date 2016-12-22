---
title: "Namespace or type specified in the Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40056"
  - "vbc40056"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40056"
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Namespace or type specified in the Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Imports '\<qualifiedelementname\>' 中指定的命名空間或型別不包含任何 Public 成員，或是找不到該命名空間或型別。請確定命名空間或型別已定義，而且其中包含至少一個 Public 成員。請確定別名名稱不包含其他別名。  
  
 `Imports` 陳述式指定了一個找不到或尚未定義任何 `Public` 成員的包含項目。  
  
 「*包含的項目*」\(Containing Element\) 可以是命名空間、類別、結構、模組、介面或列舉。  包含的項目含有許多成員，例如變數、程序或其他包含的項目。  
  
 匯入的目的是要讓您的程式碼存取命名空間或型別成員，但不需要加以限定。  您的專案可能會需要加入命名空間或型別的參考。  如需詳細資訊，請參閱[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的＜匯入包含的項目＞。  
  
 如果編譯器 \(Compiler\) 找不到指定的包含項目，就無法解析使用該項目的參考。  如果找到項目，但項目並未公開 \(Expose\) 任何 `Public` 成員，則沒有任何參考會成功。  在這兩種情況下，匯入項目並沒有任何意義。  
  
 請記住，如果您要匯入包含的項目並指派匯入別名給它，您就無法使用該匯入別名來匯入另一個項目。  下列程式碼會產生編譯器錯誤。  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **錯誤 ID**︰BC40056  
  
### 若要更正這個錯誤  
  
1.  確定可從您的專案存取包含的項目。  
  
2.  確定包含項目的規格並未包括其他匯入的任何匯入別名。  
  
3.  確定包含的項目至少公開一個 `Public` 成員。  
  
## 請參閱  
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)