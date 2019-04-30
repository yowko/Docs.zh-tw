---
title: Windows Form 控制項中的事件
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 41ad95de7a65dbd0cb3a0d1af8f5c8cb00c1ccdd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971972"
---
# <a name="events-in-windows-forms-controls"></a>Windows Form 控制項中的事件
將 Windows Forms 控制項繼承 60 個以上的事件，從<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。 其中包括<xref:System.Windows.Forms.Control.Paint>事件，這會導致要繪製的控制項，例如顯示視窗中，與相關的事件<xref:System.Windows.Forms.Control.Resize>和<xref:System.Windows.Forms.Control.Layout>事件，以及低階的滑鼠和鍵盤事件。 有些低階事件會由合成<xref:System.Windows.Forms.Control>語意的事件，例如<xref:System.Windows.Forms.Control.Click>和<xref:System.Windows.Forms.Control.DoubleClick>。 如需繼承事件的詳細資訊，請參閱<xref:System.Windows.Forms.Control>。  
  
 如果您的自訂控制項需要覆寫繼承的事件功能，請覆寫繼承的 `On` *EventName* 方法，而不要附加委派。 如果您不熟悉 .NET Framework 中的事件模型，請參閱[從元件引發事件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120))。  
  
## <a name="see-also"></a>另請參閱

- [覆寫 OnPaint 方法](overriding-the-onpaint-method.md)
- [處理使用者輸入](handling-user-input.md)
- [定義事件](defining-an-event-in-windows-forms-controls.md)
- [事件](../../../standard/events/index.md)
