---
title: "如何：使用設計工具在 Windows Form ListView 控制項中啟用 Tile 檢視"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72fc1212e6e154cf3459d9ae6b94b6a8965fb151
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>如何：使用設計工具在 Windows Form ListView 控制項中啟用 Tile 檢視
並排顯示檢視功能<xref:System.Windows.Forms.ListView>控制項可讓您提供圖形和文字資訊之間的視覺化平衡。 並排顯示檢視中針對項目顯示的文字資訊與詳細資料檢視所定義的資料行資訊相同。 並排顯示檢視函式結合的群組或插入標記功能<xref:System.Windows.Forms.ListView>控制項。  
  
 並排顯示檢視會使用 32 x 32 圖示和數行文字，如下列影像所示。  
  
 ![ListView 控制項中並排顯示](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
  
 並排顯示檢視屬性和方法讓您指定哪些資料行欄位來顯示每個項目，以及共同控制的大小和並排顯示視窗中的所有項目的外觀。 為了清楚起見，在磚中的第一行一律是文字的項目的名稱;無法變更。  
  
 下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.ListView>控制項。 設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  並排顯示檢視是僅在您的應用程式呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法時適用於 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上。 在舊版作業系統中，任何與並排顯示檢視相關的程式碼都無效，而且 <xref:System.Windows.Forms.ListView> 控制項會顯示在大圖示檢視中。 如需詳細資訊，請參閱<xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>。  
>   
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-set-tile-view-in-the-designer"></a>在設計工具中設定並排顯示檢視  
  
1.  選取<xref:System.Windows.Forms.ListView>控制項在表單上的。  
  
2.  在**屬性**視窗中，選取<xref:System.Windows.Forms.ListView.View%2A>屬性，然後選擇 **磚**。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [Windows XP 功能和 Windows Forms 控制項](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
