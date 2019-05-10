---
title: BindingSource 元件架構
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: 7300acdf46844dd79445859dfa47874889982bd1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593466"
---
# <a name="bindingsource-component-architecture"></a>BindingSource 元件架構
使用<xref:System.Windows.Forms.BindingSource>元件，都將資料來源所有的 Windows Form 控制項繫結。  
  
 <xref:System.Windows.Forms.BindingSource>元件簡化將控制項繫結至資料來源的程序，並提供下列優點勝過傳統的資料繫結：  
  
- 可讓設計階段繫結至商務物件。  
  
- 封裝<xref:System.Windows.Forms.CurrencyManager>功能並公開<xref:System.Windows.Forms.CurrencyManager>在設計階段的事件。  
  
- 可簡化建立清單支援<xref:System.ComponentModel.IBindingList>原本不支援清單中的資料來源變更通知，提供清單變更通知的介面。  
  
- 提供的擴充點<xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType>方法。  
  
- 提供資料來源和控制項之間的間接取值層的級。 資料來源可能會在執行階段變更時，則這種間接方式會相當重要。  
  
- 與其他資料相關的 Windows Form 控制項，特別是相互操作<xref:System.Windows.Forms.BindingNavigator>而<xref:System.Windows.Forms.DataGridView>控制項。  
  
 基於這些理由，<xref:System.Windows.Forms.BindingSource>元件是您的 Windows Forms 控制項繫結至資料來源的慣用的方法。  
  
## <a name="bindingsource-features"></a>BindingSource 功能  
 <xref:System.Windows.Forms.BindingSource>元件提供數個功能控制項繫結至資料。 使用這些功能，您可以實作幾乎任何程式碼在您的組件上的大部分資料繫結案例。  
  
 <xref:System.Windows.Forms.BindingSource>元件可完成此作業藉由提供一致的介面來存取許多不同種類的資料來源。 這表示，您會使用相同的程序繫結至任何類型。 例如，您可以將附加<xref:System.Windows.Forms.BindingSource.DataSource%2A>屬性設<xref:System.Data.DataSet>或商務物件，然後在這兩種情況您會使用同一組屬性、 方法和事件來操作資料來源。  
  
 提供的一致介面<xref:System.Windows.Forms.BindingSource>元件可大幅簡化資料繫結至控制項的程序。 資料來源類型，可提供變更通知，<xref:System.Windows.Forms.BindingSource>元件會自動進行通訊的控制項與資料來源之間的變更。 對於不提供變更通知的資料來源類型，事件會提供可讓您引發變更通知。 下列清單顯示所支援的功能<xref:System.Windows.Forms.BindingSource>元件：  
  
- 間接取值。  
  
- 貨幣的管理。  
  
- 為清單的資料來源。  
  
- <xref:System.Windows.Forms.BindingSource> 為<xref:System.ComponentModel.IBindingList>。  
  
- 建立自訂的項目。  
  
- 建立交易式的項目。  
  
- <xref:System.Collections.IEnumerable> 支援。  
  
- 設計階段支援。  
  
- 靜態<xref:System.Windows.Forms.ListBindingHelper>方法。  
  
- 排序和篩選與<xref:System.ComponentModel.IBindingListView>介面。  
  
- 與整合<xref:System.Windows.Forms.BindingNavigator>。  
  
### <a name="indirection"></a>間接  
 <xref:System.Windows.Forms.BindingSource>元件所提供的控制項和資料來源之間的間接取值層級。 而不是將控制項繫結至資料來源直接，您將控制項繫結至<xref:System.Windows.Forms.BindingSource>，並附加資料來源<xref:System.Windows.Forms.BindingSource>元件的<xref:System.Windows.Forms.BindingSource.DataSource%2A>屬性。  
  
 這個間接取值的層級，您可以變更資料來源，而不必重設的控制項繫結。 這可讓您下列功能：  
  
- 您可以將附加<xref:System.Windows.Forms.BindingSource>到不同的資料來源，同時保留目前的控制項繫結。  
  
- 您可以變更資料來源中的項目，並通知繫結的控制項。 如需詳細資訊，請參閱[如何：反映 Windows Form 控制項使用 BindingSource 中的資料來源更新](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)。  
  
- 您可以繫結至<xref:System.Type>而非在記憶體中的物件。 如需詳細資訊，請參閱[如何：將 Windows Forms 控制項繫結至型別](how-to-bind-a-windows-forms-control-to-a-type.md)。 您接著可以在執行階段繫結至物件。  
  
### <a name="currency-management"></a>貨幣管理  
 <xref:System.Windows.Forms.BindingSource>元件實作<xref:System.Windows.Forms.ICurrencyManagerProvider>来處理貨幣管理，以便您的介面。 具有<xref:System.Windows.Forms.ICurrencyManagerProvider>介面，您也可以存取到 currency 管理員<xref:System.Windows.Forms.BindingSource>，另一個的 currency 管理員除了<xref:System.Windows.Forms.BindingSource>繫結至相同<xref:System.Windows.Forms.BindingSource.DataMember%2A>。  
  
 <xref:System.Windows.Forms.BindingSource>元件會封裝<xref:System.Windows.Forms.CurrencyManager>功能，並會公開最常見<xref:System.Windows.Forms.CurrencyManager>屬性和事件。 下表說明一些與貨幣管理相關的成員。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> 屬性  
 取得相關聯的 currency 管理員<xref:System.Windows.Forms.BindingSource>。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A> 方法  
 如果有另一個<xref:System.Windows.Forms.BindingSource>繫結至指定的資料成員，則會取得其 currency 管理員。  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A> 屬性  
 取得資料來源的目前項目。  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A> 屬性  
 取得或設定基礎清單中的目前位置。  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 方法  
 將暫止的變更套用至基礎資料來源。  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> 方法  
 取消目前的編輯作業。  
  
### <a name="data-source-as-a-list"></a>為清單的資料來源  
 <xref:System.Windows.Forms.BindingSource>元件會實作<xref:System.ComponentModel.IBindingListView>和<xref:System.ComponentModel.ITypedList>介面。 此實作中，您可以使用<xref:System.Windows.Forms.BindingSource>元件本身當做資料來源，而不需要任何外部儲存體。  
  
 當<xref:System.Windows.Forms.BindingSource>元件連接到資料來源，它會公開為清單的資料來源。  
  
 <xref:System.Windows.Forms.BindingSource.DataSource%2A>屬性可以設定為多個資料來源。 其中包括型別、 物件和類型的清單。 產生的資料來源會公開為清單。 下表顯示一些常見的資料來源和產生的清單評估。  
  
|資料來源屬性|清單結果|  
|-------------------------|------------------|  
|null 參考 (在 Visual Basic 中為 `Nothing`)|空白<xref:System.ComponentModel.IBindingList>的物件。 新增項目設定要加入的項目類型的清單。|  
|Null 參考 (`Nothing`在 Visual Basic 中) 與<xref:System.Windows.Forms.BindingSource.DataMember%2A>設定|不支援;引發<xref:System.ArgumentException>。|  
|非清單型別或型別"T"的物件|空白<xref:System.ComponentModel.IBindingList>的型別"T"。|  
|陣列執行個體|<xref:System.ComponentModel.IBindingList>包含陣列項目。|  
|<xref:System.Collections.IEnumerable> 執行個體|<xref:System.ComponentModel.IBindingList>包含<xref:System.Collections.IEnumerable>項目|  
|列出執行個體，包含型別"T"|<xref:System.ComponentModel.IBindingList>包含型別"T"的執行個體。|  
  
 此外，<xref:System.Windows.Forms.BindingSource.DataSource%2A>可以設定為其他清單類型，例如<xref:System.ComponentModel.IListSource>並<xref:System.ComponentModel.ITypedList>，和<xref:System.Windows.Forms.BindingSource>會適當地處理它們。 在此情況下，在清單中包含的類型應該有預設建構函式。  
  
### <a name="bindingsource-as-an-ibindinglist"></a>BindingSource 表示為 IBindingList  
 <xref:System.Windows.Forms.BindingSource>元件所提供用於存取和管理為基礎的資料成員<xref:System.ComponentModel.IBindingList>。 下表說明部分這些成員。  
  
|成員|描述|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A> 屬性|取得評估的結果清單<xref:System.Windows.Forms.BindingSource.DataSource%2A>或<xref:System.Windows.Forms.BindingSource.DataMember%2A>屬性。|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> 方法|將新的項目加入基礎清單中。 適用於實作的資料來源<xref:System.ComponentModel.IBindingList>介面，並允許加入項目 (亦即<xref:System.Windows.Forms.BindingSource.AllowNew%2A>屬性設定為`true`)。|  
  
### <a name="custom-item-creation"></a>建立自訂項目  
 您可以處理<xref:System.Windows.Forms.BindingSource.AddingNew>事件來提供您自己的項目建立的邏輯。 <xref:System.Windows.Forms.BindingSource.AddingNew>加入新的物件之前，就會發生事件<xref:System.Windows.Forms.BindingSource>。 之後會引發這個事件<xref:System.Windows.Forms.BindingSource.AddNew%2A>呼叫方法時，但新的項目加入基礎清單之前。 藉由處理這個事件，您可以提供自訂的項目建立行為，而不需要衍生自<xref:System.Windows.Forms.BindingSource>類別。 如需詳細資訊，請參閱[如何：自訂使用 Windows Forms BindingSource 的項目加入](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)。  
  
### <a name="transactional-item-creation"></a>建立交易式的項目  
 <xref:System.Windows.Forms.BindingSource>元件實作<xref:System.ComponentModel.ICancelAddNew>介面，讓建立交易式的項目。 部份建立新的項目使用的呼叫之後<xref:System.Windows.Forms.BindingSource.AddNew%2A>，可能會認可或回復透過下列方式新增：  
  
- <xref:System.ComponentModel.ICancelAddNew.EndNew%2A>方法將會明確地認可暫止的加入。  
  
- 執行另一個集合運算，例如插入、 移除或移動，將會以隱含方式認可暫止的加入。  
  
- <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>方法將復原暫止的加入如果方法已被認可。  
  
### <a name="ienumerable-support"></a>IEnumerable 支援  
 <xref:System.Windows.Forms.BindingSource>元件可讓控制項繫結至<xref:System.Collections.IEnumerable>資料來源。 與這個元件，您可以繫結至資料來源這類<xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>。  
  
 當<xref:System.Collections.IEnumerable>資料來源已指派給<xref:System.Windows.Forms.BindingSource>元件，<xref:System.Windows.Forms.BindingSource>建立<xref:System.ComponentModel.IBindingList>並將內容加入<xref:System.Collections.IEnumerable>清單中的資料來源。  
  
### <a name="design-time-support"></a>設計階段支援  
 無法建立某些物件類型，在設計階段，例如從 factory 類別，建立的物件或 Web 服務所傳回的物件。 您有時可能要將控制項繫結至這些類型在設計階段，即使在您的控制項可以繫結的記憶體中沒有任何物件。 比方說，可能需要加上標籤的資料行標頭<xref:System.Windows.Forms.DataGridView>控制您的自訂類型的公用屬性的名稱。  
  
 為了支援此案例中，<xref:System.Windows.Forms.BindingSource>元件支援的繫結至<xref:System.Type>。 當您將指派<xref:System.Type>要<xref:System.Windows.Forms.BindingSource.DataSource%2A>屬性，<xref:System.Windows.Forms.BindingSource>元件會建立空白<xref:System.ComponentModel.BindingList%601>的<xref:System.Type>項目。 您接著繫結至任何控制項<xref:System.Windows.Forms.BindingSource>元件會警示您類型的結構描述之屬性的目前狀態，在設計階段，或在執行階段。 如需詳細資訊，請參閱[如何：將 Windows Forms 控制項繫結至型別](how-to-bind-a-windows-forms-control-to-a-type.md)。  
  
### <a name="static-listbindinghelper-methods"></a>靜態 ListBindingHelper 方法  
 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>， <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>，並<xref:System.Windows.Forms.BindingSource>類型來產生一份清單列出的共用通用邏輯`DataSource` / `DataMember`組。 此外，這個常見的邏輯對外公開使用的控制項作者和其他第三方在下列`static`方法：  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>排序和篩選 IBindingListView 介面  
 <xref:System.Windows.Forms.BindingSource>元件會實作<xref:System.ComponentModel.IBindingListView>介面，此功能擴充了<xref:System.ComponentModel.IBindingList>介面。 <xref:System.ComponentModel.IBindingList>提供了單一資料行排序和<xref:System.ComponentModel.IBindingListView>提供進階排序和篩選。 使用<xref:System.ComponentModel.IBindingListView>，您可以排序和篩選項目，在資料來源中，如果資料來源也會實作這些介面的其中一個。 <xref:System.Windows.Forms.BindingSource>元件不提供這些成員的參考實作。 相反地，呼叫會轉送至基礎清單中。  
  
 下表描述您用於排序和篩選的屬性。  
  
|成員|描述|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> 屬性|如果資料來源是 <xref:System.ComponentModel.IBindingListView>，可取得或設定用來篩選所檢視之資料列的運算式。|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> 屬性|如果資料來源是 <xref:System.ComponentModel.IBindingList>，可取得或設定用來排序的資料行名稱，以及排序次序資訊。<br /><br /> -或-<br /><br /> 如果資料來源是<xref:System.ComponentModel.IBindingListView>並支援進階排序，取得用來排序和排序順序的多個資料行名稱|  
  
### <a name="integration-with-bindingnavigator"></a>BindingNavigator 與整合  
 您可以使用<xref:System.Windows.Forms.BindingSource>元件，以將任何 Windows Form 控制項繫結至資料來源，但<xref:System.Windows.Forms.BindingNavigator>控制項是專為搭配<xref:System.Windows.Forms.BindingSource>元件。 <xref:System.Windows.Forms.BindingNavigator>控制項提供使用者介面來控制<xref:System.Windows.Forms.BindingSource>元件的目前項目。 根據預設，<xref:System.Windows.Forms.BindingNavigator>控制項提供的巡覽方法對應的按鈕<xref:System.Windows.Forms.BindingSource>元件。 如需詳細資訊，請參閱[如何：使用 Windows Forms BindingNavigator 控制項巡覽資料](how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [BindingSource 元件概觀](bindingsource-component-overview.md)
- [BindingNavigator 控制項](bindingnavigator-control-windows-forms.md)
- [Windows Forms 資料繫結](../windows-forms-data-binding.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [如何：將 Windows Forms 控制項繫結至型別](how-to-bind-a-windows-forms-control-to-a-type.md)
- [如何：反映 Windows Form 控制項使用 BindingSource 中的資料來源更新](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
