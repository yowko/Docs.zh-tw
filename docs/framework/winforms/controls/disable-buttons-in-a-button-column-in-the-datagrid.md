---
title: "如何：停用 Windows Form DataGridView 控制項按鈕資料行中的按鈕 | Microsoft Docs"
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
  - "按鈕, 在按鈕資料行中停用"
  - "資料格, 停用按鈕"
  - "DataGridView 控制項 [Windows Form], 停用按鈕儲存格"
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：停用 Windows Form DataGridView 控制項按鈕資料行中的按鈕
<xref:System.Windows.Forms.DataGridView> 控制項包含 <xref:System.Windows.Forms.DataGridViewButtonCell> 類別，可使用按鈕等使用者介面 \(UI\) 來顯示儲存格。  但是，<xref:System.Windows.Forms.DataGridViewButtonCell> 未提供任何方法，來停用儲存格所顯示的按鈕外觀。  
  
 下列程式碼範例示範如何自訂 <xref:System.Windows.Forms.DataGridViewButtonCell> 類別，來顯示可呈現為停用狀態的按鈕。  這個範例會定義新的儲存格類型 `DataGridViewDisableButtonCell`，這個類型衍生自 <xref:System.Windows.Forms.DataGridViewButtonCell>。  這個儲存格類型提供了新的 `Enabled` 屬性，可設定為 `false`，以便在儲存格中繪製停用的按鈕。  這個範例也會定義新的資料行類型 `DataGridViewDisableButtonColumn`，以顯示 `DataGridViewDisableButtonCell` 物件。  為了示範這個新的儲存格和資料行類型，在父 <xref:System.Windows.Forms.DataGridView> 中每個 <xref:System.Windows.Forms.DataGridViewCheckBoxCell> 的目前值會決定同一個資料列中 `DataGridViewDisableButtonCell` 的 `Enabled` 屬性是 `true` 或 `false`。  
  
> [!NOTE]
>  當您從 <xref:System.Windows.Forms.DataGridViewCell> 或 <xref:System.Windows.Forms.DataGridViewColumn> 衍生並將新屬性加入衍生類別時，請務必覆寫 `Clone` 方法，以便於複製作業期間複製新屬性。  您也應該呼叫基底類別的 `Clone` 方法，以便將基底類別的屬性複製到新的儲存格或資料行。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing、System.Windows.Forms 和 System.Windows.Forms.VisualStyles 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## 請參閱  
 [自訂 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)   
 [DataGridView 控制項架構](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)   
 [Windows Form DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)