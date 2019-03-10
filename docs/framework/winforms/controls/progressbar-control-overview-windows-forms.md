---
title: ProgressBar 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: db0a43534080d630323d8c1c95759fd2dcc04a85
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707935"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar 控制項概觀 (Windows Form)
> [!IMPORTANT]
>  
  <xref:System.Windows.Forms.ToolStripProgressBar> 控制項會取代 <xref:System.Windows.Forms.ProgressBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ProgressBar> 控制項，以提供回溯相容性及未來使用。  
  
 Windows Form<xref:System.Windows.Forms.ProgressBar>控制項顯示適量的矩形排列在水平列表示處理程序的進度。 處理程序完成時，會填滿的列。 進度列通常用來讓使用者大致了解長等待處理序完成;比方說，當大型檔案載入。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ProgressBar>控制項可以只會水平方向在表單上。  
  
## <a name="key-properties-and-methods"></a>索引鍵屬性和方法  
 索引鍵屬性<xref:System.Windows.Forms.ProgressBar>控制項<xref:System.Windows.Forms.ProgressBar.Value%2A>， <xref:System.Windows.Forms.ProgressBar.Minimum%2A>，和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>。 <xref:System.Windows.Forms.ProgressBar.Minimum%2A>和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>設定可以顯示進度列的最大和最小值的屬性。 <xref:System.Windows.Forms.ProgressBar.Value%2A>屬性表示已完成此作業的進度。 因為控制項中顯示的列由區塊所組成，其值會顯示所<xref:System.Windows.Forms.ProgressBar>控制僅以基本原則而論<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性的目前值。 根據大小<xref:System.Windows.Forms.ProgressBar>控制項，<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性會決定何時顯示下一個區塊。  
  
 更新目前的進度值的最常見方式是撰寫程式碼以設定<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性。 在載入大型檔案的範例中，您可能將上限的檔案，以 kb 為單位的大小。 比方說，如果<xref:System.Windows.Forms.ProgressBar.Maximum%2A>屬性設定為 100，<xref:System.Windows.Forms.ProgressBar.Minimum%2A>屬性設定為 10，而<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性設定為 50，將會顯示 5 個矩形。 這是可顯示的數字的下半部。  
  
 不過，有其他方式來修改所顯示的值<xref:System.Windows.Forms.ProgressBar>控制項，除了設定<xref:System.Windows.Forms.ProgressBar.Value%2A>直接屬性。 <xref:System.Windows.Forms.ProgressBar.Step%2A>屬性可以用來指定要遞增的值<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性。 然後，呼叫<xref:System.Windows.Forms.ProgressBar.PerformStep%2A>方法會遞增的值。 若要變化的遞增值，您可以使用<xref:System.Windows.Forms.ProgressBar.Increment%2A>方法並指定用來遞增值<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性。  
  
 以圖形方式會通知使用者是目前的動作的另一個控制項是<xref:System.Windows.Forms.StatusBar>控制項。  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip>及<xref:System.Windows.Forms.ToolStripStatusLabel>控制項會取代及新增功能<xref:System.Windows.Forms.StatusBar>並<xref:System.Windows.Forms.StatusBarPanel>控制項，不過，<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項保留回溯相容性和未來使用，如果您選擇。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.ProgressBar>
- [ProgressBar 控制項](progressbar-control-windows-forms.md)
