---
title: ProgressBar 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: 7dd434492cd688527ddbce5aaffa442a0b40a9e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968311"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar 控制項概觀 (Windows Form)
> [!IMPORTANT]
> <xref:System.Windows.Forms.ToolStripProgressBar> 控制項會取代 <xref:System.Windows.Forms.ProgressBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ProgressBar> 控制項，以提供回溯相容性及未來使用。  
  
 Windows Forms <xref:System.Windows.Forms.ProgressBar>控制項會以水準橫條顯示適當數目的矩形, 來指出進程的進度。 當程式完成時, 會填滿橫條。 進度列通常用來讓使用者知道等候進程完成的時間長度;例如, 載入大型檔案時。  
  
> [!NOTE]
> <xref:System.Windows.Forms.ProgressBar>控制項只能在表單上水準導向。  
  
## <a name="key-properties-and-methods"></a>索引鍵屬性和方法  
 <xref:System.Windows.Forms.ProgressBar>控制項的索引鍵屬性為<xref:System.Windows.Forms.ProgressBar.Value%2A>、 <xref:System.Windows.Forms.ProgressBar.Minimum%2A>和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>。 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>屬性會設定進度列可以顯示的最大和最小值。 <xref:System.Windows.Forms.ProgressBar.Value%2A>屬性代表完成作業所進行的進度。 由於控制項中顯示的橫條是由區塊所組成, 因此<xref:System.Windows.Forms.ProgressBar>控制項所顯示的值只會<xref:System.Windows.Forms.ProgressBar.Value%2A>接近屬性的目前值。 根據<xref:System.Windows.Forms.ProgressBar>控制項的大小<xref:System.Windows.Forms.ProgressBar.Value%2A> , 屬性會決定何時要顯示下一個區塊。  
  
 更新目前進度值最常見的方式是撰寫程式碼來設定<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性。 在載入大型檔案的範例中, 您可以將最大值設定為檔案大小 (以 kb 為單位)。 例如, 如果<xref:System.Windows.Forms.ProgressBar.Maximum%2A>屬性設定為 100, 則<xref:System.Windows.Forms.ProgressBar.Minimum%2A>屬性會設定為 10, 而<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性會設定為 50, 則會顯示5個矩形。 這是可顯示的數目一半。  
  
 不過, 除了直接<xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Value%2A>設定屬性以外, 還有其他方法可修改控制項所顯示的值。 屬性可以用來指定要<xref:System.Windows.Forms.ProgressBar.Value%2A>遞增屬性的值。 <xref:System.Windows.Forms.ProgressBar.Step%2A> 然後, 呼叫<xref:System.Windows.Forms.ProgressBar.PerformStep%2A>方法會增加值。 若要改變遞增值, 您可以使用<xref:System.Windows.Forms.ProgressBar.Increment%2A>方法, 並指定要用來<xref:System.Windows.Forms.ProgressBar.Value%2A>遞增屬性的值。  
  
 另一個以圖形方式通知使用者目前動作的控制項就是<xref:System.Windows.Forms.StatusBar>控制項。  
  
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel>和控制項會取代和加入和<xref:System.Windows.Forms.StatusBarPanel>控制項的功能; 不過, 如果您這樣做, 和控制項就會保留, 以提供回溯相容性及未來使用。 <xref:System.Windows.Forms.ToolStripStatusLabel> <xref:System.Windows.Forms.StatusStrip>決定.  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ProgressBar>
- [ProgressBar 控制項](progressbar-control-windows-forms.md)
