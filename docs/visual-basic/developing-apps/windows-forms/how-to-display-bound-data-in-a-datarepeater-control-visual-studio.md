---
title: "How to: Display Bound Data in a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, data-binding"
  - "DataRepeater, displaying bound controls"
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Display Bound Data in a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項最常見的用途就是顯示資料庫或其他資料來源的繫結資料。  
  
 但是除了繫結控制項之外，您可能還想要加入其他控制項，例如在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中每個項目上重複出現的靜態 \(Static\) 標籤或影像。  如需詳細資訊，請參閱 [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)。  
  
 您也可以藉由將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> 屬性設定為 `True`，並將資料來源指派給 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> 屬性，以在執行階段繫結至資料來源。  在這種情況下，您需要管理與資料來源的所有互動。  如需詳細資訊，請參閱 [Virtual Mode in the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### 若要建立資料繫結 DataRepeater  
  
1.  將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項從 \[**工具箱**\] 裡的 \[**Visual Basic PowerPacks**\] 索引標籤拖曳至表單或容器控制項。  
  
2.  拖曳縮放控點 \(Sizing Handle\) 和位置控點，以調整控制項的大小和位置。  
  
     請注意，控制項具有兩個矩形區域。  上方區域為「*項目樣板*」\(Item Template\)，只要是加入至這個樣板的控制項，都會在執行階段重複出現在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的每個項目中。  下方區域為「*檢視區*」\(Viewport\)，是項目的顯示位置。  
  
     您也可以在 \[屬性\] 視窗中變更 \[**Size**\] 和 \[**Position**\] 屬性，以調整控制項或項目樣板的大小及位置。  
  
3.  按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]。  
  
    > [!NOTE]
    >  如果 \[**資料來源**\] 視窗是空的，請加入資料來源。  如需詳細資訊，請參閱[資料來源概觀](/visual-studio/data-tools/add-new-data-sources)。  
  
4.  在 \[**資料來源**\] 視窗中，選取含有所要繫結資料之資料表的最上層節點。  
  
5.  在資料表節點上，按一下下拉式清單中的 \[`Details`\]，將資料表的卸除型別變更為 \[`Details`\]。  
  
6.  選取該資料表節點，並將它拖曳到 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的項目樣板區域上。  
  
     您可以指定每個欄位所顯示的控制項型別。  如需詳細資訊，請參閱 [設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [How to: Change the Appearance of a DataRepeater Control](../Topic/How%20to:%20Change%20the%20Appearance%20of%20a%20DataRepeater%20Control%20\(Visual%20Studio\).md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)