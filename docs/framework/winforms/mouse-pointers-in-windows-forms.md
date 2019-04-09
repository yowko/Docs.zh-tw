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
ms.openlocfilehash: e9b572ba40618a72b8db58917008ebd61a23de79
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122781"
---
# <a name="mouse-pointers-in-windows-forms"></a>Windows Form 中的滑鼠指標
滑鼠*指標*，這有時稱為資料指標，是指定婧鎏鶗懘為使用者輸入，使用滑鼠在螢幕的點陣圖。 本主題提供在 Windows Form 中的滑鼠指標的概觀，並說明一些修改和控制滑鼠指標的方式。  
  
## <a name="accessing-the-mouse-pointer"></a>存取滑鼠指標  
 表示滑鼠指標<xref:System.Windows.Forms.Cursor>類別，和每個<xref:System.Windows.Forms.Control>具有<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>屬性，指定該控制項的指標。 <xref:System.Windows.Forms.Cursor>類別包含屬性描述的指標，例如<xref:System.Windows.Forms.Cursor.Position%2A>並<xref:System.Windows.Forms.Cursor.HotSpot%2A>屬性和方法，例如可修改的指標，外觀<xref:System.Windows.Forms.Cursor.Show%2A>， <xref:System.Windows.Forms.Cursor.Hide%2A>，和<xref:System.Windows.Forms.Cursor.DrawStretched%2A>方法。  
  
## <a name="controlling-the-mouse-pointer"></a>控制滑鼠指標  
 有時候您可能要限制在滑鼠指標可用或變更滑鼠位置的區域。 您可以取得或設定目前的位置，使用滑鼠<xref:System.Windows.Forms.Cursor.Position%2A>屬性<xref:System.Windows.Forms.Cursor>。 此外，您可以限制可以使用滑鼠指標的區域設定<xref:System.Windows.Forms.Cursor.Clip%2A>屬性。 裁剪區域中的，根據預設，會是整個螢幕。  
  
## <a name="changing-the-mouse-pointer"></a>變更滑鼠指標  
 變更滑鼠指標會提供回饋給使用者的重要方法。 比方說，可以修改滑鼠指標的處理常式<xref:System.Windows.Forms.Control.MouseEnter>和<xref:System.Windows.Forms.Control.MouseLeave>事件來告訴使用者發生的計算及限制在控制項中的使用者互動。 有時候，將滑鼠指標會變更，因為系統事件，例如當您的應用程式參與拖放作業。  
  
 若要變更滑鼠指標的主要方式是藉由設定<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>或是<xref:System.Windows.Forms.Control.DefaultCursor%2A>到新的控制項屬性<xref:System.Windows.Forms.Cursor>。 如需變更滑鼠指標的範例，請參閱中的程式碼範例<xref:System.Windows.Forms.Cursor>類別。 颾魤 ㄛ<xref:System.Windows.Forms.Cursors>類別會公開一組<xref:System.Windows.Forms.Cursor>許多不同類型的指標，例如類似手掌的形狀指標的物件。 若要顯示等候指標，這類似於沙漏，每當滑鼠指標位於控制項上時，使用<xref:System.Windows.Forms.Control.UseWaitCursor%2A>屬性<xref:System.Windows.Forms.Control>類別。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Cursor>
- [Windows Forms 應用程式中的滑鼠輸入](mouse-input-in-a-windows-forms-application.md)
- [Windows Form 中的拖放功能](drag-and-drop-functionality-in-windows-forms.md)
