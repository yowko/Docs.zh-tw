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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 130cbda875d6a56f826aefea341d233ea4b3731d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="4b65b-102">如何：宣告自訂事件以節省記憶體 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b65b-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="4b65b-103">重要的應用程式維持在其記憶體使用量很低時，有幾種情況。</span><span class="sxs-lookup"><span data-stu-id="4b65b-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="4b65b-104">自訂事件可讓應用程式使用記憶體僅適用於處理事件。</span><span class="sxs-lookup"><span data-stu-id="4b65b-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="4b65b-105">根據預設，當類別宣告的情況下，編譯器會配置記憶體來儲存事件資訊的欄位。</span><span class="sxs-lookup"><span data-stu-id="4b65b-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="4b65b-106">如果類別有許多未使用的事件，它們其實不需要的記憶體。</span><span class="sxs-lookup"><span data-stu-id="4b65b-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="4b65b-107">而不是使用 Visual Basic 提供的事件的預設實作，您可以使用自訂事件更謹慎管理的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="4b65b-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b65b-108">範例</span><span class="sxs-lookup"><span data-stu-id="4b65b-108">Example</span></span>  
 <span data-ttu-id="4b65b-109">在此範例中，類別會使用一個執行個體<xref:System.ComponentModel.EventHandlerList>類別中，儲存在`Events`欄位，用於儲存事件的相關資訊。</xref:System.ComponentModel.EventHandlerList></span><span class="sxs-lookup"><span data-stu-id="4b65b-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="4b65b-110"><xref:System.ComponentModel.EventHandlerList>類別是設計用來保存委派最佳化的清單類別。</xref:System.ComponentModel.EventHandlerList></span><span class="sxs-lookup"><span data-stu-id="4b65b-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="4b65b-111">類別使用中的所有事件`Events`欄位來追蹤每個事件處理方法。</span><span class="sxs-lookup"><span data-stu-id="4b65b-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 <span data-ttu-id="4b65b-112">[!code-vb[VbVbalrEvents #&22;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4b65b-112">[!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b65b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b65b-113">See Also</span></span>  
 <span data-ttu-id="4b65b-114"><xref:System.ComponentModel.EventHandlerList></xref:System.ComponentModel.EventHandlerList></span><span class="sxs-lookup"><span data-stu-id="4b65b-114"><xref:System.ComponentModel.EventHandlerList></span></span>   
<span data-ttu-id="4b65b-115"> [事件](../../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="4b65b-115"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="4b65b-116"> [如何：宣告自訂事件以避免封鎖](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)</span><span class="sxs-lookup"><span data-stu-id="4b65b-116"> [How to: Declare Custom Events To Avoid Blocking](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)</span></span>
