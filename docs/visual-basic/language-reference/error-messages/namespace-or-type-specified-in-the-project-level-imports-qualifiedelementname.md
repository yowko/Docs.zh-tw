---
title: "Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc40057"
  - "bc40057"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40057"
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

專案層級 Imports '\<qualifiedelementname\>' 中指定的命名空間或型別不包含任何 Public 成員，或是找不到該命名空間或型別。請確定命名空間或型別已定義，而且其中包含至少一個 Public 成員。請確定別名名稱不包含其他別名。  
  
 專案的匯入屬性會指定找不到或尚未定義任何 `Public` 成員的包含項目。  
  
 「*包含的項目*」\(Containing Element\) 可以是命名空間、類別、結構、模組、介面或列舉。  包含的項目含有許多成員，例如變數、程序或其他包含的項目。  
  
 匯入的目的是要讓您的程式碼存取命名空間或型別成員，但不需要加以限定。  您的專案可能會需要加入命名空間或型別的參考。  如需詳細資訊，請參閱[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的＜匯入包含的項目＞。  
  
 如果編譯器 \(Compiler\) 找不到指定的包含項目，就無法解析使用該項目的參考。  如果找到項目，但項目並未公開 \(Expose\) 任何 `Public` 成員，則沒有任何參考會成功。  在這兩種情況下，匯入項目並沒有任何意義。  
  
 您可以使用 \[**專案設計工具**\]，指定要匯入的項目。  請使用 \[**參考**\] 頁面的 \[**匯入的命名空間**\] 區段。  只要按兩下 \[**方案總管**\] 中的 \[**我的專案**\] 圖示，就可以開啟 \[**專案設計工具**\]。  
  
 **錯誤 ID**︰BC40057  
  
### 若要更正這個錯誤  
  
1.  開啟 \[**專案設計工具**\]，然後切換至 \[**參考**\] 頁面。  
  
2.  在 \[**匯入的命名空間**\] 區段中，確定可從您的專案存取包含的項目。  
  
3.  確定包含的項目至少公開一個 `Public` 成員。  
  
## 請參閱  
 [專案設計工具，參考頁 \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)