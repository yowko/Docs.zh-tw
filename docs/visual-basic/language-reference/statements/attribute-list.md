---
title: "Attribute List (Visual Basic) | Microsoft Docs"
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
  - "attribute list"
  - "attributes [Visual Basic], applying"
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Attribute List (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定要套用至已宣告程式設計項目的屬性 \(Attribute\)；  多個屬性之間以逗號 \(,\) 分隔。  下列是其中一個屬性的語法。  
  
## 語法  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## 組件  
 `attributemodifier`  
 對套用於原始程式檔 \(Source File\) 開頭處的屬性為必要項。  可以是 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) 或 [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md)。  
  
 `attributename`  
 必要項。  屬性 \(Attribute\) 名稱。  
  
 `attributearguments`  
 選擇項。  這個屬性 \(Attribute\) 的位置引數清單。  以逗號 \( , \) 分隔多個引數。  
  
 `attributeinitializer`  
 選擇項。  這個屬性 \(Attribute\) 的變數或屬性 \(Property\) 初始設定式清單。  初始設定式之間會以逗號來分隔。  
  
## 備註  
 一個或多個屬性 \(Attribute\) 套用幾乎可以套用到任何程式設計項目 \(型別、程序、屬性 \(Property\) 等\)。  屬性會出現在組件的中繼資料 \(Metadata\) 中，且可協助您加上程式碼的附註，或指定如何使用特定程式設計項目。  您可套用 Visual Basic 和 .NET Framework 所提供的屬性，且可定義自己的屬性。  
  
 如需何時使用屬性的詳細資訊，請參閱[屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)。  如需屬性名稱的詳細資訊，請參閱[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## 規則  
  
-   **位置** ：可將屬性套用至大部分已宣告的程式設計項目。  若要套用一或多個屬性，則可在項目宣告開頭處放置「*屬性區塊*」。  屬性清單中的每個項目都會指定您想套用的屬性，以及要用於這個屬性引動的修飾詞 \(Modifier\) 和引數。  
  
-   **角括弧** 如果提供屬性清單，則必須將它封入角括弧 \("`<`" 和 "`>`"\) 中。  
  
-   **宣告的一部分** ：屬性必須是項目宣告的一部分，而非個別的陳述式 \(Statement\)。  您可使用行接續字元 \(Line\-Continuation\) 序列 \(" `_`"\)，將宣告陳述式 \(Declaration Statement\) 擴充成多個原始程式碼行。  
  
-   **修飾詞。** 對於套用至原始程式檔開頭處之程式設計項目的每個屬性而言，屬性修飾詞 \(`Assembly` 或 `Module`\) 是必要項。  對於套用至不在原始程式檔開頭處之項目的屬性而言，則不允許有屬性修飾詞。  
  
-   **引數** ：屬性 \(Attribute\) 的所有位置性引數必須在任何變數或屬性 \(Property\) 初始設定式之前。  
  
## 範例  
 下列範例會將 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性套用至 `Function` 程序的基本架構定義。  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> 表示屬性化程序代表 Unmanaged 動態連結程式庫 \(DLL\) 的進入點 \(Entry Point\)。  屬性會提供 DLL 名稱做為位置性引數，而將其他資訊做為變數初始設定式。  
  
## 請參閱  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)   
 [Module \<keyword\>](../../../visual-basic/language-reference/modifiers/module-keyword.md)   
 [屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [如何：在程式碼中中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)