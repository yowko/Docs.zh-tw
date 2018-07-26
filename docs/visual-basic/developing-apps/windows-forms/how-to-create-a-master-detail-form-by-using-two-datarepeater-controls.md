---
title: 如何： 利用兩個 DataRepeater 控制項 (Visual Studio) 來建立主從式表單
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
ms.openlocfilehash: 84639a5d49a3fa4a8c6845793c39fc8a67c31e02
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245522"
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>如何：使用兩個 DataRepeater 控制項建立主從式表單 (Visual Studio)
您可以使用兩個或多個顯示相關的資料<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項建立主從式表單。 比方說，您可能想要在其中顯示一份客戶<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>，並當使用者選取客戶時，會顯示該客戶的訂單清單的每秒<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
 您可以顯示相關的資料的詳細資料的項目共用相同的主資料表節點，從**資料來源**視窗拖曳至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 例如，如果您有具有 Customers 資料表和相關的 Orders 資料表的資料來源時，您看到這兩個資料表中的樹狀檢視中的最上層節點**Zdroje dat**視窗。 展開 [客戶] 節點，以便您可以看到資料行。 請注意，在清單中的最後一欄可展開的節點，表示 「 訂單 」 資料表。 這個節點代表客戶相關的訂單。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>若要在兩個 DataRepeater 控制項中顯示相關的資料  
  
1.  將兩個<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項從**Visual Basic PowerPacks**索引標籤**工具箱**到表單或容器控制項。  
  
2.  拖曳調整大小和位置控點來調整控制項的大小，然後放置在並排顯示。  
  
3.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
    > [!NOTE]
    >  如果**Zdroje dat**視窗是空的加入資料來源。 如需詳細資訊，請參閱[新增資料來源](/visualstudio/data-tools/add-new-data-sources)。  
  
4.  在 [ **Zdroje dat** ] 視窗中，選取主要資料表中的最上層節點。  
  
5.  卸除類型變更主要資料表的詳細資料，即可**詳細資料**資料表節點上的下拉式清單中。  
  
6.  在主要資料表節點拖曳至第一個項目範本區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
7.  展開 [主資料表] 節點，然後選取相關資料表的詳細資料節點。  
  
8.  將詳細資料表的卸除類型變更為詳細資料中，依序按一下**詳細資料**資料表節點上的下拉式清單中。  
  
9. 選取這個資料表節點，然後將它拖曳至第二個項目範本區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [操作說明：在 DataRepeater 控制項中顯示繫結資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [如何：在 Windows Forms 應用程式中顯示相關的資料](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [操作說明：變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
