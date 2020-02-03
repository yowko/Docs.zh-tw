---
title: ProgressBar 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: a0c4a0401d06614ab3ad148b932ebc64080c592c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741287"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar 控制項概觀 (Windows Form)
> [!IMPORTANT]
> <xref:System.Windows.Forms.ToolStripProgressBar> 控制項會取代 <xref:System.Windows.Forms.ProgressBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ProgressBar> 控制項，以提供回溯相容性及未來使用。  
  
 Windows Forms <xref:System.Windows.Forms.ProgressBar> 控制項會藉由顯示在水準列中排列的適當矩形數目，來指出進程的進度。 當程式完成時，會填滿橫條。 進度列通常用來讓使用者知道等候進程完成的時間長度;例如，載入大型檔案時。  
  
> [!NOTE]
> <xref:System.Windows.Forms.ProgressBar> 控制項只能在表單上水準導向。  
  
## <a name="key-properties-and-methods"></a>索引鍵屬性和方法  
 <xref:System.Windows.Forms.ProgressBar> 控制項的索引鍵屬性是 <xref:System.Windows.Forms.ProgressBar.Value%2A>、<xref:System.Windows.Forms.ProgressBar.Minimum%2A>和 <xref:System.Windows.Forms.ProgressBar.Maximum%2A>。 [<xref:System.Windows.Forms.ProgressBar.Minimum%2A>] 和 [<xref:System.Windows.Forms.ProgressBar.Maximum%2A>] 屬性會設定進度列可以顯示的最大和最小值。 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性代表完成作業所進行的進度。 因為控制項中顯示的橫條是由區塊所組成，所以 <xref:System.Windows.Forms.ProgressBar> 控制項所顯示的值，只會接近 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性的目前值。 根據 <xref:System.Windows.Forms.ProgressBar> 控制項的大小，<xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性會決定何時要顯示下一個區塊。  
  
 更新目前進度值最常見的方式是撰寫程式碼來設定 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性。 在載入大型檔案的範例中，您可以將最大值設定為檔案大小（以 kb 為單位）。 例如，如果 <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 屬性設為100，則 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 屬性會設定為10，而 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性會設定為50，則會顯示5個矩形。 這是可顯示的數目一半。  
  
 不過，除了直接設定 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性以外，還有其他方式可以修改 <xref:System.Windows.Forms.ProgressBar> 控制項所顯示的值。 <xref:System.Windows.Forms.ProgressBar.Step%2A> 屬性可以用來指定值，以遞增 <xref:System.Windows.Forms.ProgressBar.Value%2A> 的屬性。 然後，呼叫 <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> 方法將會增加值。 若要改變遞增值，您可以使用 <xref:System.Windows.Forms.ProgressBar.Increment%2A> 方法，並指定要用來遞增 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性的值。  
  
 另一個以圖形方式通知使用者目前動作的控制項是 <xref:System.Windows.Forms.StatusBar> 控制項。  
  
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusStrip> 和 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代 <xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項的功能，並將其加入。不過，如果您選擇，<xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項都會保留，以提供回溯相容性及未來使用。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ProgressBar>
- [ProgressBar 控制項](progressbar-control-windows-forms.md)
