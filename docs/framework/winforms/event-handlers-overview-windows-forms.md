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
ms.openlocfilehash: ffec8a9f8e080dec78152e62e00e2dceefbdaab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141688"
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="9fefa-102">事件處理常式概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="9fefa-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="9fefa-103">事件處理常式是綁定到事件的方法。</span><span class="sxs-lookup"><span data-stu-id="9fefa-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="9fefa-104">引發事件時，將執行事件處理常式中的代碼。</span><span class="sxs-lookup"><span data-stu-id="9fefa-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="9fefa-105">每個事件處理常式提供兩個參數，允許您正確處理事件。</span><span class="sxs-lookup"><span data-stu-id="9fefa-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="9fefa-106">下面的示例顯示了<xref:System.Windows.Forms.Button>控制項<xref:System.Windows.Forms.Control.Click>事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="9fefa-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
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
  
 <span data-ttu-id="9fefa-107">第一個參數`sender`提供引發事件的物件的引用。</span><span class="sxs-lookup"><span data-stu-id="9fefa-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="9fefa-108">在上面的示例中，`e`第二個參數傳遞特定于正在處理的事件的物件。</span><span class="sxs-lookup"><span data-stu-id="9fefa-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="9fefa-109">通過引用物件的屬性（有時，有時，其方法），可以獲取資訊，例如滑鼠的位置，用於滑鼠事件或在拖放事件中傳輸的資料。</span><span class="sxs-lookup"><span data-stu-id="9fefa-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="9fefa-110">通常，每個事件都會為第二個參數生成具有不同事件物件類型的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="9fefa-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="9fefa-111">某些事件處理常式（如<xref:System.Windows.Forms.Control.MouseDown>和<xref:System.Windows.Forms.Control.MouseUp>事件的事件處理常式）對於其第二個參數具有相同的物件類型。</span><span class="sxs-lookup"><span data-stu-id="9fefa-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="9fefa-112">對於這些類型的事件，可以使用同一事件處理常式來處理這兩個事件。</span><span class="sxs-lookup"><span data-stu-id="9fefa-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="9fefa-113">您還可以使用同一事件處理常式處理不同控制項的同一事件。</span><span class="sxs-lookup"><span data-stu-id="9fefa-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="9fefa-114">例如，如果表單上有一組<xref:System.Windows.Forms.RadioButton>控制項，則可以為<xref:System.Windows.Forms.Control.Click>事件創建單個事件處理常式，並將每個控制項<xref:System.Windows.Forms.Control.Click>的事件綁定到單個事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="9fefa-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="9fefa-115">有關詳細資訊，請參閱[：將多個事件連接到 Windows 表單中的單個事件處理常式](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="9fefa-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fefa-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fefa-116">See also</span></span>

- [<span data-ttu-id="9fefa-117">在 Windows Forms 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="9fefa-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="9fefa-118">事件概觀</span><span class="sxs-lookup"><span data-stu-id="9fefa-118">Events Overview</span></span>](events-overview-windows-forms.md)
