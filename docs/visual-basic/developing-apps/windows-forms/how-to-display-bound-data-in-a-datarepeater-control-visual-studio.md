---
title: "如何︰ 在 DataRepeater 控制項 (Visual Studio) 中顯示繫結的資料 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9bf8f2f5fcc4dfa2b29e368a4e26bf112e08149e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a>如何：在 DataRepeater 控制項中顯示繫結資料 (Visual Studio)
最常見的使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項是以顯示來自資料庫或其他資料來源繫結的資料。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
 除了繫結控制項，您可能想要加入其他控制項，例如靜態標籤或映像中的每個項目重複<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 如需詳細資訊，請參閱[How to︰ 在 DataRepeater 控制項中顯示未繫結控制項](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)。  
  
 您也可以繫結至資料來源在執行階段藉由設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>屬性`True`並指派至資料來源<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A>屬性。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> 在此情況下，您必須管理與資料來源的所有互動。 如需詳細資訊，請參閱[DataRepeater 控制項中的虛擬模式](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a>若要建立資料繫結 DataRepeater  
  
1.  拖放到<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項從**Visual Basic PowerPacks**索引標籤中**工具箱**到表單或容器控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  拖曳調整大小和位置控點大小和控制項的位置。  
  
     請注意控制項有兩個矩形區域。 上方區域是*項目範本*; 將重複控制項加入到範本中的每個項目中<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項在執行階段。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 較低的區域是*檢視區*，其中會顯示的項目。  
  
     您也可以大小和放置控制項或項目範本，藉由變更**大小**和**位置**[屬性] 視窗中的屬性。  
  
3.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
    > [!NOTE]
    >  如果**資料來源**視窗是空的加入資料來源。 如需詳細資訊，請參閱[加入新的資料來源](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources)。  
  
4.  在**資料來源** 視窗中，選取包含您想要繫結的資料之資料表的最上層節點。  
  
5.  變更資料表的卸除類型`Details`按一下`Details`資料表節點的下拉式清單中。  
  
6.  選取 [資料表] 節點，然後拖曳的項目範本區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
     您可以指定每個欄位會顯示哪些類型的控制項。 如需詳細資訊，請參閱[設定要從資料來源視窗拖曳時要建立的控制項](https://docs.microsoft.com/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [如何︰ 顯示未繫結 DataRepeater 控制項中的控制項](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [如何︰ 使用兩個 DataRepeater 控制項 (Visual Studio) 建立主從式表單](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [如何︰ 變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
