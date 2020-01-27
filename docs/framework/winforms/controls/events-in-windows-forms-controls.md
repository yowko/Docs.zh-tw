---
title: 控制項中的事件
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: c60713917b9c84aa7fad50fb1c81fc9252149ad6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745748"
---
# <a name="events-in-windows-forms-controls"></a>Windows Form 控制項中的事件
Windows Forms 控制項從 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>繼承超過60個事件。 其中包括 <xref:System.Windows.Forms.Control.Paint> 事件，這會導致控制項繪製、顯示視窗的相關事件，例如 <xref:System.Windows.Forms.Control.Resize> 和 <xref:System.Windows.Forms.Control.Layout> 事件，以及低層級的滑鼠和鍵盤事件。 某些低層級的事件會藉由 <xref:System.Windows.Forms.Control> 為語義事件（例如 <xref:System.Windows.Forms.Control.Click> 和 <xref:System.Windows.Forms.Control.DoubleClick>）合成。 如需繼承事件的詳細資訊，請參閱 <xref:System.Windows.Forms.Control>。  
  
 如果您的自訂控制項需要覆寫繼承的事件功能，請覆寫繼承的 `On`*EventName* 方法，而不要附加委派。 如果您不熟悉 .NET Framework 中的事件模型，請參閱[從元件引發事件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120))。  
  
## <a name="see-also"></a>請參閱

- [覆寫 OnPaint 方法](overriding-the-onpaint-method.md)
- [處理使用者輸入](handling-user-input.md)
- [定義事件](defining-an-event-in-windows-forms-controls.md)
- [事件](../../../standard/events/index.md)
