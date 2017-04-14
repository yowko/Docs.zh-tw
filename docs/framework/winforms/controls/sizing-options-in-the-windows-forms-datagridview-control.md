---
title: "Windows Form DataGridView 控制項中的調整大小選項 | Microsoft Docs"
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
  - "資料格, 調整資料行大小"
  - "資料格, 調整資料列大小"
  - "資料格, 調整大小選項"
  - "DataGridView 控制項 [Windows Form], 調整資料行大小"
  - "DataGridView 控制項 [Windows Form], 調整資料列大小"
  - "DataGridView 控制項 [Windows Form], 調整大小選項"
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
caps.latest.revision: 29
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# Windows Form DataGridView 控制項中的調整大小選項
<xref:System.Windows.Forms.DataGridView> 的資料列、資料行和行首可以因不同事件而改變大小。  下列表格顯示了這些事件。  
  
|事件|描述|  
|--------|--------|  
|使用者調整大小|使用者可以透過拖曳滑鼠或按兩下資料列、資料行或行首分隔線來調整大小。|  
|控制項調整大小|在資料行填入模式中，資料行寬度會隨著控制項寬度變更；例如，當控制項停駐在其父表單內，而使用者重新調整表單的大小時。|  
|儲存格的值變更|在根據內容自動調整大小模式中，大小會依新的顯示值而變更。|  
|方法呼叫|以程式設計方式所做的內容架構大小調整可以讓您根據儲存格在方法被呼叫時的值，機動調整大小。|  
|屬性設定|您也可以設定特定的高度和寬度值。|  
  
 根據預設，使用者調整大小是啟用的，而自動調整是停用的，當儲存格值比資料行還要寬時則會被裁剪。  
  
 下列表格顯示了一些案例，在這些案例當中，您可以調整預設的行為，或使用特定的調整選項來達到特定的效果。  
  
|情節|實作|  
|--------|--------|  
|在相對少數的資料行佔用整個控制項的寬度，而且沒有顯示水平捲軸的情況下，使用資料行填入模式來顯示大小相近的資料。|將 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>。|  
|使用資料行填入模式來顯示大小不等的值。|將 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>。  設定資料行的 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 屬性，或將資料填入控制項之後，呼叫控制項的 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> 方法來初始化相對資料行寬度。|  
|使用資料行填入模式來顯示不同重要性的值。|將 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>。  為永遠必須顯示其部分資料的資料行設定比較大的 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 值，或在特定資料行使用填入模式以外的其他調整選項。|  
|使用資料行填入模式來避免顯示控制項背景。|在最後一個資料行將 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>，在其他資料行使用其他調整選項。  如果其他資料行使用太多可用的空間，請設定最後一個資料行的 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 屬性。|  
|顯示固定寬度的資料行，例如圖示或者 ID 資料行。|將資料行的 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>，並將 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> 設定為 <xref:System.Windows.Forms.DataGridViewTriState>。  設定資料行的 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> 屬性，或將資料填入控制項之後，呼叫控制項的 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> 方法來初始化資料行寬度。|  
|每當儲存格內容變更時，自動調整大小以防止裁剪發生，並且將空間使用最佳化。|將自動調整大小屬性設定為代表內容架構調整模式的值。  若要避免在處理大量資料時的效能損失，請使用只會計算要顯示之資料列的調整模式。|  
|調整大小以符合顯示的資料列中的值，避免在使用多個資料列時的效能損失。|以適當的調整模式列舉型別值來搭配自動調整大小或程式設計方式調整大小使用。  若要在捲動時調整大小以符合剛顯示的資料列中的值，請呼叫 <xref:System.Windows.Forms.DataGridView.Scroll> 事件處理常式中的調整大小方法。  若要自訂使用者按兩下的調整大小方法，只讓已顯示的資料列當中的值決定新大小，請呼叫 <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> 或 <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> 事件處理常式中的調整大小方法。|  
|只有在特定時間才調整大小以符合儲存格內容，以避免效能損失或啟用使用者調整大小。|在事件處理常式中呼叫一個內容架構的調整大小方法。  例如，使用 <xref:System.Windows.Forms.DataGridView.DataBindingComplete> 事件在繫結後初始化大小，並處理 <xref:System.Windows.Forms.DataGridView.CellValidated> 或 <xref:System.Windows.Forms.DataGridView.CellValueChanged> 事件，以根據使用者在繫結之資料來源的編輯或變更來調整大小。|  
|為多行的儲存格內容調整資料列高度。|確定資料行的寬度足以顯示文字段落，再使用自動或程式設計方式的內容架構資料列調整來調整高度。  您同時也要確定在顯示具有多行內容的儲存格時，其 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> 儲存格樣式值設定為 <xref:System.Windows.Forms.DataGridViewTriState>。<br /><br /> 通常，您將會使用自動資料行調整模式來維持資料行的寬度，或者在調整資料列高度之前，先將資料行設定為指定寬度。|  
  
## 使用滑鼠調整大小  
 根據預設，只要資料列、資料行和行首不是使用根據儲存格值自動調整的模式，使用者就可以調整其大小。  若要避免使用者在其他模式中 \(例如資料行填入模式\) 調整大小，請設定一或多個下列 <xref:System.Windows.Forms.DataGridView> 屬性：  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 您也可以設定資料列或資料行的 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 屬性，避免使用者調整個別資料列或資料行的大小。  根據預設，<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 屬性值是依照資料行的 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> 屬性值和資料列的 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> 屬性值來決定。  如果您明確地將 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 設定為 <xref:System.Windows.Forms.DataGridViewTriState> 或 <xref:System.Windows.Forms.DataGridViewTriState>，則這個指定值會覆寫控制項中資料列或資料行的屬性值。  將 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 設定為 <xref:System.Windows.Forms.DataGridViewTriState> 可以還原其繼承。  
  
 因為 <xref:System.Windows.Forms.DataGridViewTriState> 還原了繼承值，除非資料列或資料行尚未加入至 <xref:System.Windows.Forms.DataGridView> 控制項，否則 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 屬性將永遠不會傳回 <xref:System.Windows.Forms.DataGridViewTriState> 值。  如果您必須判斷資料列或資料行的 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 屬性值是否為繼承而來，請檢查其 <xref:System.Windows.Forms.DataGridViewElement.State%2A> 屬性。  如果 <xref:System.Windows.Forms.DataGridViewElement.State%2A> 值包含了 <xref:System.Windows.Forms.DataGridViewElementStates> 旗標，則 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 屬性值就不是從繼承而來。  
  
## 自動調整大小  
 在 <xref:System.Windows.Forms.DataGridView> 控制項中有兩種自動調整：資料行填入模式和內容架構的自動調整。  
  
 資料行填入模式會以控制項中看得見的資料行來填滿控制項顯示區域的寬度。  如需此模式的詳細資訊，請參閱[在 Windows Form DataGridView 控制項中的資料行填入模式](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)。  
  
 您也可以設定資料列、資料行和行首，讓它們根據儲存格的內容來自動調整大小。  這種情況下，只要儲存格內容發生變更，大小就會隨之調整。  
  
> [!NOTE]
>  如果您使用虛擬模式在一個自訂資料快取中維護儲存格值，當使用者編輯儲存格值時就會發生自動調整，但是如果您是從 <xref:System.Windows.Forms.DataGridView.CellValuePushed> 事件處理常式之外更改快取的值，就不會發生自動調整。  這種情況下，可呼叫 <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> 方法，強制控制項更新儲存格顯示並套用目前的自動調整模式。  
  
 如果內容架構的自動調整只在一個維度上啟用 \(只在資料列或只在資料行啟用\)，而且同時啟用了 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>，當另一個維度發生變更時，大小也會隨之調整。  例如，如果資料列設定了自動調整 \(資料行未設定\)，而且啟用了 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>，使用者可以拖曳資料行分隔線來變更資料行寬度，資料列高度會自動調整，儲存格內容還是可以完整顯示。  
  
 如果您在資料列和資料行都設定了內容架構的自動調整，而且啟用了 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>，當儲存格內容發生變更時，<xref:System.Windows.Forms.DataGridView> 控制項即會調整大小，並使用理想的儲存格長寬比來計算新的大小。  
  
 若要設定行首和資料列 \(以及未覆寫控制項值的資料行\) 的調整模式，請設定一或多個下列 <xref:System.Windows.Forms.DataGridView> 屬性：  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 若要覆寫控制項對某一個別資料行的資料行調整模式，請將其 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> 以外的值。  資料行的調整模式實際上是藉由其 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> 屬性來決定。  而這個屬性值則是根據資料行的 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 屬性值而來，除非該值為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>，在這種情況下，控制項的 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 值是從繼承而來。  
  
 當您在處理大量資料時，請謹慎使用內容架構的自動調整。  若要避免效能損失，請使用只會計算所顯示資料列大小的自動調整模式，不要對控制項中的每個資料列進行分析。  若要達到最佳效能，請改以程式設計方式來調整大小，這樣您可以在特定的時間調整大小，例如，在新資料載入後立刻進行。  
  
 如果您將資料列或資料行的 <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> 屬性，或是控制項的 <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> 或 <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> 屬性設定為 `false`，內容架構的自動調整模式並不會影響這些隱藏的資料列、資料行或行首。  例如，如果某一個資料行為了容納一個較大的儲存格值而自動調整大小，在這之後該資料行被隱藏；即使包含了較大儲存格值的資料列被刪除，這個隱藏的資料行並不會改變其大小。  自動調整不會因為可視性的變更而發生，因此，將資料行的 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> 屬性變更回 `true` 並不會強制它根據目前的內容重新計算大小。  
  
 以程式設計方式所做的內容架構大小調整會影響資料列、資料行和行首，而不論其可視性為何。  
  
## 以程式設計方式調整大小  
 當自動調整停用時，您可以藉由下列屬性，以程式設計方式來設定資料列、資料行或行首確切的寬度或高度：  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=fullName>  
  
 您也可以使用下列方法，以程式設計方式來調整資料列、資料行和行首的大小，以符合其內容：  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 這些方法會對資料列、資料行或行首進行一次調整大小，而不會把它們調整為持續改變大小。  新的大小會自動計算，以在不裁剪的情況下顯示所有儲存格內容。  但是，當您要以程式設計方式調整其 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> 屬性值為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> 的資料行時，計算所得出的內容架構寬度會用來依比例調整資料行的 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 屬性值，實際的資料行寬度則會根據這些新比例來計算，以使所有資料行填滿控制項中可用的顯示區域。  
  
 以程式設計方式調整大小可有效避免持續調整大小所造成的效能損失。  您也可以用它來為使用者可調整大小的資料列、資料行和行首，以及為資料行填入模式提供初始的大小。  
  
 通常您會在特定時間呼叫程式設計方式的調整大小方法。  例如，您可能想在資料載入後立刻以程式設計方式調整所有資料行的大小，或者，您可能會想在某個特定儲存格值修改後，以程式設計方式其資料列的大小。  
  
## 自訂內容架構的調整行為  
 在使用衍生的 <xref:System.Windows.Forms.DataGridView> 儲存格、資料列和資料行型別時，您可以自訂調整行為，做法是覆寫 <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=fullName>、<xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=fullName> 或 <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=fullName> 方法，或呼叫衍生的 <xref:System.Windows.Forms.DataGridView> 控制項中受保護的調整大小方法多載。  受保護的調整大小方法多載在設計上是成對運作，可以達到理想的儲存格長寬比，避免造成過寬或過高的儲存格。  例如，如果您呼叫了 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> 方法的 `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` 多載，並且傳入一個 `false` 值給 <xref:System.Boolean> 參數，這個多載會計算資料列中儲存格理想的高度和寬度，但是它只會調整資料列的高度。  您必須接著呼叫 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> 方法，以根據計算出的理想值調整資料行寬度。  
  
## 內容架構的調整選項  
 調整大小屬性和方法所使用的列舉型別，對於內容架構的調整都具有類似的值。  使用這些值，您就可以限制要以哪些儲存格來計算慣用大小。  在所有調整大小的列舉型別中，如果值是參考已顯示的儲存格之名稱，就會將計算限制在已顯示資料列的儲存格這個範圍當中。  當您必須處理大量資料列時，排除一些資料列可以避免效能損失。  您也可以將計算限制在行首的儲存格值，或非行首的儲存格當中。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>   
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>   
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>   
 [調整 Windows Form DataGridView 控制項中資料行和資料列的大小](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)   
 [在 Windows Form DataGridView 控制項中的資料行填入模式](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)   
 [如何：設定 Windows Form DataGridView 控制項的縮放模式](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)