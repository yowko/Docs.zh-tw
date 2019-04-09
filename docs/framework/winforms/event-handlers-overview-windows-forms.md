---
title: 事件處理常式概觀 (Windows Form)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
ms.openlocfilehash: 05acbfaf427060d015c2445360a7d73ebe97d070
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186078"
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="f2b0f-102">事件處理常式概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="f2b0f-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="f2b0f-103">事件處理常式是繫結至事件的方法。</span><span class="sxs-lookup"><span data-stu-id="f2b0f-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="f2b0f-104">當引發事件時，會執行內的事件處理常式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f2b0f-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="f2b0f-105">每個事件處理常式提供可讓您正確地處理事件的兩個參數。</span><span class="sxs-lookup"><span data-stu-id="f2b0f-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="f2b0f-106">下列範例顯示的事件處理常式<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="f2b0f-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 <span data-ttu-id="f2b0f-107">第一個參數，`sender`，提供引發事件之物件的參考。</span><span class="sxs-lookup"><span data-stu-id="f2b0f-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="f2b0f-108">第二個參數， `e`，在上述範例中，會傳遞物件特定處理的事件。</span><span class="sxs-lookup"><span data-stu-id="f2b0f-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="f2b0f-109">藉由參考物件的屬性 （和，某些情況下，其方法），您可以取得資訊，例如滑鼠事件或資料傳輸在拖放事件中的滑鼠位置。</span><span class="sxs-lookup"><span data-stu-id="f2b0f-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="f2b0f-110">通常每個事件，就會產生與第二個參數的不同事件物件類型的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f2b0f-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="f2b0f-111">事件處理常式，如<xref:System.Windows.Forms.Control.MouseDown>和<xref:System.Windows.Forms.Control.MouseUp>事件，都有相同的物件類型，其第二個參數。</span><span class="sxs-lookup"><span data-stu-id="f2b0f-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="f2b0f-112">針對這些類型的事件，您可以使用相同的事件處理常式來處理這兩個事件。</span><span class="sxs-lookup"><span data-stu-id="f2b0f-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="f2b0f-113">您也可以使用相同的事件處理常式來處理不同的控制項相同的事件。</span><span class="sxs-lookup"><span data-stu-id="f2b0f-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="f2b0f-114">比方說，如果您有一群<xref:System.Windows.Forms.RadioButton>表單上的控制項，您可以建立單一事件處理常式<xref:System.Windows.Forms.Control.Click>事件，而且有每個控制項<xref:System.Windows.Forms.Control.Click>事件繫結至單一事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f2b0f-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="f2b0f-115">如需詳細資訊，請參閱[如何：將多個事件連線至 Windows Forms 中的單一事件處理常式](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="f2b0f-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b0f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2b0f-116">See also</span></span>

- [<span data-ttu-id="f2b0f-117">在 Windows Form 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="f2b0f-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="f2b0f-118">事件概觀</span><span class="sxs-lookup"><span data-stu-id="f2b0f-118">Events Overview</span></span>](events-overview-windows-forms.md)
