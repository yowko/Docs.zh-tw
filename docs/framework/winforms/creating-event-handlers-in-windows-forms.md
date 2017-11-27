---
title: "在 Windows Form 中建立事件處理常式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0625d5272b4c3ae4f21793d0b0fc8645158e6a2c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="88454-102">在 Windows Form 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="88454-102">Creating Event Handlers in Windows Forms</span></span>
<span data-ttu-id="88454-103">事件處理常式是程式碼中的一項程序，可以決定發生事件時 (例如當使用者按一下按鈕，或訊息佇列收到訊息時) 所應執行的動作。</span><span class="sxs-lookup"><span data-stu-id="88454-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="88454-104">當事件引發時，收到事件的事件處理常式或處理常式會隨即執行。</span><span class="sxs-lookup"><span data-stu-id="88454-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="88454-105">事件可以指派給多個處理常式，而處理特定事件的方法也可隨機變更。</span><span class="sxs-lookup"><span data-stu-id="88454-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="88454-106">您也可以使用 Windows Forms 設計工具建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="88454-106">You can also use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="88454-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="88454-107">In This Section</span></span>  
 [<span data-ttu-id="88454-108">事件概觀</span><span class="sxs-lookup"><span data-stu-id="88454-108">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)  
 <span data-ttu-id="88454-109">說明事件模型與委派的角色。</span><span class="sxs-lookup"><span data-stu-id="88454-109">Explains the event model and the role of delegates.</span></span>  
  
 [<span data-ttu-id="88454-110">事件處理常式概觀</span><span class="sxs-lookup"><span data-stu-id="88454-110">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 <span data-ttu-id="88454-111">說明如何處理事件。</span><span class="sxs-lookup"><span data-stu-id="88454-111">Describes how to handle events.</span></span>  
  
 [<span data-ttu-id="88454-112">如何：在執行階段建立 Windows Forms 的事件處理常式</span><span class="sxs-lookup"><span data-stu-id="88454-112">How to: Create Event Handlers at Run Time for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)  
 <span data-ttu-id="88454-113">提供如何隨機回應系統或使用者事件的指引。</span><span class="sxs-lookup"><span data-stu-id="88454-113">Gives directions for responding to system or user events dynamically.</span></span>  
  
 [<span data-ttu-id="88454-114">如何：在 Windows Forms 中將多個事件連線至單一事件處理常式</span><span class="sxs-lookup"><span data-stu-id="88454-114">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)  
 <span data-ttu-id="88454-115">提供如何透過事件指派相同功能給多個控制項的指引。</span><span class="sxs-lookup"><span data-stu-id="88454-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>  
  
 [<span data-ttu-id="88454-116">Windows Forms 中的事件順序</span><span class="sxs-lookup"><span data-stu-id="88454-116">Order of Events in Windows Forms</span></span>](../../../docs/framework/winforms/order-of-events-in-windows-forms.md)  
 <span data-ttu-id="88454-117">說明事件在 Windows Forms 控制項中的引發順序。</span><span class="sxs-lookup"><span data-stu-id="88454-117">Describes the order in which events are raised in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="88454-118">如何：使用設計工具建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="88454-118">How to: Create Event Handlers Using the Designer</span></span>](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2)  
 <span data-ttu-id="88454-119">說明如何使用 Windows Forms 設計工具建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="88454-119">Describes how to use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="88454-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="88454-120">Related Sections</span></span>  
 [<span data-ttu-id="88454-121">事件</span><span class="sxs-lookup"><span data-stu-id="88454-121">Events</span></span>](../../../docs/standard/events/index.md)  
 <span data-ttu-id="88454-122">提供有關如何使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 處理及引發事件之主題的連結。</span><span class="sxs-lookup"><span data-stu-id="88454-122">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [<span data-ttu-id="88454-123">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="88454-123">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="88454-124">列出常見於繼承之元件中所發生的事件處理常式問題。</span><span class="sxs-lookup"><span data-stu-id="88454-124">Lists common issues that occur with event handlers in inherited components.</span></span>
