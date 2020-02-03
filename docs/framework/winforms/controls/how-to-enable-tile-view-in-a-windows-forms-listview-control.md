---
title: 在 ListView 控制項中啟用並排顯示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: 8ccbd42d870e44fc6fd80169327922409ea4f6e7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745473"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>如何：在 Windows Form ListView 控制項中啟用並排顯示
使用的 <xref:System.Windows.Forms.ListView> 控制項的並排顯示檢視功能，您可以提供圖形和文字資訊之間的視覺化平衡。 並排顯示檢視中針對項目顯示的文字資訊與詳細資料檢視所定義的資料行資訊相同。 並排顯示檢視與 <xref:System.Windows.Forms.ListView> 控制項中的群組或插入標記功能相配合。  
  
 並排顯示檢視會使用 32 x 32 像素圖示和數行的文字，如下列影像所示。  
  
 ![在 ListView 控制項中並排顯示](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "並排顯示的圖示和文字")  
 
 若要啟用並排顯示檢視，請將 <xref:System.Windows.Forms.ListView.View%2A> 屬性設定為 <xref:System.Windows.Forms.View.Tile>。 您可以藉由設定 <xref:System.Windows.Forms.ListView.TileSize%2A> 屬性調整並排顯示的大小，並藉由調整 <xref:System.Windows.Forms.ListView.Columns%2A> 集合來調整並排顯示中顯示的文字行數。  
  
### <a name="to-set-tile-view-programmatically"></a>以程式設計方式設定並排顯示檢視  
  
1. 使用 <xref:System.Windows.Forms.View> 控制項的 <xref:System.Windows.Forms.ListView> 的列舉。  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>範例  
 下列完整的程式碼範例示範並排顯示檢視，並修改為可顯示三行文字。 已經調整並排顯示大小以避免自動換行。  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System 和 System.Windows.Forms 組件的參考。  
  
- 名為 book.ico 的圖示檔，位於與可執行檔相同的目錄中。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView 控制項](listview-control-windows-forms.md)
- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
