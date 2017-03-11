---
title: "How to: Change the Appearance of a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, customizing"
  - "DataRepeater, changing run time appearance"
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# How to: Change the Appearance of a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

變更 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項外觀的方式有二，您可以在設計階段設定屬性，或在執行階段處理 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 事件。  
  
 選取控制項的項目樣板區段時，會在執行階段為各個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 重複您在設計階段設定的屬性。  只有在容器的一部分處於未涵蓋的狀態時 \(例如，若 <xref:System.Windows.Forms.Control.Padding%2A> 屬性設為大型值\)，<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項自身的外觀相關屬性才會在執行階段顯示。  
  
 在執行階段，外觀相關屬性可以根據條件進行設定。  例如在排程應用程式中，您可以變更項目的背景色彩，以便在項目過期時警告使用者。  在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 事件處理常式中，如果您在如 `If…Then` 等的條件陳述式 \(Statement\) 中設定屬性，則您也必須使用 `Else` 子句指定當條件不成立時的外觀。  
  
### 若要在設計階段變更外觀  
  
1.  在 \[Windows Form 設計工具\] 中，選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的項目樣板 \(上方\) 區域。  
  
2.  在 \[屬性\] 視窗中，選取屬性並變更其值。  一般會影響外觀的屬性有 <xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.BackgroundImage%2A>、<xref:System.Windows.Forms.Panel.BorderStyle%2A> 和 <xref:System.Windows.Forms.Control.ForeColor%2A>。  
  
### 若要在執行階段變更外觀  
  
1.  在 \[程式碼編輯器\] 中，按一下 \[事件\] 下拉式清單中的 \[**DrawItem**\]。  
  
2.  在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 事件處理常式中，加入程式碼來設定屬性：  
  
     [!code-cs[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterAppearanceCS/VbPowerPacksDataRepeaterAppearance.cs#1)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterAppearance/VbPowerPacksDataRepeaterAppearance.vb#1)]  
  
## 範例  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的某些常用自訂包括以替代色彩的方式顯示資料列，以及根據條件變更欄位的色彩。  下列範例顯示如何執行這些自訂工作。  這個範例假設您有一個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項，而且這個控制項已繫結到 Northwind 資料庫中的 Products 資料表。  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterAlternateBackColor/AlternateBackColor.vb#1)]
 [!code-cs[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPwrPacksDataRepeaterAltBColorCS/AlternateBackColor.cs#1)]  
  
 請注意，針對這兩種自訂，您必須提供程式碼，以便設定正、反條件的屬性。  如果不指定 `Else` 條件，則在執行階段將看到意外的結果。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)