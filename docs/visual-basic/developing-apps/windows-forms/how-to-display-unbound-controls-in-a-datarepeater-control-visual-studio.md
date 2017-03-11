---
title: "How to: Display Unbound Controls in a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, adding unbound controls"
  - "DataRepeater"
  - "displaying unbound data"
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# How to: Display Unbound Controls in a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

除了繫結控制項之外，您可能還想要將其他控制項加入至 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>，例如 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的每個項目上重複出現的靜態 \(Static\) 標籤或影像。  
  
> [!NOTE]
>  在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 上，您也必須至少有一個繫結控制項，否則在執行階段不會顯示任何項目。  
  
### 若要將未繫結控制項加入至 DataRepeater  
  
1.  將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項從 \[**工具箱**\] 裡的 \[**Visual Basic PowerPacks**\] 索引標籤拖曳至表單或容器控制項。  
  
2.  拖曳縮放控點 \(Sizing Handle\) 和位置控點，以調整控制項的大小和位置。  
  
     您也可以在 \[屬性\] 視窗中變更 \[**Size**\] 和 \[**Position**\] 屬性，以調整控制項的大小和位置。  
  
3.  將至少一個資料繫結控制項加入至 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項。  如需詳細資訊，請參閱 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)。  
  
4.  從 \[**工具箱**\] 將控制項拖曳到 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的項目樣板區域上。  
  
     請注意，控制項具有兩個矩形區域。  內部區域為「*項目樣板*」\(Item Template\)，加入至此樣板的控制項將會在執行階段重複出現在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的每個項目中。  外部區域為「*檢視區*」\(Viewport\)，將是顯示項目的位置，加入至這個區域的控制項將不會在執行階段顯示。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)