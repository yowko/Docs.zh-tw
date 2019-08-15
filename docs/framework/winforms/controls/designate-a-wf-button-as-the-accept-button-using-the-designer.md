---
title: 作法：使用設計工具將 Windows Forms 的按鈕指定為接受按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27ecb26c493232bcfb996d012f9760b7ef91e5b2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039663"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>作法：使用設計工具將 Windows Forms 的按鈕指定為接受按鈕
在任何 Windows Form 上, 您可以將<xref:System.Windows.Forms.Button>控制項指定為 [接受] 按鈕, 也稱為 [預設值] 按鈕。 每當使用者按下 ENTER 鍵時, 不論表單上的其他控制項有焦點, 都會按一下 [預設] 按鈕。 這種情況的例外狀況是當具有焦點的控制項是另一個按鈕時, 在此情況下, 將會按一下具有焦點的按鈕 (或多行文字方塊), 或陷印 ENTER 鍵的自訂控制項。

## <a name="to-designate-the-accept-button"></a>若要指定接受按鈕

1. 選取按鈕所在的表單。

2. 在 [**屬性**] 視窗中, 將窗<xref:System.Windows.Forms.Form.AcceptButton%2A>體的屬性<xref:System.Windows.Forms.Button>設為控制項的名稱。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Button 控制項概觀](button-control-overview-windows-forms.md)
- [選取 Windows Forms Button 控制項的方法](ways-to-select-a-windows-forms-button-control.md)
- [如何：回應 Windows Forms 按鈕點擊](how-to-respond-to-windows-forms-button-clicks.md)
- [如何：使用設計工具將 Windows Forms 按鈕指定為 [取消] 按鈕](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Button 控制項](button-control-windows-forms.md)
