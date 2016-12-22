---
title: "Delegates (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "delegates [Visual Basic]"
  - "Visual Basic code, delegates"
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Delegates (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

委派就是參考方法的物件。  它們有時會被描述成「*型別安全函式指標*」\(Type\-Safe Function Pointer\)，這是因為它們與使用在其他程式語言中的函式指標類似。  但與函式指標不同的是，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 委派是以類別 <xref:System.Delegate?displayProperty=fullName> 為基礎的參考型別。  委派可以同時參考共用方法 \(不需特定的類別執行個體即可呼叫的方法\) 和執行個體方法。  
  
## 委派和事件  
 在呼叫程序與被呼叫程序之間需要媒介的情況下，委派相當有用。  例如，您可能要引發事件的物件能夠在不同的情況下呼叫不同的事件處理常式。  不過，引發事件的物件無法事先得知事件處理常式處理特定事件的時間。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會在您使用 `AddHandler` 陳述式時為您建立委派，讓您能夠以動態方式建立事件處理常式與事件的關聯。  委派會在 Run Time 時將呼叫轉至適當的事件處理常式。  
  
 雖然，您可以建立自己的委派，但多數情況下，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會為您建立委派並處理細節。  例如，`Event` 陳述式會將名為 `<EventName>EventHandler` 的委派類別，隱含定義為包含 `Event` 陳述式的類別的巢狀類別 \(Nested Class\)，並與事件具有相同的簽章。  `AddressOf` 陳述式會以隱含方式建立委派的執行個體，而該委派會參考特定的程序。  下列兩行程式碼是對等用法。  在第一行中，您可看見 `Eventhandler` 執行個體的明確建立，內含當做引數傳送之 `Button1_Click` 方法的參考。  第二行則是用於執行相同作業的簡便方式。  
  
 [!CODE [VbVbalrDelegates#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrDelegates#6)]  
  
 只要編譯器 \(Compiler\) 能夠依內容判斷委派的型別，您就可以使用簡略的方法來建立委派。  
  
## 宣告使用現有委派型別的事件  
 在一些情況下，您可能想要宣告事件來將現有的委派型別 \(Delegate Type\) 當做其基礎委派使用。  如下列語法所示：  
  
 [!CODE [VbVbalrDelegates#7](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrDelegates#7)]  
  
 當您要傳送多個事件到相同的處理常式時，這會相當有用。  
  
## 委派變數和參數  
 您可以在其他與事件無關的工作上使用委派，例如無限制執行緒或是需要在執行階段呼叫不同函式版本的程序。  
  
 例如，假設您有個分類廣告應用程式，其中包含具有汽車名稱的清單方塊。  廣告是依標題 \(通常是汽車的型號\) 排序。  當一些汽車在型號之前包括有年份時，就會發生您可能要面對的問題。  問題在於，清單方塊的內建排序功能只會依字元碼排序；它會先列出所有以日期開頭的廣告，接著才是以型號開頭的廣告。  
  
 若要解決這個問題，您可以在類別中建立一排序程序，讓它在多數的清單方塊中使用標準的字母順序排序，但能夠在 Run Time 時切換控制為汽車廣告所用的自訂排序程序。  若要這麼做，您就要在執行階段使用委派，將自訂排序程序傳遞至排序類別。  
  
## AddressOf 和 Lambda 運算式  
 每個委派類別會定義傳遞物件方法規格的建構函式 \(Constructor\)。  委派建構函式的引數必須是方法的參考或 Lambda 運算式。  
  
 若要指定方法的參考，請使用下列語法：  
  
 `AddressOf` \[`expression`.\]`methodName`  
  
 `expression` 在編譯時期的型別必須是包含指定名稱 \(其簽章符合委派類別的簽章\) 方法的類別或介面的名稱。  `methodName` 可以是共用方法或執行個體方法。  即使您為類別的預設方法建立委派，`methodName` 還是必要項。  
  
 若要指定 Lambda 運算式，請使用下列語法：  
  
 `Function` \(\[`parm` As `type`, `parm2` As `type2`, ...\]\) `expression`  
  
 下列範例顯示用於指定委派參考的 `AddressOf` 和 Lambda 運算式。  
  
 [!CODE [VbVbalrDelegates#15](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrDelegates#15)]  
  
 函式的簽章必須符合委派型別的簽章。  如需 Lambda 運算式的詳細資訊，請參閱 [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  如需 Lambda 運算式的更多範例和委派的 `AddressOf` 指派，請參閱[Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[How to: Invoke a Delegate Method](../Topic/How%20to:%20Invoke%20a%20Delegate%20Method%20\(Visual%20Basic\).md)|提供範例，顯示如何使方法與委派產生關聯，然後再透過委派叫用方法。|  
|[How to: Pass Procedures to Another Procedure in Visual Basic](../Topic/How%20to:%20Pass%20Procedures%20to%20Another%20Procedure%20in%20Visual%20Basic.md)|示範如何使用委派將某個程序傳遞至其他程序。|  
|[Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|描述即使在簽章不同的情況下，如何將子函數與函式指派給委派或處理常式。|  
|[Events](../../../../visual-basic/programming-guide/language-features/events/events.md)|提供 Visual Basic 中的事件概觀。|