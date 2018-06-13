---
title: Windows Form 中的滑鼠指標
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: ed6312cb386d1557d4217a330318664b4e87c330
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539513"
---
# <a name="mouse-pointers-in-windows-forms"></a>Windows Form 中的滑鼠指標
滑鼠*指標*，這有時也稱為資料指標，是指定婧鎏鶗懘為使用者輸入，使用滑鼠在螢幕的點陣圖。 本主題提供滑鼠指標在 Windows Form 中的概觀，並描述的數種方式來修改和控制滑鼠指標。  
  
## <a name="accessing-the-mouse-pointer"></a>存取滑鼠指標  
 將滑鼠指標由<xref:System.Windows.Forms.Cursor>類別，而每個<xref:System.Windows.Forms.Control>具有<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>屬性，指定該控制項的指標。 <xref:System.Windows.Forms.Cursor>類別包含屬性，例如描述指標<xref:System.Windows.Forms.Cursor.Position%2A>和<xref:System.Windows.Forms.Cursor.HotSpot%2A>屬性和方法，例如修改指標的外觀<xref:System.Windows.Forms.Cursor.Show%2A>， <xref:System.Windows.Forms.Cursor.Hide%2A>，和<xref:System.Windows.Forms.Cursor.DrawStretched%2A>方法。  
  
## <a name="controlling-the-mouse-pointer"></a>控制滑鼠指標  
 有時您可能想要限制在滑鼠指標可用或變更滑鼠位置的區域。 您可以取得或設定目前的位置，使用滑鼠<xref:System.Windows.Forms.Cursor.Position%2A>屬性<xref:System.Windows.Forms.Cursor>。 此外，您可以限制可以使用滑鼠指標的區域是設定<xref:System.Windows.Forms.Cursor.Clip%2A>屬性。 裁剪區域中的，依預設，會是整個螢幕。  
  
## <a name="changing-the-mouse-pointer"></a>變更滑鼠指標  
 變更滑鼠指標是一個重要方法的意見反應提供給使用者。 例如，可以修改滑鼠指標的處理常式中<xref:System.Windows.Forms.Control.MouseEnter>和<xref:System.Windows.Forms.Control.MouseLeave>事件發生的計算，告訴使用者，並限制使用者在控制項中的互動。 有時候，滑鼠指標會變更，因為系統事件，例如，當您的應用程式參與拖放作業。  
  
 若要變更滑鼠指標的主要方式是藉由設定<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>或<xref:System.Windows.Forms.Control.DefaultCursor%2A>至新的控制項屬性<xref:System.Windows.Forms.Cursor>。 範例變更滑鼠指標，請參閱中的程式碼範例<xref:System.Windows.Forms.Cursor>類別。 此外，<xref:System.Windows.Forms.Cursors>類別會公開一組<xref:System.Windows.Forms.Cursor>許多不同類型的指標，例如類似手形指標的物件。 若要顯示等待指標，這類似於以沙漏來表示，，每當滑鼠指標位於控制項上時，使用<xref:System.Windows.Forms.Control.UseWaitCursor%2A>屬性<xref:System.Windows.Forms.Control>類別。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Cursor>  
 [Windows Forms 應用程式中的滑鼠輸入](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [Windows Forms 中的拖放功能](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)
