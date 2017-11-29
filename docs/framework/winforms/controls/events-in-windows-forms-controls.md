---
title: "Windows Form 控制項中的事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e568dd7fadea8af399a63aa95347f368b4e13a54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="1c191-102">Windows Form 控制項中的事件</span><span class="sxs-lookup"><span data-stu-id="1c191-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="1c191-103">Windows Form 控制項繼承來自多個六十事件<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1c191-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1c191-104">這些包括<xref:System.Windows.Forms.Control.Paint>會導致要繪製控制項的事件，例如顯示視窗，與相關的事件<xref:System.Windows.Forms.Control.Resize>和<xref:System.Windows.Forms.Control.Layout>事件，以及低階滑鼠和鍵盤事件。</span><span class="sxs-lookup"><span data-stu-id="1c191-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="1c191-105">某些低階事件，可由合成<xref:System.Windows.Forms.Control>成語意的事件，例如<xref:System.Windows.Forms.Control.Click>和<xref:System.Windows.Forms.Control.DoubleClick>。</span><span class="sxs-lookup"><span data-stu-id="1c191-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="1c191-106">如需繼承的事件的詳細資訊，請參閱<xref:System.Windows.Forms.Control>。</span><span class="sxs-lookup"><span data-stu-id="1c191-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="1c191-107">如果您的自訂控制項需要覆寫繼承的事件功能，請覆寫繼承的 `On` *EventName* 方法，而不要附加委派。</span><span class="sxs-lookup"><span data-stu-id="1c191-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="1c191-108">如果您不熟悉 .NET Framework 中的事件模型，請參閱[從元件引發事件](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0)。</span><span class="sxs-lookup"><span data-stu-id="1c191-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c191-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c191-109">See Also</span></span>  
 [<span data-ttu-id="1c191-110">覆寫 OnPaint 方法</span><span class="sxs-lookup"><span data-stu-id="1c191-110">Overriding the OnPaint Method</span></span>](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [<span data-ttu-id="1c191-111">處理使用者輸入</span><span class="sxs-lookup"><span data-stu-id="1c191-111">Handling User Input</span></span>](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [<span data-ttu-id="1c191-112">定義事件</span><span class="sxs-lookup"><span data-stu-id="1c191-112">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="1c191-113">事件</span><span class="sxs-lookup"><span data-stu-id="1c191-113">Events</span></span>](../../../../docs/standard/events/index.md)
