---
title: "How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio) | Microsoft Docs"
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
  - "DataRepeater, master/detail tables"
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您可以使用兩個 \(含\) 以上的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項建立主從式表單，藉以顯示相關資料。  例如，您可能想要在第一個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 中顯示客戶清單，而當使用者選取客戶時，在第二個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 中顯示客戶訂單清單。  
  
 您可以從 \[**資料來源**\] 視窗中把共用相同主資料表節點的詳細資料項目拖曳到 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項上，藉以顯示相關資料。  例如，如果資料來源有 Customers 資料表和相關的 Orders 資料表，則在 \[**資料來源**\] 視窗中，就會看到這兩個資料表在樹狀檢視中為最上層節點。  展開 Customers 節點即可看到資料行。  請注意，清單中的最後一個資料行是可展開的節點，此節點表示 Orders 資料表。  這個節點表示客戶的相關訂單。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### 若要在兩個 DataRepeater 控制項中顯示相關資料  
  
1.  從 \[**工具箱**\] 的 \[**Visual Basic PowerPacks**\] 索引標籤中，將兩個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項拖曳到表單或容器控制項。  
  
2.  拖曳縮放控點和位置控點以調整這兩個控制項的大小，並將它們左右並排。  
  
3.  按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]。  
  
    > [!NOTE]
    >  如果 \[**資料來源**\] 視窗是空的，請加入資料來源。  如需詳細資訊，請參閱[資料來源概觀](/visual-studio/data-tools/add-new-data-sources)。  
  
4.  在 \[**資料來源**\] 視窗中，選取主資料表的最上層節點。  
  
5.  在資料表節點上，按一下下拉式清單中的 \[**詳細資料**\]，將主資料表的卸除型別變更為 \[詳細資料\]。  
  
6.  將主資料表節點拖曳到第一個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的項目樣板區域上。  
  
7.  展開主資料表節點，並選取相關資料表的詳細資料節點。  
  
8.  在資料表節點上，按一下下拉式清單中的 \[**詳細資料**\]，將詳細資料表的卸除型別變更為 \[詳細資料\]。  
  
9. 選取這個資料表節點並將它拖曳到第二個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的項目樣板區域上。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [如何：在 Windows Form 應用程式中顯示相關的資料](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)   
 [How to: Change the Appearance of a DataRepeater Control](../Topic/How%20to:%20Change%20the%20Appearance%20of%20a%20DataRepeater%20Control%20\(Visual%20Studio\).md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)