---
title: HOW TO：宣告自訂事件以節省記憶體 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3bd58a09d016d818c4cc88c1d2527e81a95411e6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967122"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>HOW TO：宣告自訂事件以節省記憶體 (Visual Basic)
重要的應用程式保持其記憶體使用量低時，有幾種情況。 自訂事件可讓應用程式使用的記憶體只會針對它所處理的事件。  
  
 根據預設，當類別宣告事件時，編譯器會配置記憶體來儲存事件資訊的欄位。 如果類別有許多未使用的事件，會不必要地佔用記憶體。  
  
 而不是使用 Visual Basic 提供的事件的預設實作，您可以使用自訂的事件，更仔細管理的記憶體使用量。  
  
## <a name="example"></a>範例  
 在此範例中，類別會使用一個執行個體<xref:System.ComponentModel.EventHandlerList>類別，儲存在`Events`欄位，用於儲存事件的相關資訊。 <xref:System.ComponentModel.EventHandlerList>類別是設計用來保存委派的最佳化的清單類別。  
  
 類別使用中的所有事件`Events`欄位來追蹤哪些方法會處理每個事件。  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ComponentModel.EventHandlerList>
- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [如何：宣告自訂事件以避免封鎖](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
