---
title: "如何： 使用兩個 DataRepeater 控制項 (Visual Studio) 建立主從式表單"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02f98cce74f99d8a00bc916b38e5c290045926a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>如何：使用兩個 DataRepeater 控制項建立主從式表單 (Visual Studio)
您可以使用兩個或多個顯示相關的資料<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項建立主從式表單。 比方說，您可以在其中一個顯示客戶清單<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>，當使用者選取的客戶，顯示該客戶的訂單清單的第二個和<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
 您可以顯示相關的資料的詳細資料的項目共用相同的主資料表節點，從**資料來源**視窗拖曳至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 比方說，如果您有具有 Customers 資料表和相關的 Orders 資料表的資料來源，您看到這兩個資料表中的樹狀檢視中的最上層節點**資料來源**視窗。 展開 Customers 節點，您可以看到資料行。 請注意，在清單中的最後一欄可展開的節點代表 「 訂單 」 資料表。 此節點代表客戶相關的訂單。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>若要在兩個 DataRepeater 控制項中顯示相關的資料  
  
1.  拖放兩<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制從**Visual Basic PowerPacks**索引標籤中**工具箱**到表單或容器控制項。  
  
2.  拖曳調整大小和位置控點，控制項的大小和位置來並行。  
  
3.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
    > [!NOTE]
    >  如果**資料來源**視窗是空的加入資料來源。 如需詳細資訊，請參閱[新增資料來源](/visualstudio/data-tools/add-new-data-sources)。  
  
4.  在**資料來源**視窗中，選取主要資料表中的最上層節點。  
  
5.  主要資料表的卸除類型變更為詳細資料，依序按一下**詳細資料**資料表節點上的下拉式清單中。  
  
6.  主要資料表節點拖曳至第一個項目範本區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
7.  展開主要資料表節點，然後選取相關資料表的詳細資料節點。  
  
8.  詳細資料表的卸除類型變更為詳細資料，依序按一下**詳細資料**資料表節點上的下拉式清單中。  
  
9. 選取這個資料表節點，然後將它拖曳至第二個項目範本區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [操作說明：在 DataRepeater 控制項中顯示繫結資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [如何：在 Windows Forms 應用程式中顯示相關的資料](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)  
 [操作說明：變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
