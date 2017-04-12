---
title: "如何︰ 宣告自訂事件以節省記憶體 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declaring events, custom
- events [Visual Basic], custom
- custom events
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 4f8ce32a3b4da411a73010119283ce9661b82a6c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>如何：宣告自訂事件以節省記憶體 (Visual Basic)
重要的應用程式維持在其記憶體使用量很低時，有幾種情況。 自訂事件可讓應用程式使用記憶體僅適用於處理事件。  
  
 根據預設，當類別宣告的情況下，編譯器會配置記憶體來儲存事件資訊的欄位。 如果類別有許多未使用的事件，它們其實不需要的記憶體。  
  
 而不是使用 Visual Basic 提供的事件的預設實作，您可以使用自訂事件更謹慎管理的記憶體使用量。  
  
## <a name="example"></a>範例  
 在此範例中，類別會使用一個執行個體<xref:System.ComponentModel.EventHandlerList>類別中，儲存在`Events`欄位，用於儲存事件的相關資訊。</xref:System.ComponentModel.EventHandlerList> <xref:System.ComponentModel.EventHandlerList>類別是設計用來保存委派最佳化的清單類別。</xref:System.ComponentModel.EventHandlerList>  
  
 類別使用中的所有事件`Events`欄位來追蹤每個事件處理方法。  
  
 [!code-vb[VbVbalrEvents #&22;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ComponentModel.EventHandlerList></xref:System.ComponentModel.EventHandlerList>   
 [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)   
 [如何：宣告自訂事件以避免封鎖](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
