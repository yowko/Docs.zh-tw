---
title: 如何：區分按一下和按兩下
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- mouse [Windows Forms], click
- mouse [Windows Forms], double-click
- mouse clicks [Windows Forms], single versus double
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
ms.openlocfilehash: 84d085700091c4e7b8658e8eac4cf86fbd7730d5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555439"
---
# <a name="how-to-distinguish-between-clicks-and-double-clicks"></a>如何：區分按一下和按兩下
一般而言，單一「按一下」(click) 會啟始使用者介面 (UI) 動作，而「按兩下」(double-click) 會擴充此動作。 例如，按一下通常會選取項目，而按兩下可編輯選取的項目。 不過，Windows Form Click 事件並不輕易滿足按一下和按兩下會執行不相容動作的案例，因為會先執行與 <xref:System.Windows.Forms.Control.Click> 或 <xref:System.Windows.Forms.Control.MouseClick> 事件相關的動作，之後此動作才會與 <xref:System.Windows.Forms.Control.DoubleClick> 或 <xref:System.Windows.Forms.Control.MouseDoubleClick> 事件相關。 本主題會示範兩種解決這個問題的方案。 一個解決方案是處理按兩下事件，並復原處理 Click 事件的動作。 在罕見的情況下您可能需要處理 <xref:System.Windows.Forms.Control.MouseDown> 事件並使用 <xref:System.Windows.Forms.SystemInformation> 類別的 <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> 和 <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> 屬性來模擬按一下和按兩下行為。 您可測量點擊間隔時間，如果第二個點擊在達到 <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> 的值之前就先發生，且該點擊位於由 <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> 所定義的矩形內，則執行按兩下動作；否則執行按一下動作。  
  
### <a name="to-roll-back-a-click-action"></a>復原按一下動作  
  
-   請確定您正在使用的控制項具有標準的按兩下行為。 如果沒有，請以 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法啟用此控制項。 處理此按兩下事件，並復原按一下動作，以及復原按兩下動作。 下列程式碼範例示範如何在已啟用按兩下的情況下建立自訂按鈕，以及如何復原按兩下事件處理程式碼中的按一下動作。  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### <a name="to-distinguish-between-clicks-in-the-mousedown-event"></a>區分 MouseDown 事件中的按一下  
  
-   請處理 <xref:System.Windows.Forms.Control.MouseDown> 事件，並使用適當的 <xref:System.Windows.Forms.SystemInformation> 屬性和 <xref:System.Windows.Forms.Timer> 元件來決定點擊之間的位置和時間範圍。 根據按一下或按兩下進行與否，執行適當的動作。 下列程式碼範例會示範其做法。  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這些範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 建置這些範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這些範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 應用程式中的滑鼠輸入](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
