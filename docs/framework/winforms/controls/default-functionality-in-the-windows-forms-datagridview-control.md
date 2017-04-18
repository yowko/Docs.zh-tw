---
title: "Windows Form DataGridView 控制項的預設功能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "資料格, DataGridView 控制項中的預設功能"
  - "DataGridView 控制項 [Windows Form], 預設功能"
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Windows Form DataGridView 控制項的預設功能
Windows Form <xref:System.Windows.Forms.DataGridView> 控制項為使用者提供了相當多的預設功能。  
  
## 預設功能  
 根據預設，<xref:System.Windows.Forms.DataGridView> 控制項：  
  
-   會自動顯示資料行行首和資料列行首，當表格垂直捲動時仍然可見。  
  
-   具有資料列行首，其中包含目前資料列的選取範圍指示器。  
  
-   在第一個儲存格具有選取矩形。  
  
-   具有使用者按兩下資料行分割線就可以自動調整大小的資料行。  
  
-   從應用程式的 `Main` 方法呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法時，會自動支援 Windows XP 和 Windows Server 2003 系列的視覺化樣式。  
  
 此外，<xref:System.Windows.Forms.DataGridView> 控制項的內容預設為可以編輯：  
  
-   如果使用者在儲存格內按兩下或按 F2，這個控制項就會自動將儲存格變成編輯模式，並且隨著使用者輸入自動更新儲存格的內容。  
  
-   如果使用者捲動到方格的結尾，將會看到用來加入新資料錄的資料列。  當使用者按一下這個資料列時，就會在 <xref:System.Windows.Forms.DataGridView> 控制項中加入含有預設值的新資料列。  當使用者按 ESC 鍵時，這個新資料列就會消失。  
  
-   如果使用者按一下資料列行首，會選取整個資料列。  
  
 當您設定 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性，將控制項繫結至資料來源時，控制項會：  
  
-   自動使用資料來源的資料行名稱做為資料行行首的文字。  
  
-   填入資料來源的內容。  並自動建立資料來源中每個資料行的 <xref:System.Windows.Forms.DataGridView> 資料行。  
  
-   為資料表中每個可見的資料列建立資料列。  
  
-   當使用者按一下資料行行首時，會根據基礎資料自動排序資料列。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)