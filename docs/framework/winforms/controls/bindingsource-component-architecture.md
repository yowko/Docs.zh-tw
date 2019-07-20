---
title: BindingSource 元件架構
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: 54a23ba899ceb05701fe3580aefbb723c6b3f0fd
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364412"
---
# <a name="bindingsource-component-architecture"></a>BindingSource 元件架構
<xref:System.Windows.Forms.BindingSource>使用元件, 您可以將所有 Windows Forms 控制項通用地系結至資料來源。  
  
 此<xref:System.Windows.Forms.BindingSource>元件簡化了將控制項系結至資料來源的程式, 並提供與傳統資料系結相比的下列優點:  
  
- 啟用商務物件的設計階段系結。  
  
- 封裝<xref:System.Windows.Forms.CurrencyManager>功能, 並<xref:System.Windows.Forms.CurrencyManager>在設計階段公開事件。  
  
- 藉由提供不以原生<xref:System.ComponentModel.IBindingList>方式支援清單變更通知的資料來源清單變更通知, 簡化建立支援介面的清單。  
  
- 提供<xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType>方法的擴充點。  
  
- 提供資料來源和控制項之間的間接取值層級。 當資料來源在執行時間可能變更時, 這個間接取值就很重要。  
  
- 與其他資料相關的 Windows Forms 控制項交互操作, 尤其<xref:System.Windows.Forms.BindingNavigator>是<xref:System.Windows.Forms.DataGridView>和控制項。  
  
 基於這些理由, <xref:System.Windows.Forms.BindingSource>元件是將 Windows Forms 控制項系結至資料來源的慣用方式。  
  
## <a name="bindingsource-features"></a>BindingSource 功能  
 <xref:System.Windows.Forms.BindingSource>元件提供數個將控制項系結至資料的功能。 有了這些功能, 您就可以執行大部分的資料系結案例, 幾乎不需要自行撰寫程式碼。  
  
 此<xref:System.Windows.Forms.BindingSource>元件藉由提供一致的介面來存取許多不同類型的資料來源, 來完成這項工作。 這表示您會使用相同的程式來系結至任何類型。 例如, 您可以將<xref:System.Windows.Forms.BindingSource.DataSource%2A>屬性附加<xref:System.Data.DataSet>至或商務物件, 而在這兩種情況下, 您會使用相同的屬性、方法和事件集來運算元據源。  
  
 <xref:System.Windows.Forms.BindingSource>元件所提供的一致介面會大幅簡化將資料系結至控制項的程式。 對於提供變更通知的資料來源類型, <xref:System.Windows.Forms.BindingSource>元件會自動傳達控制項與資料來源之間的變更。 若為不提供變更通知的資料來源類型, 則會提供事件, 讓您引發變更通知。 下列清單顯示<xref:System.Windows.Forms.BindingSource>元件支援的功能:  
  
- 間接取值.  
  
- 貨幣管理。  
  
- 以清單形式的資料來源。  
  
- <xref:System.Windows.Forms.BindingSource>做為<xref:System.ComponentModel.IBindingList>。  
  
- 自訂專案建立。  
  
- 建立交易式專案。  
  
- <xref:System.Collections.IEnumerable>部門.  
  
- 設計階段支援。  
  
- 靜態<xref:System.Windows.Forms.ListBindingHelper>方法。  
  
- 使用<xref:System.ComponentModel.IBindingListView>介面進行排序和篩選。  
  
- 與<xref:System.Windows.Forms.BindingNavigator>整合。  
  
### <a name="indirection"></a>間接  
 <xref:System.Windows.Forms.BindingSource>元件提供控制項和資料來源之間的間接取值層級。 您不需要將控制項直接系結至資料來源, 而是將控制項系<xref:System.Windows.Forms.BindingSource>結至, 並將資料來源附加<xref:System.Windows.Forms.BindingSource>至元件的<xref:System.Windows.Forms.BindingSource.DataSource%2A>屬性。  
  
 使用此間接取值層級, 您可以變更資料來源, 而不需要重設控制項系結。 這可提供下列功能:  
  
- 您可以將附加<xref:System.Windows.Forms.BindingSource>到不同的資料來源, 同時保留目前的控制項系結。  
  
- 您可以變更資料來源中的專案, 並通知繫結控制項。 如需詳細資訊，請參閱[如何：使用 BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)來反映 Windows Forms 控制項中的資料來源更新。  
  
- 您可以系結至<xref:System.Type>記憶體中的, 而不是物件。 如需詳細資訊，請參閱[如何：將 Windows Forms 控制項系結至類型](how-to-bind-a-windows-forms-control-to-a-type.md)。 接著, 您可以在執行時間系結至物件。  
  
### <a name="currency-management"></a>貨幣管理  
 <xref:System.Windows.Forms.BindingSource>元件會執行介面,為<xref:System.Windows.Forms.ICurrencyManagerProvider>您處理貨幣管理。 使用介面, 除了另<xref:System.Windows.Forms.BindingSource>一個系結至相同<xref:System.Windows.Forms.BindingSource.DataMember%2A>的貨幣管理員以外<xref:System.Windows.Forms.BindingSource>, 您也可以存取的「貨幣管理員」。 <xref:System.Windows.Forms.ICurrencyManagerProvider>  
  
 元件會封裝<xref:System.Windows.Forms.CurrencyManager>功能並公開最常見<xref:System.Windows.Forms.CurrencyManager>的屬性和事件。 <xref:System.Windows.Forms.BindingSource> 下表描述一些與貨幣管理相關的成員。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> 屬性  
 取得與<xref:System.Windows.Forms.BindingSource>相關聯的 currency 管理員。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A> 方法  
 如果有另一個<xref:System.Windows.Forms.BindingSource>系結至指定的資料成員, 則會取得其 currency 管理員。  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A> 屬性  
 取得資料來源的目前項目。  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A> 屬性  
 取得或設定基礎清單中的目前位置。  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 方法  
 將暫止的變更套用至基礎資料來源。  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> 方法  
 取消目前的編輯作業。  
  
### <a name="data-source-as-a-list"></a>以清單形式的資料來源  
 元件會執行<xref:System.ComponentModel.ITypedList>和介面。 <xref:System.ComponentModel.IBindingListView> <xref:System.Windows.Forms.BindingSource> 使用此實作為, 您可以使用<xref:System.Windows.Forms.BindingSource>元件本身作為資料來源, 而不需要任何外部儲存體。  
  
 <xref:System.Windows.Forms.BindingSource>當元件附加至資料來源時, 它會將資料來源公開為清單。  
  
 <xref:System.Windows.Forms.BindingSource.DataSource%2A>屬性可以設定為數個數據源。 這些包括類型、物件和類型清單。 產生的資料來源將會公開為清單。 下表顯示一些常見的資料來源和所產生的清單評估。  
  
|DataSource 屬性|列出結果|  
|-------------------------|------------------|  
|null 參考 (在 Visual Basic 中為 `Nothing`)|物件的<xref:System.ComponentModel.IBindingList>空白。 加入專案會將清單設定為已加入專案的類型。|  
|`Nothing` 具有<xref:System.Windows.Forms.BindingSource.DataMember%2A> set 的 null 參考 (在 Visual Basic 中)|不支援;引發<xref:System.ArgumentException>。|  
|非清單類型或類型 "T" 的物件|類型為<xref:System.ComponentModel.IBindingList> "T" 的空白。|  
|陣列實例|<xref:System.ComponentModel.IBindingList>包含陣列元素的。|  
|<xref:System.Collections.IEnumerable>示例|<xref:System.ComponentModel.IBindingList> 包含<xref:System.Collections.IEnumerable>專案的。|  
|包含類型 "T" 的清單實例|包含<xref:System.ComponentModel.IBindingList>類型 "T" 的實例。|  
  
 此外, <xref:System.Windows.Forms.BindingSource.DataSource%2A>可以設定為其他清單類型 ( <xref:System.ComponentModel.IListSource>例如和<xref:System.ComponentModel.ITypedList>), 而且<xref:System.Windows.Forms.BindingSource>會適當地處理它們。 在此情況下, 清單中所包含的型別應該具有無參數的函式。  
  
### <a name="bindingsource-as-an-ibindinglist"></a>BindingSource 做為 IBindingList  
 元件會提供成員來存取和操作基礎資料<xref:System.ComponentModel.IBindingList>做為。 <xref:System.Windows.Forms.BindingSource> 下表描述其中一些成員。  
  
|成員|說明|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A> 屬性|取得由<xref:System.Windows.Forms.BindingSource.DataSource%2A>或<xref:System.Windows.Forms.BindingSource.DataMember%2A>屬性的評估所產生的清單。|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> 方法|將新的項目加入基礎清單中。 適用于執行<xref:System.ComponentModel.IBindingList>介面並允許加入專案的資料來源 (也就是<xref:System.Windows.Forms.BindingSource.AllowNew%2A>屬性設定為`true`)。|  
  
### <a name="custom-item-creation"></a>自訂專案建立  
 您可以處理<xref:System.Windows.Forms.BindingSource.AddingNew>事件, 以提供您自己的專案建立邏輯。 事件發生于新的物件加入<xref:System.Windows.Forms.BindingSource>至之前。 <xref:System.Windows.Forms.BindingSource.AddingNew> 這個事件是在呼叫<xref:System.Windows.Forms.BindingSource.AddNew%2A>方法之後, 但在將新專案加入基礎清單之前引發。 藉由處理這個事件, 您可以提供自訂專案建立行為, 而<xref:System.Windows.Forms.BindingSource>不需要從類別衍生。 如需詳細資訊，請參閱[如何：使用 Windows Forms BindingSource](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)自訂加入專案。  
  
### <a name="transactional-item-creation"></a>交易式專案建立  
 <xref:System.Windows.Forms.BindingSource>元件會執行介面,以啟用交易<xref:System.ComponentModel.ICancelAddNew>式專案的建立。 使用的呼叫<xref:System.Windows.Forms.BindingSource.AddNew%2A>建立新專案 provisionally 之後, 可能會以下列方式來認可或回復加入:  
  
- <xref:System.ComponentModel.ICancelAddNew.EndNew%2A>方法會明確認可暫止的加入。  
  
- 執行另一個集合作業 (例如插入、移除或移動), 會隱含地認可擱置的加入。  
  
- 如果<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>尚未認可方法, 此方法將會回復暫止的新增。  
  
### <a name="ienumerable-support"></a>IEnumerable 支援  
 元件可讓您將控制項<xref:System.Collections.IEnumerable>系結至資料來源。 <xref:System.Windows.Forms.BindingSource> 使用此元件, 您可以系結至資料來源 (例如<xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>)。  
  
 <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource> <xref:System.Collections.IEnumerable>將資料來源指派給<xref:System.ComponentModel.IBindingList>元件時, 會建立, 並將資料來源的內容加入至清單中。 <xref:System.Collections.IEnumerable>  
  
### <a name="design-time-support"></a>設計階段支援  
 某些物件類型無法在設計階段建立, 例如從 factory 類別建立的物件, 或由 Web 服務傳回的物件。 您有時可能需要在設計階段將控制項系結至這些類型, 即使您的控制項可以系結的記憶體中沒有物件。 例如, 您可能需要使用自訂類型之公用屬性的名稱<xref:System.Windows.Forms.DataGridView> , 為控制項的資料行標頭加上標籤。  
  
 為了支援此案例, <xref:System.Windows.Forms.BindingSource>元件支援系結<xref:System.Type>至。 當您將指派<xref:System.Type> <xref:System.Windows.Forms.BindingSource.DataSource%2A>給屬性時, 該<xref:System.Windows.Forms.BindingSource>元件會建立一個<xref:System.ComponentModel.BindingList%601>空<xref:System.Type>的專案。 您後續系結至<xref:System.Windows.Forms.BindingSource>元件的任何控制項都會在設計階段或執行時間收到您類型的屬性或架構出現的警示。 如需詳細資訊，請參閱[如何：將 Windows Forms 控制項系結至類型](how-to-bind-a-windows-forms-control-to-a-type.md)。  
  
### <a name="static-listbindinghelper-methods"></a>靜態 ListBindingHelper 方法  
 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>、和<xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>類型全都/會共用`DataSource` 共同的邏輯,以從`DataMember`配對產生清單。 <xref:System.Windows.Forms.BindingSource> 此外, 這個常見的邏輯會公開供控制項作者和其他協力廠商用於下列`static`方法:  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>使用 IBindingListView 介面進行排序和篩選  
 元件會執行<xref:System.ComponentModel.IBindingList>介面, 以擴充介面。 <xref:System.ComponentModel.IBindingListView> <xref:System.Windows.Forms.BindingSource> 提供單一資料行排序, 以及<xref:System.ComponentModel.IBindingListView>提供先進的排序和篩選。 <xref:System.ComponentModel.IBindingList> 使用<xref:System.ComponentModel.IBindingListView>, 您可以在資料來源中排序和篩選項目 (如果資料來源也會執行這些介面的其中一個)。 <xref:System.Windows.Forms.BindingSource>元件不會提供這些成員的參考執行。 相反地, 呼叫會轉送到基礎清單。  
  
 下表描述您用於排序和篩選的屬性。  
  
|成員|描述|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> 屬性|如果資料來源是 <xref:System.ComponentModel.IBindingListView>，可取得或設定用來篩選所檢視之資料列的運算式。|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> 屬性|如果資料來源是 <xref:System.ComponentModel.IBindingList>，可取得或設定用來排序的資料行名稱，以及排序次序資訊。<br /><br /> -或-<br /><br /> 如果資料來源是<xref:System.ComponentModel.IBindingListView>並支援高階排序, 會取得用於排序和排序次序的多個資料行名稱|  
  
### <a name="integration-with-bindingnavigator"></a>與 BindingNavigator 整合  
 您可以使用<xref:System.Windows.Forms.BindingSource>元件將任何 Windows Forms 控制項系結至資料來源, <xref:System.Windows.Forms.BindingNavigator>但控制項是<xref:System.Windows.Forms.BindingSource>特別設計來與元件搭配使用。 控制項會提供用來<xref:System.Windows.Forms.BindingSource>控制元件目前專案的使用者介面。 <xref:System.Windows.Forms.BindingNavigator> 根據預設, <xref:System.Windows.Forms.BindingNavigator>控制項會提供對應至<xref:System.Windows.Forms.BindingSource>元件上之導覽方法的按鈕。 如需詳細資訊，請參閱[如何：使用 Windows Forms BindingNavigator 控制項](how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md)流覽資料。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [BindingSource 元件概觀](bindingsource-component-overview.md)
- [BindingNavigator 控制項](bindingnavigator-control-windows-forms.md)
- [Windows Forms 資料繫結](../windows-forms-data-binding.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [如何：將 Windows Forms 控制項系結至類型](how-to-bind-a-windows-forms-control-to-a-type.md)
- [如何：使用 BindingSource 反映 Windows Forms 控制項中的資料來源更新](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
