---
title: 作法：使用設計工具在 Windows Forms ListView 控制項中啟用並排顯示
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 8a45a8a484bd373f53585b1b113a51e59b30fca2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040356"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>作法：使用設計工具在 Windows Forms ListView 控制項中啟用並排顯示
<xref:System.Windows.Forms.ListView>控制項的磚視圖功能可讓您在圖形和文字資訊之間提供視覺化平衡。 並排顯示檢視中針對項目顯示的文字資訊與詳細資料檢視所定義的資料行資訊相同。 並排顯示函式與<xref:System.Windows.Forms.ListView>控制項中的群組或插入標記功能組合。

 磚視圖使用 32 x 32 圖示和數行文字, 如下圖所示。

 ![ListView 控制項中的磚視圖](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "並排顯示圖示和文字")

 磚視圖屬性和方法可讓您指定要針對每個專案顯示的資料列欄位, 以及共同控制磚視圖視窗內所有專案的大小和外觀。 為了清楚起見, 磚中的第一行文字一律是專案的名稱;無法變更。

 下列程式需要具有包含<xref:System.Windows.Forms.ListView>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。

> [!NOTE]
> 並排顯示檢視是僅在您的應用程式呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法時適用於 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上。 在舊版作業系統中，任何與並排顯示檢視相關的程式碼都無效，而且 <xref:System.Windows.Forms.ListView> 控制項會顯示在大圖示檢視中。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>。

## <a name="to-set-tile-view-in-the-designer"></a>在設計工具中設定磚視圖

1. 在 Visual Studio 中, <xref:System.Windows.Forms.ListView>選取表單上的控制項。

2. 在 [**屬性**] 視窗中, <xref:System.Windows.Forms.ListView.View%2A>選取屬性, 然後選擇 [**磚**]。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
