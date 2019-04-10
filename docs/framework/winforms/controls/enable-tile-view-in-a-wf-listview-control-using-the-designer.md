---
title: HOW TO：使用設計工具在 Windows Forms ListView 控制項中啟用並排顯示
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: f8c8a1b2e3d2adfa7daadd609051ffc304150efe
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300589"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>HOW TO：使用設計工具在 Windows Forms ListView 控制項中啟用並排顯示
並排顯示檢視功能<xref:System.Windows.Forms.ListView>控制項可讓您提供圖形和文字資訊之間的視覺化平衡。 並排顯示檢視中針對項目顯示的文字資訊與詳細資料檢視所定義的資料行資訊相同。 並排顯示檢視函式搭配的群組 」 或 「 插入標記功能<xref:System.Windows.Forms.ListView>控制項。  
  
 並排顯示檢視會使用 32x32 圖示和數行文字，如下圖所示。  
  
 ![ListView 控制項中並排](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "圖格的圖示和文字")  
  
 並排顯示屬性和方法可讓您指定的資料行欄位，顯示針對每個項目，以及共同控制的大小和並排顯示檢視 視窗中的所有項目的外觀。 為了清楚起見，在圖格中的第一行一律是文字的項目的名稱;無法變更。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.ListView>控制項。 如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  並排顯示檢視是僅在您的應用程式呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法時適用於 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上。 在舊版作業系統中，任何與並排顯示檢視相關的程式碼都無效，而且 <xref:System.Windows.Forms.ListView> 控制項會顯示在大圖示檢視中。 如需詳細資訊，請參閱<xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>。  
>   
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-set-tile-view-in-the-designer"></a>若要在設計師中設定並排顯示檢視  
  
1. 選取<xref:System.Windows.Forms.ListView>您表單上的控制項。  
  
2. 在 **屬性**視窗中，選取<xref:System.Windows.Forms.ListView.View%2A>屬性，然後選擇**圖格**。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
