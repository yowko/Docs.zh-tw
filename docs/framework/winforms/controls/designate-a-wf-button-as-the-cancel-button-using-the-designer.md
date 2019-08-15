---
title: HOW TO：使用設計工具將 Windows Forms 的按鈕指定為取消按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: cc352f15fb1e8b531cd0f9b298b2db4ce649d3cf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039640"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>作法：使用設計工具將 Windows Forms 的按鈕指定為取消按鈕
在任何 Windows Form 上, 您可以將<xref:System.Windows.Forms.Button>控制項指定為 [取消] 按鈕。 每當使用者按下 ESC 鍵時, 就會按一下 [取消] 按鈕, 而不論表單上的其他控制項有哪些焦點。 這類按鈕通常是程式設計的, 可讓使用者快速結束作業, 而不需要認可任何動作。

## <a name="to-designate-the-cancel-button"></a>若要指定取消按鈕

1. 選取按鈕所在的表單。

2. 在 [**屬性**] 視窗中, 將窗<xref:System.Windows.Forms.Form.CancelButton%2A>體的屬性<xref:System.Windows.Forms.Button>設為控制項的名稱。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Button 控制項概觀](button-control-overview-windows-forms.md)
- [選取 Windows Forms Button 控制項的方法](ways-to-select-a-windows-forms-button-control.md)
- [如何：回應 Windows Forms 按鈕點擊](how-to-respond-to-windows-forms-button-clicks.md)
- [如何：使用設計工具將 Windows Forms 按鈕指定為 [接受] 按鈕](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Button 控制項](button-control-windows-forms.md)
