---
title: "資料繫結和 Windows Form | Microsoft Docs"
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
  - "繫結控制項, Windows Form"
  - "資料 [Windows Form], 複雜資料繫結"
  - "資料 [Windows Form], 資料繫結"
  - "資料 [Windows Form], 簡單資料繫結"
  - "資料繫結, Windows Form"
  - "資料繫結控制項, Windows Form"
  - "查閱資料表, 資料繫結"
  - "主從式清單"
  - "報表, Windows Form"
  - "Windows Form 控制項, 資料繫結"
ms.assetid: 419aac5e-819b-4aad-88b0-73a2f8c0bd27
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 資料繫結和 Windows Form
在 Windows Forms 中，您不只可以繫結至傳統的資料來源，也能繫結至幾乎任何包含資料的結構。  您可以繫結至執行階段計算、從檔案讀取，或衍生自其他控制項之值的值陣列。  
  
 此外，您也可以將任何控制項的任何屬性繫結至資料來源。  在傳統資料繫結中，您通常將顯示屬性 — 例如 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性 — 繫結到資料來源。  使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]，您也可以選擇透過繫結設定其他屬性。  您可以使用繫結來執行下列工作：  
  
-   設定影像控制項的圖形。  
  
-   設定一或多個控制項的背景色彩。  
  
-   設定控制項的大小。  
  
 基本上，資料繫結是在表單上自動設定任何控制項的任何執行階段可存取屬性的方法。  
  
## 資料繫結的類型  
 Windows Forms 可以利用兩種類型的資料繫結：簡單繫結和複雜繫結。  各有不同的優點。  
  
|資料繫結的類型|描述|  
|-------------|--------|  
|簡單資料繫結|控制項繫結至單一資料項目的能力，例如資料集中資料表的資料行值。  這是一般適用於例如 <xref:System.Windows.Forms.TextBox> 控制項或 <xref:System.Windows.Forms.Label> 控制項等控制項的繫結類型，這些控制項通常只會顯示單一值。  事實上，控制項上的任何屬性都可以繫結至資料庫中的欄位。  在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中對這項功能有廣泛的支援。<br /><br /> 如需詳細資訊，請參閱：<br /><br /> -   [與資料繫結相關的介面](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)<br />-   [如何：巡覽 Windows Form 中的資料](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)<br />-   [如何：在 Windows Form 上建立簡單繫結控制項](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)|  
|複雜資料繫結|控制項繫結至一個以上資料項目的能力，在資料庫中通常會超過一筆記錄。  複雜繫結也稱為清單架構繫結。  支援複雜繫結的控制項範例有 <xref:System.Windows.Forms.DataGridView>、<xref:System.Windows.Forms.ListBox> 和 <xref:System.Windows.Forms.ComboBox> 控制項。  如需複雜資料繫結的範例，請參閱 [如何：將 Windows Form ComboBox 或 ListBox 控制項繫結至資料](../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)。|  
  
## BindingSource 元件  
 為了簡化資料繫結，Windows Forms 可讓您將資料來源繫結至 <xref:System.Windows.Forms.BindingSource> 元件，然後將控制項繫結至 <xref:System.Windows.Forms.BindingSource>。  您可以在簡單或複雜繫結案例中使用 <xref:System.Windows.Forms.BindingSource>。  在任一種情況下，<xref:System.Windows.Forms.BindingSource> 擔任了資料來源與繫結控制項之間的媒介，提供變更通知流通管理和其他服務。  
  
## 使用資料繫結的常見案例  
 幾乎所有商業應用程式都使用讀取自某種資料來源的資訊，通常是透過資料繫結。  下列清單顯示一些最常見的案例，利用資料繫結作為資料展示和管理的方法。  
  
|情節|描述|  
|--------|--------|  
|Reporting|報表會提供有彈性的方式，以在書面文件中顯示和彙總資料。  建立報表，將選取的資料來源內容列印至螢幕或印表機，是很常見的作法。  常見的報表包含清單、發票和摘要。  項目通常會格式化成清單資料行，且將子項目組織在每個清單項目下，但您應該選擇最適合資料的版面配置。|  
|資料輸入|若要輸入大量相關資料，或提示使用者輸入資訊，常用的方式是透過資料輸入表單。  使用者可以輸入資訊，或使用文字方塊、選項按鈕、下拉式清單和核取方塊來選取選項。  資訊便會送出並儲存在資料庫中，其結構是根據輸入的資訊。|  
|主從式關係|主從式應用程式是查看相關資料的一種格式。  明確地說，有兩個具有相連關係的資料表 — 在一般的商業範例中，「客戶」資料表和「訂單」資料表，它們之間連結了客戶和個別訂單的關係。  如需有關建立主從式應用程式與兩個 Windows Forms <xref:System.Windows.Forms.DataGridView> 控制項的詳細資訊，請參閱 [如何：使用兩個 Windows Form DataGridView 控制項建立主從式表單](../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagrids.md)|  
|查閱資料表|另一個常見的資料展示\/管理案例是資料表查閱。  通常，在較大的資料顯示中，<xref:System.Windows.Forms.ComboBox> 控制項是用來顯示和管理資料。  關鍵在於 <xref:System.Windows.Forms.ComboBox> 控制項中顯示的資料與寫入資料庫的資料不同。  例如，如果您有 <xref:System.Windows.Forms.ComboBox> 控制項，顯示可從雜貨店取得的項目，您可能會想看到產品的名稱 \(麵包、牛奶、蛋\)。  不過，為了簡化資料庫中的資訊擷取以及資料庫的正規化，您可能會將特定訂單的特定項目資訊儲存為項目編號 \(\#501、\#603 等\)。  因此，表單上 <xref:System.Windows.Forms.ComboBox> 控制項中的雜貨項目的「易記名稱」，與訂單中出現的相關項目編號，兩者之間有隱含的連接。  這是資料表查閱的本質。  如需詳細資訊，請參閱[如何：使用 Windows Form BindingSource 元件建立查閱資料表](../../../docs/framework/winforms/controls/how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component.md)。|  
  
## 請參閱  
 <xref:System.Windows.Forms.Binding>   
 [Windows Form 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [如何：將 Windows Form DataGrid 控制項繫結至資料來源](../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)   
 [BindingSource 元件](../../../docs/framework/winforms/controls/bindingsource-component.md)