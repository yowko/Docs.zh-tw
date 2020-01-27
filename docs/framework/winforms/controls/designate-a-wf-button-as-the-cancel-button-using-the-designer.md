---
title: 使用設計工具將按鈕指定為 [取消] 按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: 95d1139b6e339055f944ad0b0967a6d91283d49e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746047"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>如何：使用設計工具將 Windows Form 按鈕指定為取消按鈕
在任何 Windows Form 上，您都可以將 <xref:System.Windows.Forms.Button> 控制項指定為 [取消] 按鈕。 每當使用者按下 ESC 鍵時，就會按一下 [取消] 按鈕，而不論表單上的其他控制項有哪些焦點。 這類按鈕通常是程式設計的，可讓使用者快速結束作業，而不需要認可任何動作。

## <a name="to-designate-the-cancel-button"></a>若要指定取消按鈕

1. 選取按鈕所在的表單。

2. 在 [**屬性**] 視窗中，將表單的 [<xref:System.Windows.Forms.Form.CancelButton%2A>] 屬性設定為 <xref:System.Windows.Forms.Button> 控制項的名稱。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Button 控制項概觀](button-control-overview-windows-forms.md)
- [選取 Windows Forms Button 控制項的方法](ways-to-select-a-windows-forms-button-control.md)
- [操作說明：回應 Windows Forms Button 按一下動作](how-to-respond-to-windows-forms-button-clicks.md)
- [如何：使用設計工具將 Windows Forms 按鈕指定為接受按鈕](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Button 控制項](button-control-windows-forms.md)
