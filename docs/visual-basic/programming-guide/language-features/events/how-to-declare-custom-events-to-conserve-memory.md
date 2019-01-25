---
title: HOW TO：宣告自訂事件以節省記憶體 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: bf22c2029671588ab0ebaefd2554fcb2a5a1131c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719517"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="020ce-102">HOW TO：宣告自訂事件以節省記憶體 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="020ce-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="020ce-103">重要的應用程式保持其記憶體使用量低時，有幾種情況。</span><span class="sxs-lookup"><span data-stu-id="020ce-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="020ce-104">自訂事件可讓應用程式使用的記憶體只會針對它所處理的事件。</span><span class="sxs-lookup"><span data-stu-id="020ce-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="020ce-105">根據預設，當類別宣告事件時，編譯器會配置記憶體來儲存事件資訊的欄位。</span><span class="sxs-lookup"><span data-stu-id="020ce-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="020ce-106">如果類別有許多未使用的事件，會不必要地佔用記憶體。</span><span class="sxs-lookup"><span data-stu-id="020ce-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="020ce-107">而不是使用 Visual Basic 提供的事件的預設實作，您可以使用自訂的事件，更仔細管理的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="020ce-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="020ce-108">範例</span><span class="sxs-lookup"><span data-stu-id="020ce-108">Example</span></span>  
 <span data-ttu-id="020ce-109">在此範例中，類別會使用一個執行個體<xref:System.ComponentModel.EventHandlerList>類別，儲存在`Events`欄位，用於儲存事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="020ce-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="020ce-110"><xref:System.ComponentModel.EventHandlerList>類別是設計用來保存委派的最佳化的清單類別。</span><span class="sxs-lookup"><span data-stu-id="020ce-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="020ce-111">類別使用中的所有事件`Events`欄位來追蹤哪些方法會處理每個事件。</span><span class="sxs-lookup"><span data-stu-id="020ce-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="020ce-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="020ce-112">See also</span></span>
- <xref:System.ComponentModel.EventHandlerList>
- [<span data-ttu-id="020ce-113">事件</span><span class="sxs-lookup"><span data-stu-id="020ce-113">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="020ce-114">如何：宣告自訂事件以避免封鎖</span><span class="sxs-lookup"><span data-stu-id="020ce-114">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
