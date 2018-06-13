---
title: 如何：宣告自訂事件以節省記憶體 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: d19c91d66e458ca2317dc049d517b92fa7406ef6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647174"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>如何：宣告自訂事件以節省記憶體 (Visual Basic)
重要的應用程式保留其記憶體使用量低時，有幾種情況。 自訂事件可讓應用程式使用的記憶體僅適用於處理事件。  
  
 根據預設，當類別宣告事件時，編譯器會配置記憶體來儲存事件資訊的欄位。 如果類別有許多未使用的事件，會不必要地佔用記憶體。  
  
 而不是使用 Visual Basic 提供的事件的預設實作，您可以使用自訂事件，來更謹慎管理的記憶體使用量。  
  
## <a name="example"></a>範例  
 在此範例中，類別會使用一個執行個體<xref:System.ComponentModel.EventHandlerList>類別，儲存在`Events`欄位，來儲存使用中事件的相關資訊。 <xref:System.ComponentModel.EventHandlerList>類別是設計來保存委派最佳化的清單類別。  
  
 類別使用中的所有事件`Events`哪種方法會處理每個事件追蹤的欄位。  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ComponentModel.EventHandlerList>  
 [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [如何：宣告自訂事件以避免封鎖](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
