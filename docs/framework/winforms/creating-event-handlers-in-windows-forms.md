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
ms.openlocfilehash: 329060e0c53178a9320be9a7cdff492d69917782
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211254"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="f1ee2-102">在 Windows Form 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="f1ee2-102">Creating Event Handlers in Windows Forms</span></span>

<span data-ttu-id="f1ee2-103">事件處理常式是程式碼中的一項程序，可以決定發生事件時 (例如當使用者按一下按鈕，或訊息佇列收到訊息時) 所應執行的動作。</span><span class="sxs-lookup"><span data-stu-id="f1ee2-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="f1ee2-104">當事件引發時，收到事件的事件處理常式或處理常式會隨即執行。</span><span class="sxs-lookup"><span data-stu-id="f1ee2-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="f1ee2-105">事件可以指派給多個處理常式，而處理特定事件的方法也可隨機變更。</span><span class="sxs-lookup"><span data-stu-id="f1ee2-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="f1ee2-106">您也可以使用 Visual Studio 中的 Windows Form 設計工具建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f1ee2-106">You can also use the Windows Forms Designer in Visual Studio to create event handlers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f1ee2-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="f1ee2-107">In This Section</span></span>

 <span data-ttu-id="f1ee2-108">[事件概觀](events-overview-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="f1ee2-108">[Events Overview](events-overview-windows-forms.md)\\</span></span>
 <span data-ttu-id="f1ee2-109">說明事件模型與委派的角色。</span><span class="sxs-lookup"><span data-stu-id="f1ee2-109">Explains the event model and the role of delegates.</span></span>

 <span data-ttu-id="f1ee2-110">[事件處理常式概觀](event-handlers-overview-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="f1ee2-110">[Event Handlers Overview](event-handlers-overview-windows-forms.md)\\</span></span>
 <span data-ttu-id="f1ee2-111">說明如何處理事件。</span><span class="sxs-lookup"><span data-stu-id="f1ee2-111">Describes how to handle events.</span></span>

 <span data-ttu-id="f1ee2-112">[如何：在執行階段建立 Windows Forms 事件處理常式](how-to-create-event-handlers-at-run-time-for-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="f1ee2-112">[How to: Create Event Handlers at Run Time for Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)\\</span></span>
 <span data-ttu-id="f1ee2-113">提供如何隨機回應系統或使用者事件的指引。</span><span class="sxs-lookup"><span data-stu-id="f1ee2-113">Gives directions for responding to system or user events dynamically.</span></span>

 <span data-ttu-id="f1ee2-114">[如何：將多個事件連線至 Windows Forms 中的單一事件處理常式](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="f1ee2-114">[How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)\\</span></span>
 <span data-ttu-id="f1ee2-115">提供如何透過事件指派相同功能給多個控制項的指引。</span><span class="sxs-lookup"><span data-stu-id="f1ee2-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>

 <span data-ttu-id="f1ee2-116">[Windows Form 中事件的順序](order-of-events-in-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="f1ee2-116">[Order of Events in Windows Forms](order-of-events-in-windows-forms.md)\\</span></span>
 <span data-ttu-id="f1ee2-117">說明事件在 Windows Forms 控制項中的引發順序。</span><span class="sxs-lookup"><span data-stu-id="f1ee2-117">Describes the order in which events are raised in Windows Forms controls.</span></span>

 <span data-ttu-id="f1ee2-118">[如何：建立事件處理常式使用設計工具](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))描述如何使用 Windows Form 設計工具建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f1ee2-118">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Describes how to use the Windows Forms Designer to create event handlers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="f1ee2-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="f1ee2-119">Related Sections</span></span>

 <span data-ttu-id="f1ee2-120">[事件](../../standard/events/index.md)\\</span><span class="sxs-lookup"><span data-stu-id="f1ee2-120">[Events](../../standard/events/index.md)\\</span></span>
 <span data-ttu-id="f1ee2-121">提供主題連結，在處理和引發事件，使用[!INCLUDE [dnprdnshort](../../../includes/dnprdnshort-md.md)\]。</span><span class="sxs-lookup"><span data-stu-id="f1ee2-121">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)\].</span></span>

 <span data-ttu-id="f1ee2-122">[針對 Visual Basic 中的繼承事件處理常式疑難排解](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)\\</span><span class="sxs-lookup"><span data-stu-id="f1ee2-122">[Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)\\</span></span>
 <span data-ttu-id="f1ee2-123">列出常見於繼承之元件中所發生的事件處理常式問題。</span><span class="sxs-lookup"><span data-stu-id="f1ee2-123">Lists common issues that occur with event handlers in inherited components.</span></span>
