---
title: 事件處理常式概觀
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
ms.openlocfilehash: 10ba458197973ede35849a86fec35003f139b8d2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743466"
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="645e7-102">事件處理常式概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="645e7-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="645e7-103">事件處理常式是系結至事件的方法。</span><span class="sxs-lookup"><span data-stu-id="645e7-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="645e7-104">當引發事件時，就會執行事件處理常式中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="645e7-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="645e7-105">每個事件處理常式都會提供兩個參數，讓您可以正確地處理事件。</span><span class="sxs-lookup"><span data-stu-id="645e7-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="645e7-106">下列範例顯示 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="645e7-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
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
  
 <span data-ttu-id="645e7-107">第一個參數（`sender`）會提供引發事件之物件的參考。</span><span class="sxs-lookup"><span data-stu-id="645e7-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="645e7-108">在上述範例中，第二個參數 `e`，會傳遞所處理事件的特定物件。</span><span class="sxs-lookup"><span data-stu-id="645e7-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="645e7-109">藉由參考物件的屬性（有時也是其方法），您可以取得資訊，例如滑鼠事件的位置，或在拖放事件中傳送的資料。</span><span class="sxs-lookup"><span data-stu-id="645e7-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="645e7-110">一般來說，每個事件都會針對第二個參數產生事件處理常式，並具有不同的事件物件類型。</span><span class="sxs-lookup"><span data-stu-id="645e7-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="645e7-111">某些事件處理常式，例如 <xref:System.Windows.Forms.Control.MouseDown> 和 <xref:System.Windows.Forms.Control.MouseUp> 事件的處理常式，其第二個參數具有相同的物件類型。</span><span class="sxs-lookup"><span data-stu-id="645e7-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="645e7-112">針對這些類型的事件，您可以使用相同的事件處理常式來處理這兩個事件。</span><span class="sxs-lookup"><span data-stu-id="645e7-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="645e7-113">您也可以使用相同的事件處理常式，針對不同的控制項處理相同的事件。</span><span class="sxs-lookup"><span data-stu-id="645e7-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="645e7-114">例如，如果您在表單上有一組 <xref:System.Windows.Forms.RadioButton> 控制項，您可以為 <xref:System.Windows.Forms.Control.Click> 事件建立單一事件處理常式，並讓每個控制項的 <xref:System.Windows.Forms.Control.Click> 事件系結至單一事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="645e7-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="645e7-115">如需詳細資訊，請參閱[如何：將多個事件連接到 Windows Forms 中的單一事件處理常式](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="645e7-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="645e7-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="645e7-116">See also</span></span>

- [<span data-ttu-id="645e7-117">在 Windows Forms 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="645e7-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="645e7-118">事件概觀</span><span class="sxs-lookup"><span data-stu-id="645e7-118">Events Overview</span></span>](events-overview-windows-forms.md)
