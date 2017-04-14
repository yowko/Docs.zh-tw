---
title: "DataGridView 控制項案例 (Windows Form) | Microsoft Docs"
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
  - "資料 [Windows Form], 以表格式格式顯示"
  - "資料格, 關於資料格"
  - "DataGridView 控制項 [Windows Form], 案例"
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# DataGridView 控制項案例 (Windows Form)
透過 <xref:System.Windows.Forms.DataGridView> 控制項，您可以顯示各種資料來源的表格式資料。  為了使用簡便，您可以透過控制項直接手動填入 <xref:System.Windows.Forms.DataGridView> 並管理資料。  但是，您通常會將資料儲存在外部資料來源，並透過 <xref:System.Windows.Forms.BindingSource> 元件將控制項繫結至此元件。  
  
 本主題描述涉及 <xref:System.Windows.Forms.DataGridView> 控制項的一些常見案例。  
  
## 案例 1：顯示少量的資料  
 您不必為了在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示資料，而將資料儲存在外部資料來源。  如果您正在處理少量的資料，可以自行填入控制項並透過控制項管理資料。  這稱為*未繫結模式*。  如需詳細資訊，請參閱 [如何：建立未繫結的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)。  
  
### 案例重點  
  
-   在未繫結模式中，手動填入控制項。  
  
-   未繫結模式尤其適用於少量的唯讀資料。  
  
-   未繫結模式也適用於類似試算表或只有少部分填入的資料表。  
  
## 案例 2：檢視和更新儲存在外部資料來源的資料  
 您可以將 <xref:System.Windows.Forms.DataGridView> 控制項當做使用者介面 \(UI\) 使用，這樣使用者就可以透過它來存取保存在資料來源 \(例如資料庫資料表或商務物件的集合\) 中的資料。  如需詳細資訊，請參閱 [如何：將資料繫結至 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)。  
  
### 案例重點  
  
-   繫結模式可以讓您連接資料來源、根據資料來源的屬性或資料庫資料行自動產生資料行，以及自動填入控制項。  
  
-   繫結模式適用於使用者與資料互動頻繁的狀況。  它可以格式化資料以供顯示，並且可以將使用者指定的資料剖析為資料來源所預期的格式。  同時，可以偵測到資料輸入格式錯誤和資料庫條件約束 \(Constraint\) 錯誤，因此可以警告使用者以更正錯誤的儲存格。  
  
-   其他像是資料行排序、凍結和重新調整順序的功能，可以讓使用者以他們工作流程中最簡便的方式檢視資料。  
  
-   剪貼簿支援可以讓使用者將資料從應用程式中複製到其他應用程式中。  
  
## 案例 3：進階資料  
 如果您有標準資料繫結模式無法處理的特殊需求，您可以實作「*虛擬模式*」來管理控制項與資料間的互動。  實作虛擬模式表示實作一或多個事件處理常式，讓控制項在需要關於儲存格的資訊時要求資訊。  
  
 例如，如果您在處理大量的資料，您可能會想要實作虛擬模式以確保最佳的效率。  在維護與其他資料來源所擷取的資料行一起顯示的未繫結資料行的值時，虛擬模式也非常有用。  
  
 如需虛擬模式的詳細資訊，請參閱 [逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。  
  
### 案例重點  
  
-   虛擬模式適用於需要微調效能以顯示大量的資料時。  
  
## 案例 4：自動調整資料列和資料行  
 當您顯示定期更新的資料時，您可以自動調整資料列和資料行的大小，以確保可以看見所有的內容。  <xref:System.Windows.Forms.DataGridView> 控制項會提供幾個選項，讓您啟用或停用手動調整大小、在特定時間以程式設計的方式調整大小，以及在內容變更時自動調整大小。  如需詳細資訊，請參閱 [Windows Form DataGridView 控制項中的調整大小選項](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)。  
  
### 案例重點  
  
-   手動調整大小可以讓使用者調整儲存格的高度和寬度。  
  
-   自動調整大小可以讓您維持儲存格的大小，以免裁剪到儲存格的內容。  
  
-   以程式設計方式調整大小可以讓您在特定時間調整儲存格大小，以免持續自動調整大小會降低效能。  
  
## 案例 5：簡單自訂  
 <xref:System.Windows.Forms.DataGridView> 控制項提供許多方式，讓您更改它的基本外觀和行為。  如需詳細資訊，請參閱 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
### 案例重點  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle> 物件讓您為控制項的個別項目，在多個層級提供色彩、字型、格式和位置資訊。  
  
-   儲存格樣式可以進行分層並由多個項目共用，讓您可以重複使用程式碼。  
  
## 案例 6：進階自訂  
 <xref:System.Windows.Forms.DataGridView> 控制項提供許多方式，讓您自訂它的外觀和行為。  
  
### 案例重點  
  
-   您可以提供自己的儲存格繪製程式碼。  如需詳細資訊，請參閱 [如何：在 Windows Form DataGridView 控制項中自訂儲存格的外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)。  
  
-   您可以提供自己的資料列繪製程式碼。  例如，在使用合併多個資料行的內容建立資料列時，這就非常有用。  如需詳細資訊，請參閱 [如何：在 Windows Form DataGridView 控制項中自訂資料列的外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)。  
  
-   您可以實作自己的儲存格和資料行類別，以自訂儲存格外觀。  如需詳細資訊，請參閱 [如何：擴充儲存格和資料行的行為和外觀以自訂 Windows Form DataGridView 控制項中的儲存格和資料行](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)。  
  
-   您可以實作自己的儲存格和資料行類別，以裝載內建資料行型別所提供的控制項以外的控制項。  如需詳細資訊，請參閱 [如何：Windows Form DataGridView 儲存格中的主控制項](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 [DataGridView 控制項概觀](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)