---
title: "Windows Form 支援的資料來源"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collections [Windows Forms], binding to
- OLE DB providers [Windows Forms], Windows Forms
- DataTable class [Windows Forms], binding and Windows Forms
- Windows Forms, data binding
- DataView class [Windows Forms], binding and Windows Forms
- DataViewManager class [Windows Forms], binding and Windows Forms
- Windows Forms, source data
- arrays [Windows Forms]
- data sources [Windows Forms]
- data providers [Windows Forms]
- DataSet class [Windows Forms], binding and Windows Forms
- data [Windows Forms], data providers
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a0a4c2bca136377b9c6812008189dae009e195f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="data-sources-supported-by-windows-forms"></a>Windows Form 支援的資料來源
傳統上，資料繫結已使用的應用程式中利用儲存在資料庫中的資料。 Windows Form 資料繫結，您可以從資料庫，以及其他結構，例如陣列和集合中的資料存取資料，只要符合特定最低需求。  
  
## <a name="structures-to-bind-to"></a>要繫結至結構  
 在 Windows Forms 中，您可以繫結至各種不同的結構，從簡單到複雜的清單，例如 ADO.NET 資料的資料表 （複雜繫結） 的物件 （簡單繫結）。 簡單繫結，Windows Form 支援簡單的物件上的公用屬性的繫結。 Windows Form 清單架構繫結通常需要物件支援<xref:System.Collections.IList>介面或<xref:System.ComponentModel.IListSource>介面。 此外，如果您透過繫結與<xref:System.Windows.Forms.BindingSource>元件，您可以繫結至支援的物件<xref:System.Collections.IEnumerable>介面。 如需資料繫結相關的介面的詳細資訊，請參閱[介面相關的資料繫結](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)。  
  
 下表將列出您可以在 Windows Form 中繫結至結構。  
  
 <xref:System.Windows.Forms.BindingSource>  
 A<xref:System.Windows.Forms.BindingSource>是最常見的 Windows Form 資料來源，做為資料來源與 Windows Form 控制項之間的 proxy。 一般<xref:System.Windows.Forms.BindingSource>繫結至控制項的使用模式<xref:System.Windows.Forms.BindingSource>並繫結<xref:System.Windows.Forms.BindingSource>到資料來源 （例如，ADO.NET 資料的資料表或商務物件）。 <xref:System.Windows.Forms.BindingSource>提供啟用和改善的繫結支援的資料層級的服務。 例如，Windows Form 清單基礎控制項例如<xref:System.Windows.Forms.DataGridView>和<xref:System.Windows.Forms.ComboBox>不直接支援繫結至<xref:System.Collections.IEnumerable>資料來源不過，您可以啟用此案例中的透過繫結<xref:System.Windows.Forms.BindingSource>。 在此情況下，<xref:System.Windows.Forms.BindingSource>將資料來源轉換成<xref:System.Collections.IList>。  
  
 簡單物件  
 Windows Form 支援的物件使用執行個體上的公用屬性的資料繫結控制屬性<xref:System.Windows.Forms.Binding>型別。 Windows Form 也支援基礎清單控制項繫結，例如<xref:System.Windows.Forms.ListControl>物件執行個體時<xref:System.Windows.Forms.BindingSource>用。  
  
 陣列或集合  
 若要做為資料來源，必須實作清單<xref:System.Collections.IList>介面; 其中一個範例是陣列，其中是的執行個體<xref:System.Array>類別。 如需陣列的詳細資訊，請參閱[How to： 建立陣列的物件 (Visual Basic)](http://msdn.microsoft.com/library/6b64e069-0387-400c-9081-3bdc581020c3)。  
  
 一般情況下，您應該使用<xref:System.ComponentModel.BindingList%601>當您建立資料繫結的物件清單。 <xref:System.ComponentModel.BindingList%601>泛型版本<xref:System.ComponentModel.IBindingList>介面。 <xref:System.ComponentModel.IBindingList>介面延伸<xref:System.Collections.IList>加屬性、 方法和所需的雙向資料繫結事件的介面。  
  
 <xref:System.Collections.IEnumerable>  
 Windows Form 控制項可以繫結至資料來源只支援<xref:System.Collections.IEnumerable>介面透過繫結<xref:System.Windows.Forms.BindingSource>元件。  
  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]資料物件  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]提供數個適用於繫結至資料結構。 在其複雜度和複雜程度上各有不同。  
  
-   <xref:System.Data.DataColumn>. A<xref:System.Data.DataColumn>是基本建置組塊<xref:System.Data.DataTable>，依此資料行的數字組成的資料表。 每個<xref:System.Data.DataColumn>具有<xref:System.Data.DataColumn.DataType%2A>屬性，可判斷資料行保留 （例如，請汽車描述 cars 資料表中） 的資料種類。 您可以簡單繫結控制項 (例如<xref:System.Windows.Forms.TextBox>控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性) 到資料表中的資料行。  
  
-   <xref:System.Data.DataTable>. A<xref:System.Data.DataTable>中是具有資料列和資料行的資料表，表示[!INCLUDE[vstecado](../../../includes/vstecado-md.md)]。 資料表包含兩個集合： <xref:System.Data.DataColumn>，代表在給定資料表中 （這會決定您可以輸入該資料表的資料類型），資料行和<xref:System.Data.DataRow>，表示給定資料表中的資料列。 您可以複雜繫結控制項至資料表中所包含的資訊 (例如繫結<xref:System.Windows.Forms.DataGridView>至資料表的控制項)。 不過，當您繫結至<xref:System.Data.DataTable>，您是真的繫結至資料表的預設檢視。  
  
-   <xref:System.Data.DataView>. A<xref:System.Data.DataView>是單一資料表的資料可能會被篩選或排序的自訂的檢視。 資料檢視會是 「 快照集 」 複雜繫結控制項所使用的資料。 您可以簡單繫結或複雜繫結至的資料在資料檢視中，但請注意，您會繫結至固定 「 圖片 」 的資料，而不是全新的更新資料來源。  
  
-   <xref:System.Data.DataSet>. A<xref:System.Data.DataSet>是資料表、 關聯性和條件約束的資料庫中資料的集合。 您可以簡單繫結或複雜繫結至資料集內的資料，但請注意，您要繫結預設值<xref:System.Data.DataViewManager>如<xref:System.Data.DataSet>（請參閱下一個點的項目符號）。  
  
-   <xref:System.Data.DataViewManager>. A<xref:System.Data.DataViewManager>是自訂的檢視，將整個<xref:System.Data.DataSet>，類似於<xref:System.Data.DataView>，但是使用包含的關聯。 與<xref:System.Data.DataViewManager.DataViewSettings%2A>集合，則您可以設定預設篩選和排序選項的任何檢視<xref:System.Data.DataViewManager>具有指定的資料表。  
  
## <a name="see-also"></a>請參閱  
 [Windows Forms 資料繫結中的變更告知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [資料繫結和 Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Windows Forms 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)
