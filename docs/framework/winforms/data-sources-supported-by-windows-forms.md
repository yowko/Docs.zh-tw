---
title: Windows Form 支援的資料來源
ms.date: 03/30/2017
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
ms.openlocfilehash: b648d62c9128f0864d60ace1ca56700f594b78c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967085"
---
# <a name="data-sources-supported-by-windows-forms"></a>Windows Form 支援的資料來源
傳統上，資料繫結已使用的應用程式中利用儲存在資料庫中的資料。 使用 Windows Form 資料繫結，您可以從資料庫，以及其他的結構，例如陣列和集合中的資料存取資料，只要已符合特定最低需求。  
  
## <a name="structures-to-bind-to"></a>要繫結至結構  
 在 Windows Forms 中，您可以繫結至各種不同的結構，從簡單到複雜的清單，例如 ADO.NET 資料資料表 （複雜繫結） 的物件 （簡單繫結）。 簡單繫結，Windows Forms 會支援簡單的物件上的公用屬性的繫結。 Windows Form 清單為基礎的繫結通常需要物件支援<xref:System.Collections.IList>介面或<xref:System.ComponentModel.IListSource>介面。 此外，如果您要透過繫結與<xref:System.Windows.Forms.BindingSource>元件，您可以繫結至支援的物件<xref:System.Collections.IEnumerable>介面。 如需有關資料繫結介面的詳細資訊，請參閱[相關的資料繫結介面](interfaces-related-to-data-binding.md)。  
  
 下列清單會顯示您可以在 Windows Form 中繫結至結構。  
  
 <xref:System.Windows.Forms.BindingSource>  
 A<xref:System.Windows.Forms.BindingSource>是最常見的 Windows Form 資料來源，做為資料來源和 Windows Form 控制項之間的 proxy。 一般<xref:System.Windows.Forms.BindingSource>使用模式是將您的控制項繫結<xref:System.Windows.Forms.BindingSource>，並繫結<xref:System.Windows.Forms.BindingSource>到資料來源 （例如，ADO.NET 資料的資料表或商務物件）。 <xref:System.Windows.Forms.BindingSource>提供服務，啟用並提升資料繫結支援層級。 比方說，Windows Forms 清單基礎控制項這類<xref:System.Windows.Forms.DataGridView>並<xref:System.Windows.Forms.ComboBox>不直接支援繫結至<xref:System.Collections.IEnumerable>zdroje dat 不過，您可以啟用此案例中的透過繫結<xref:System.Windows.Forms.BindingSource>。 在此情況下，<xref:System.Windows.Forms.BindingSource>將資料來源轉換成<xref:System.Collections.IList>。  
  
 簡單物件  
 Windows Form 支援公用屬性的資料繫結控制項屬性的物件使用的執行個體上<xref:System.Windows.Forms.Binding>型別。 Windows Form 也支援繫結清單控制項，例如<xref:System.Windows.Forms.ListControl>物件執行個體時<xref:System.Windows.Forms.BindingSource>用。  
  
 陣列或集合  
 若要做為資料來源，必須實作清單<xref:System.Collections.IList>介面; 一個範例是陣列，其中是的執行個體<xref:System.Array>類別。 如需有關陣列的詳細資訊，請參閱[How to:建立物件 (Visual Basic) 的陣列](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/487y7874(v=vs.100))。  
  
 一般情況下，您應該使用<xref:System.ComponentModel.BindingList%601>當您建立資料繫結的物件清單。 <xref:System.ComponentModel.BindingList%601> 是的泛型版本<xref:System.ComponentModel.IBindingList>介面。 <xref:System.ComponentModel.IBindingList>介面會擴充<xref:System.Collections.IList>藉由新增屬性、 方法和所需的雙向資料繫結事件的介面。  
  
 <xref:System.Collections.IEnumerable>  
 Windows Form 控制項可以繫結至資料來源僅支援<xref:System.Collections.IEnumerable>介面會透過繫結<xref:System.Windows.Forms.BindingSource>元件。  
  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 資料物件  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 提供一些適合繫結至資料結構。 每個會在其複雜度和複雜程度而有所不同。  
  
- <xref:System.Data.DataColumn>. A<xref:System.Data.DataColumn>是基本建置組塊的<xref:System.Data.DataTable>，依此資料行的數目所組成的資料表。 每個<xref:System.Data.DataColumn>具有<xref:System.Data.DataColumn.DataType%2A>決定的資料行保留 （例如，請描述 cars 資料表中的汽車） 的資料類型的屬性。 您可以簡單繫結控制項 (例如<xref:System.Windows.Forms.TextBox>控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性) 到資料表中的資料行。  
  
- <xref:System.Data.DataTable>. A<xref:System.Data.DataTable>資料表，且資料列和資料行，表示處於[!INCLUDE[vstecado](../../../includes/vstecado-md.md)]。 資料表包含兩個集合： <xref:System.Data.DataColumn>，代表在給定資料表中 （這會決定可輸入至該資料表的資料類型），資料行和<xref:System.Data.DataRow>，表示給定資料表中的資料列。 您可以複雜繫結控制項至資料表中所包含的資訊 (例如繫結<xref:System.Windows.Forms.DataGridView>至資料表的控制項)。 不過，當您繫結至<xref:System.Data.DataTable>，您會以真正的繫結至資料表的預設檢視。  
  
- <xref:System.Data.DataView>. A<xref:System.Data.DataView>是單一資料表的資料可能會篩選或排序的自訂的檢視。 資料檢視會是 「 快照集 」 複雜繫結控制項所使用的資料。 您可以簡單繫結或複雜繫結至的資料在資料檢視中，但請注意，您會繫結至固定 「 印象 」 資料，而不是全新的更新資料來源。  
  
- <xref:System.Data.DataSet>. A<xref:System.Data.DataSet>是資料表、 關聯性和條件約束的資料庫中資料的集合。 您可以簡單繫結或複雜繫結至資料集資料，但請注意，您要繫結預設值<xref:System.Data.DataViewManager>針對<xref:System.Data.DataSet>（請參閱下一步 的項目符號點）。  
  
- <xref:System.Data.DataViewManager>. A<xref:System.Data.DataViewManager>是自訂的檢視的整個<xref:System.Data.DataSet>，類似於<xref:System.Data.DataView>，但包含的關聯性。 具有<xref:System.Data.DataViewManager.DataViewSettings%2A>集合中，您可以設定預設篩選和排序選項的任何檢視，<xref:System.Data.DataViewManager>具有指定的資料表。  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 資料繫結中的變更告知](change-notification-in-windows-forms-data-binding.md)
- [資料繫結和 Windows Forms](data-binding-and-windows-forms.md)
- [Windows Forms 資料繫結](windows-forms-data-binding.md)
