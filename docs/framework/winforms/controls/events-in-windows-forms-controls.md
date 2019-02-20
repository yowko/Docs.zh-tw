---
title: Windows Form 控制項中的事件
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 56de08f039fd4dee9dcc5a1b3f86cc0e8e577b43
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442434"
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="2ddfa-102">Windows Form 控制項中的事件</span><span class="sxs-lookup"><span data-stu-id="2ddfa-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="2ddfa-103">將 Windows Forms 控制項繼承 60 個以上的事件，從<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="2ddfa-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2ddfa-104">其中包括<xref:System.Windows.Forms.Control.Paint>事件，這會導致要繪製的控制項，例如顯示視窗中，與相關的事件<xref:System.Windows.Forms.Control.Resize>和<xref:System.Windows.Forms.Control.Layout>事件，以及低階的滑鼠和鍵盤事件。</span><span class="sxs-lookup"><span data-stu-id="2ddfa-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="2ddfa-105">有些低階事件會由合成<xref:System.Windows.Forms.Control>語意的事件，例如<xref:System.Windows.Forms.Control.Click>和<xref:System.Windows.Forms.Control.DoubleClick>。</span><span class="sxs-lookup"><span data-stu-id="2ddfa-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="2ddfa-106">如需繼承事件的詳細資訊，請參閱<xref:System.Windows.Forms.Control>。</span><span class="sxs-lookup"><span data-stu-id="2ddfa-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="2ddfa-107">如果您的自訂控制項需要覆寫繼承的事件功能，請覆寫繼承的 `On` *EventName* 方法，而不要附加委派。</span><span class="sxs-lookup"><span data-stu-id="2ddfa-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="2ddfa-108">如果您不熟悉 .NET Framework 中的事件模型，請參閱[從元件引發事件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="2ddfa-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ddfa-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ddfa-109">See also</span></span>
- [<span data-ttu-id="2ddfa-110">覆寫 OnPaint 方法</span><span class="sxs-lookup"><span data-stu-id="2ddfa-110">Overriding the OnPaint Method</span></span>](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)
- [<span data-ttu-id="2ddfa-111">處理使用者輸入</span><span class="sxs-lookup"><span data-stu-id="2ddfa-111">Handling User Input</span></span>](../../../../docs/framework/winforms/controls/handling-user-input.md)
- [<span data-ttu-id="2ddfa-112">定義事件</span><span class="sxs-lookup"><span data-stu-id="2ddfa-112">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="2ddfa-113">事件</span><span class="sxs-lookup"><span data-stu-id="2ddfa-113">Events</span></span>](../../../../docs/standard/events/index.md)
