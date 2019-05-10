---
title: HOW TO：在執行階段建立 Windows Forms 的事件處理常式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
ms.openlocfilehash: 4d2290622e648030f150d9bb06ce1f3000145759
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211451"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="bf9d7-102">HOW TO：在執行階段建立 Windows Forms 的事件處理常式</span><span class="sxs-lookup"><span data-stu-id="bf9d7-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>

<span data-ttu-id="bf9d7-103">除了建立使用 Windows Form 設計工具在 Visual Studio 中的事件，您也可以在執行階段建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bf9d7-103">In addition to creating events using the Windows Forms Designer in Visual Studio, you can also create an event handler at run time.</span></span> <span data-ttu-id="bf9d7-104">這個動作可讓您在執行階段根據程式碼中的條件來連接事件處理常式，而不需要程式一開始啟動時進行連接。</span><span class="sxs-lookup"><span data-stu-id="bf9d7-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>

## <a name="create-an-event-handler-at-run-time"></a><span data-ttu-id="bf9d7-105">在執行階段建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="bf9d7-105">Create an event handler at run time</span></span>

1. <span data-ttu-id="bf9d7-106">開啟您想要新增事件處理常式的表單。</span><span class="sxs-lookup"><span data-stu-id="bf9d7-106">Open the form that you want to add an event handler to.</span></span>

2. <span data-ttu-id="bf9d7-107">使用您要處理之事件的方法簽章，將方法新增至您的表單。</span><span class="sxs-lookup"><span data-stu-id="bf9d7-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>

     <span data-ttu-id="bf9d7-108">例如，如果您要處理<xref:System.Windows.Forms.Control.Click>事件的<xref:System.Windows.Forms.Button>控制項，您將建立的方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf9d7-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>

    ```vb
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)
       ' Add event handler code here.
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
    // Add event handler code here.
    }
    ```

    ```cpp
    private:
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          // Add event handler code here.
       }
    ```

3. <span data-ttu-id="bf9d7-109">將程式碼新增至您的應用程式的適當事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bf9d7-109">Add code to the event handler as appropriate to your application.</span></span>

4. <span data-ttu-id="bf9d7-110">決定您要為其建立事件處理常式的表單或控制項。</span><span class="sxs-lookup"><span data-stu-id="bf9d7-110">Determine which form or control you want to create an event handler for.</span></span>

5. <span data-ttu-id="bf9d7-111">在您表單類別內的方法中，新增程式碼以指定要處理事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bf9d7-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="bf9d7-112">例如，下列程式碼指定事件處理常式`button1_Click`控制代碼<xref:System.Windows.Forms.Control.Click>事件的<xref:System.Windows.Forms.Button>控制項：</span><span class="sxs-lookup"><span data-stu-id="bf9d7-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <span data-ttu-id="bf9d7-113"><xref:System.ComponentModel.EventHandlerList.AddHandler%2A>上述 Visual Basic 程式碼所示的方法會建立按鈕的 click 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bf9d7-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf9d7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf9d7-114">See also</span></span>

- [<span data-ttu-id="bf9d7-115">在 Windows Forms 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="bf9d7-115">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="bf9d7-116">事件處理常式概觀</span><span class="sxs-lookup"><span data-stu-id="bf9d7-116">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="bf9d7-117">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="bf9d7-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
