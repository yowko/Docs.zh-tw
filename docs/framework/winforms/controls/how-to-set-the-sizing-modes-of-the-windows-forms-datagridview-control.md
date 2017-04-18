---
title: "如何：設定 Windows Form DataGridView 控制項的縮放模式 | Microsoft Docs"
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
  - "資料格, 設定調整大小模式"
  - "DataGridView 控制項 [Windows Form], 調整大小模式"
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：設定 Windows Form DataGridView 控制項的縮放模式
下列程序示範一些常見的情況，這些自訂或結合可用的調整大小選項以供 <xref:System.Windows.Forms.DataGridView> 控制項以及控制項中的特定資料行使用。  
  
### 建立固定寬度資料行  
  
-   將 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 屬性設為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> 、 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> 屬性設為 <xref:System.Windows.Forms.DataGridViewTriState> 、 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> 屬性設為 `true` 和 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> 屬性設為適當值。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### 建立會自動調整其大小以符合其內容的資料行  
  
-   將 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 屬性設定為以內容為基礎的大小調整模式。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### 建立不同的大小和重要性的值填滿模式資料行  
  
-   設定 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=fullName> 屬性為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>來為所有不會覆寫此值的資料行設定大小調整模式。  將資料行的 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 屬性，依照它們的平均內容寬度找出適當比例，做為設定值。  設定重要性資料行的 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 屬性，以確保會顯示部分內容。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## 範例  
 下列的完整程式碼範例提供示範用應用程式，可以協助您了解本主題中所述的大小調整選項。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 使用本示範應用程式：  
  
-   變更表單的大小  觀察填滿模式資料行在由 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 屬性值指定並保留比例時如何變更其寬度。  觀察資料行的 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 如何在表單太小時防止其變更。  
  
-   使用滑鼠拖曳資料行分隔線來變更資料行大小。  觀察某些資料行為何不能調整大小，以及可調整大小的資料行為何不能設定成比最小寬度還窄。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   本系統以及 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以將程式碼貼到新的專案裡，以便在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>   
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=fullName>