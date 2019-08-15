---
title: 作法：繼承控制項類別
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: 535827db660ab1113a25a01b7a0553a1c4414c74
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037780"
---
# <a name="how-to-inherit-from-the-control-class"></a>作法：繼承控制項類別
如果您想要建立完全自訂的控制項以在 Windows Form 上使用, 您應該繼承<xref:System.Windows.Forms.Control>自類別。 從<xref:System.Windows.Forms.Control>類別繼承時, 需要您執行更多規劃和實作為, 同時也會提供您最大範圍的選項。 當繼承自<xref:System.Windows.Forms.Control>時, 您會繼承可讓控制項運作的非常基本功能。 <xref:System.Windows.Forms.Control>類別中固有的功能會透過鍵盤和滑鼠來處理使用者輸入、定義控制項的界限和大小、提供 windows 控制碼, 以及提供訊息處理和安全性。 它不會併入任何繪製功能 (在此例中是控制項圖形化介面的實際轉譯)，也不會併入任何特定的使用者互動功能。 您必須透過自訂程式碼來提供上述一切。

## <a name="to-create-a-custom-control"></a>建立自訂控制項

1. 建立新的 [Windows 應用程式] 或 [Windows 控制項程式庫] 專案。

2. 從 [專案] 功能表中，選擇 [新增類別]。

3. 在 [新增項目] 對話方塊中，按一下 [自訂控制項]。

     新的自訂控制項會新增至您的專案。

4. 按 F7 鍵，開啟自訂控制項的 [程式碼編輯器]。

5. 找出<xref:System.Windows.Forms.Control.OnPaint%2A>方法, 這會是空的, 但不包括呼叫<xref:System.Windows.Forms.Control.OnPaint%2A>基類的方法。

6. 修改程式碼，以併入您要用於控制項的任何自訂繪製功能。

     如需撰寫程式碼來轉譯控制項圖形的相關資訊，請參閱[自訂控制項繪製和轉譯](custom-control-painting-and-rendering.md)。

7. 實作您的控制項將併入的任何自訂方法、屬性或事件。

8. 儲存並測試您的控制項。

## <a name="see-also"></a>另請參閱

- [各種自訂控制項](varieties-of-custom-controls.md)
- [如何：繼承自 UserControl 類別](how-to-inherit-from-the-usercontrol-class.md)
- [如何：繼承自現有的 Windows Forms 控制項](how-to-inherit-from-existing-windows-forms-controls.md)
- [如何：Windows Forms 的作者控制項](how-to-author-controls-for-windows-forms.md)
- [Visual Basic 中的繼承事件處理常式疑難排解](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [在設計階段開發 Windows Forms 控制項](developing-windows-forms-controls-at-design-time.md)
