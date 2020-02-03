---
title: 滑鼠指標
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: 4e8349effcd9b59045e39b763b4cb8b7d2fceb91
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740952"
---
# <a name="mouse-pointers-in-windows-forms"></a>Windows Form 中的滑鼠指標
滑鼠*指標*（有時也稱為游標）是一個點陣圖，它會指定螢幕上的焦點點，以使用滑鼠來進行使用者輸入。 本主題概述 Windows Forms 中的滑鼠指標，並說明一些修改和控制滑鼠指標的方式。  
  
## <a name="accessing-the-mouse-pointer"></a>存取滑鼠指標  
 滑鼠指標是由 <xref:System.Windows.Forms.Cursor> 類別表示，而每個 <xref:System.Windows.Forms.Control> 都有一個 <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> 屬性，可指定該控制項的指標。 <xref:System.Windows.Forms.Cursor> 類別包含描述指標的屬性，例如 <xref:System.Windows.Forms.Cursor.Position%2A> 和 <xref:System.Windows.Forms.Cursor.HotSpot%2A> 屬性，以及可修改指標外觀的方法，例如 <xref:System.Windows.Forms.Cursor.Show%2A>、<xref:System.Windows.Forms.Cursor.Hide%2A>和 <xref:System.Windows.Forms.Cursor.DrawStretched%2A> 方法。  
  
## <a name="controlling-the-mouse-pointer"></a>控制滑鼠指標  
 有時候，您可能會想要限制可以使用滑鼠指標的區域，或變更滑鼠的位置。 您可以使用 <xref:System.Windows.Forms.Cursor>的 <xref:System.Windows.Forms.Cursor.Position%2A> 屬性，取得或設定滑鼠的目前位置。 此外，您可以限制可以使用滑鼠指標的區域是設定 <xref:System.Windows.Forms.Cursor.Clip%2A> 屬性。 根據預設，剪輯區域是整個畫面。  
  
## <a name="changing-the-mouse-pointer"></a>變更滑鼠指標  
 變更滑鼠指標是提供意見反應給使用者的重要方式。 例如，您可以在 <xref:System.Windows.Forms.Control.MouseEnter> 的處理常式中修改滑鼠指標，並 <xref:System.Windows.Forms.Control.MouseLeave> 事件來告知使用者發生計算，並限制控制項中的使用者互動。 有時候，滑鼠指標會因為系統事件而變更，例如當您的應用程式牽涉到拖放作業時。  
  
 變更滑鼠指標的主要方式是將控制項的 [<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>] 或 [<xref:System.Windows.Forms.Control.DefaultCursor%2A>] 屬性設定為新的 <xref:System.Windows.Forms.Cursor>。 如需變更滑鼠指標的範例，請參閱 <xref:System.Windows.Forms.Cursor> 類別中的程式碼範例。 此外，<xref:System.Windows.Forms.Cursors> 類別會針對許多不同類型的指標公開一組 <xref:System.Windows.Forms.Cursor> 物件，例如類似手形的指標。 當滑鼠指標位於控制項上時，若要顯示類似沙漏的等候指標，請使用 <xref:System.Windows.Forms.Control> 類別的 <xref:System.Windows.Forms.Control.UseWaitCursor%2A> 屬性。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Cursor>
- [Windows Forms 應用程式中的滑鼠輸入](mouse-input-in-a-windows-forms-application.md)
- [Windows Forms 中的拖放功能](drag-and-drop-functionality-in-windows-forms.md)
