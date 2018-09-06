---
title: 在 Windows Form 中建立事件處理常式
ms.date: 03/30/2017
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
ms.openlocfilehash: 9095946d52360c69fd6c4dd6285039fb3e1874d5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43878925"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="d9be0-102">在 Windows Form 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="d9be0-102">Creating Event Handlers in Windows Forms</span></span>
<span data-ttu-id="d9be0-103">事件處理常式是程式碼中的一項程序，可以決定發生事件時 (例如當使用者按一下按鈕，或訊息佇列收到訊息時) 所應執行的動作。</span><span class="sxs-lookup"><span data-stu-id="d9be0-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="d9be0-104">當事件引發時，收到事件的事件處理常式或處理常式會隨即執行。</span><span class="sxs-lookup"><span data-stu-id="d9be0-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="d9be0-105">事件可以指派給多個處理常式，而處理特定事件的方法也可隨機變更。</span><span class="sxs-lookup"><span data-stu-id="d9be0-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="d9be0-106">您也可以使用 Windows Forms 設計工具建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d9be0-106">You can also use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9be0-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="d9be0-107">In This Section</span></span>  
 [<span data-ttu-id="d9be0-108">事件概觀</span><span class="sxs-lookup"><span data-stu-id="d9be0-108">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)  
 <span data-ttu-id="d9be0-109">說明事件模型與委派的角色。</span><span class="sxs-lookup"><span data-stu-id="d9be0-109">Explains the event model and the role of delegates.</span></span>  
  
 [<span data-ttu-id="d9be0-110">事件處理常式概觀</span><span class="sxs-lookup"><span data-stu-id="d9be0-110">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 <span data-ttu-id="d9be0-111">說明如何處理事件。</span><span class="sxs-lookup"><span data-stu-id="d9be0-111">Describes how to handle events.</span></span>  
  
 [<span data-ttu-id="d9be0-112">如何：在執行階段建立 Windows Forms 的事件處理常式</span><span class="sxs-lookup"><span data-stu-id="d9be0-112">How to: Create Event Handlers at Run Time for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)  
 <span data-ttu-id="d9be0-113">提供如何隨機回應系統或使用者事件的指引。</span><span class="sxs-lookup"><span data-stu-id="d9be0-113">Gives directions for responding to system or user events dynamically.</span></span>  
  
 [<span data-ttu-id="d9be0-114">如何：在 Windows Forms 中將多個事件連線至單一事件處理常式</span><span class="sxs-lookup"><span data-stu-id="d9be0-114">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)  
 <span data-ttu-id="d9be0-115">提供如何透過事件指派相同功能給多個控制項的指引。</span><span class="sxs-lookup"><span data-stu-id="d9be0-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>  
  
 [<span data-ttu-id="d9be0-116">Windows Forms 中的事件順序</span><span class="sxs-lookup"><span data-stu-id="d9be0-116">Order of Events in Windows Forms</span></span>](../../../docs/framework/winforms/order-of-events-in-windows-forms.md)  
 <span data-ttu-id="d9be0-117">說明事件在 Windows Forms 控制項中的引發順序。</span><span class="sxs-lookup"><span data-stu-id="d9be0-117">Describes the order in which events are raised in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="d9be0-118">如何：使用設計工具建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="d9be0-118">How to: Create Event Handlers Using the Designer</span></span>](https://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2)  
 <span data-ttu-id="d9be0-119">說明如何使用 Windows Forms 設計工具建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d9be0-119">Describes how to use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d9be0-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="d9be0-120">Related Sections</span></span>  
 [<span data-ttu-id="d9be0-121">事件</span><span class="sxs-lookup"><span data-stu-id="d9be0-121">Events</span></span>](../../../docs/standard/events/index.md)  
 <span data-ttu-id="d9be0-122">提供有關如何使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 處理及引發事件之主題的連結。</span><span class="sxs-lookup"><span data-stu-id="d9be0-122">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [<span data-ttu-id="d9be0-123">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="d9be0-123">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="d9be0-124">列出常見於繼承之元件中所發生的事件處理常式問題。</span><span class="sxs-lookup"><span data-stu-id="d9be0-124">Lists common issues that occur with event handlers in inherited components.</span></span>
