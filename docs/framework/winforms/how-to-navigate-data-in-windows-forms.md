---
title: "如何：巡覽 Windows Form 中的資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "CurrencyManager 類別, 巡覽 Windows Form 資料"
  - "游標, 資料來源"
  - "資料 [Windows Form], 巡覽"
  - "資料來源, Windows Form"
  - "Windows Form, 巡覽"
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：巡覽 Windows Form 中的資料
在 Windows 應用程式中，巡覽資料錄最簡單的方法就是將一個 <xref:System.Windows.Forms.BindingSource> 元件繫結至資料來源，然後再將控制項繫結至 <xref:System.Windows.Forms.BindingSource>。  接著您就可以使用 <xref:System.Windows.Forms.BindingSource> 中內建的巡覽方法，例如 <xref:System.Windows.Forms.BindingSource.MoveNext%2A>、<xref:System.Windows.Forms.BindingSource.MoveLast%2A>、<xref:System.Windows.Forms.BindingSource.MovePrevious%2A> 和 <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>。  使用這些方法就可以適當調整 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.Position%2A> 和 <xref:System.Windows.Forms.BindingSource.Current%2A> 屬性。  您也設定 <xref:System.Windows.Forms.BindingSource.Position%2A> 屬性，將找到的項目設定為目前項目。  
  
### 若要遞增在資料來源中的位置  
  
1.  請將繫結資料的 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.Position%2A> 屬性設定至所要前往的資料錄位置。  下列範例會說明如何在 `nextButton` 按下時，使用 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 方法來遞增 <xref:System.Windows.Forms.BindingSource.Position%2A> 屬性。  <xref:System.Windows.Forms.BindingSource> 與 `Northwind` 資料集的 `Customers` 資料表相關聯。  
  
    > [!NOTE]
    >  將 <xref:System.Windows.Forms.BindingSource.Position%2A> 屬性值設定超出最前或最後記錄範圍之外，並不會導致錯誤，因為 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 不會允許您將值的位置設在資料清單的界限之外。  如果在您的應用程式中，必須知道是否超出最前或最後的資料記錄以外，請在程式中加入邏輯判斷來測試是否會超過資料項目計數。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### 若要檢查是否超過結尾或開頭  
  
1.  為 <xref:System.Windows.Forms.BindingSource.PositionChanged> 事件建立事件處理常式。  在處理常式中，您可以測試所建議的位置值是否超出實際資料項目計數以外。  
  
     以下範例說明如何測試是否已經達到資料的最後項目。  在範例中，如果到達最後一筆項目，則表單中的 \[**下一步**\] 按鈕即會停用。  
  
    > [!NOTE]
    >  請注意，當您在程式碼中變更所巡覽的清單時，應該要重新啟用 \[**下一步**\] 按鈕，使用者才能夠瀏覽新清單的整個範圍。  此外，請注意，您正在使用之特定 <xref:System.Windows.Forms.BindingSource> 的上述 <xref:System.Windows.Forms.BindingSource.PositionChanged> 事件必須與它的事件處理方法相關聯。  下列是處理 <xref:System.Windows.Forms.BindingSource.PositionChanged> 事件的方法範例：  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### 若要尋找項目並將其設定為目前項目  
  
1.  找出您想要設定為目前項目的資料錄。  如果您的資料來源已實作 <xref:System.ComponentModel.IBindingList>，使用 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.Find%2A> 方法，即可達到此目的。  例如 <xref:System.ComponentModel.BindingList%601> 和 <xref:System.Data.DataView> 就是資料來源實作 <xref:System.ComponentModel.IBindingList> 的範例。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## 請參閱  
 [Windows Form 支援的資料來源](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)   
 [Windows Form 資料繫結中的變更告知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)   
 [資料繫結和 Windows Form](../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [Windows Form 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)