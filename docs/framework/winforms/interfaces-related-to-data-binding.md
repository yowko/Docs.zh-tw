---
title: 與資料繫結相關的介面
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], data-binding interfaces
- INotifyPropertyChanged interface
- IBindingListView interface
- IList interface [Windows Forms], Windows Forms data binding
- IBindingList interface [Windows Forms], Windows Forms data binding
- interfaces [Windows Forms], Windows Forms data binding
- IEditableObject interface [Windows Forms], Windows Forms data binding
- data binding [Windows Forms], interfaces
- IDataErrorInfo interface [Windows Forms], Windows Forms data binding
ms.assetid: 14e49a2e-3e46-47ca-b491-70d546333277
ms.openlocfilehash: 9f102b584d2ed0b5a9d2bbb0e7ce3f7871ec40b2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046363"
---
# <a name="interfaces-related-to-data-binding"></a>與資料繫結相關的介面

透過 ADO.NET, 您可以建立許多不同的資料結構, 以符合應用程式的系結需求和您正在使用的資料。 您或許會想要建立自有類別以在 Windows Forms 中提供或取用資料。 這些物件可以提供不同程度的功能和複雜度，從基本的資料繫結，到提供設計階段支援、錯誤檢查、變更通知，或甚至對資料本身所做變更的結構化回復支援。

## <a name="consumers-of-data-binding-interfaces"></a>資料繫結介面的取用者

下列幾節會說明兩個群組的介面物件。 第一個群組所列出的介面會由資料來源作者實作到資料來源上。 這些介面是設計來供資料來源取用者取用，而在大部分情況下，這些取用者就是 Windows Forms 控制項或元件。 第二個群組所列出的介面則是設計來供元件作者使用。 元件作者在建立可支援資料繫結的元件以供 Windows Forms 資料繫結引擎取用時，就會使用這些介面。 您可以在與表單相關聯的類別內實作這些介面，以啟用資料繫結；下列每個案例都會提出一個類別，該類別會實作可與資料互動的介面。 Visual Studio 快速應用程式開發 (RAD) 資料設計體驗工具已充分利用這項功能。

### <a name="interfaces-for-implementation-by-data-source-authors"></a>可供資料來源作者實作的介面

下列介面是設計來供 Windows Forms 控制項取用︰

- <xref:System.Collections.IList>介面

  執行<xref:System.Collections.IList>介面的類別可以<xref:System.Array>是、 <xref:System.Collections.ArrayList>或<xref:System.Collections.CollectionBase>。 這些是類型<xref:System.Object>專案的索引清單。 這些清單必須包含同質型別，因為此索引的第一個項目會決定其型別。 <xref:System.Collections.IList>只有在執行時間才可供系結。

  > [!NOTE]
  > 如果您想要建立與 Windows Forms 系結的商務物件清單, 您應該考慮使用<xref:System.ComponentModel.BindingList%601>。 <xref:System.ComponentModel.BindingList%601>是一種可延伸的類別, 可執行雙向 Windows Forms 資料系結所需的主要介面。

- <xref:System.ComponentModel.IBindingList>介面

  執行<xref:System.ComponentModel.IBindingList>介面的類別提供更高層級的資料系結功能。 此實作可提供您基本的排序功能和變更通知，讓您在清單項目變更時 (例如，客戶清單的第三個項目變更了 [位址] 欄位) 以及在清單本身變更時 (例如，清單的項目數增加或減少) 使用。 如果您打算讓多個控制項繫結至相同資料，並想要讓其中一個控制項的資料變更傳播到其他繫結控制項，變更通知就很重要。

  > [!NOTE]
  > 會<xref:System.ComponentModel.IBindingList> `true`透過屬性來啟用介面的變更通知<xref:System.ComponentModel.IBindingList.ListChanged> , 而當引發事件時, 表示清單已變更或清單中的專案已變更。 <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A>

  變更的類型是由<xref:System.ComponentModel.ListChangedType> <xref:System.ComponentModel.ListChangedEventArgs>參數的屬性所描述。 因此，每當資料模型更新時，所有相依的檢視 (例如其他繫結至相同資料來源的控制項) 也會隨之更新。 不過, 清單中包含的物件必須在變更時通知清單, 讓清單可以引發<xref:System.ComponentModel.IBindingList.ListChanged>事件。

  > [!NOTE]
  > <xref:System.ComponentModel.BindingList%601>提供<xref:System.ComponentModel.IBindingList>介面的泛型實作為。

- <xref:System.ComponentModel.IBindingListView>介面

  執行<xref:System.ComponentModel.IBindingListView>介面的類別會提供的所有功能<xref:System.ComponentModel.IBindingList>, 以及篩選和先進排序功能。 此實作可提供以字串為基礎的篩選功能，以及利用屬性描述元與方向配對來進行的多欄排序功能。

- <xref:System.ComponentModel.IEditableObject>介面

  實作為<xref:System.ComponentModel.IEditableObject>介面的類別可讓物件控制何時將該物件的變更設為永久。 此實作為<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>提供您、 <xref:System.ComponentModel.IEditableObject.EndEdit%2A>和<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>方法, 可讓您復原對物件所做的變更。 以下簡短說明<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、和<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>方法的運作方式, 以及<xref:System.ComponentModel.IEditableObject.EndEdit%2A>它們如何彼此搭配運作, 以啟用對資料所做之變更的可能復原:

  - <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>方法會指示物件上的編輯開始。 執行此介面的物件必須在<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>方法呼叫之後儲存任何更新, 如此一來, <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>當呼叫方法時, 就可以捨棄更新。 在 資料系結 Windows Forms 中, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>您可以在單一編輯交易的範圍內多次呼叫 ( <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> <xref:System.ComponentModel.IEditableObject.EndEdit%2A>例如、、)。 的<xref:System.ComponentModel.IEditableObject>執行應該追蹤是否<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>已呼叫<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, 並忽略的後續呼叫。 因為可以多次呼叫此方法, 所以對它的後續呼叫很重要。也就是說, 後續<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>呼叫無法摧毀已進行的更新, 或變更第一次<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>呼叫時儲存的資料。

  - 方法<xref:System.ComponentModel.IEditableObject.EndEdit%2A>會將自呼叫之後<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>的任何變更推送至基礎物件中 (如果物件目前處於編輯模式)。

  - <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>方法會捨棄對物件所做的任何變更。

  如需<xref:System.ComponentModel.IEditableObject.BeginEdit%2A> <xref:System.ComponentModel.IEditableObject.EndEdit%2A>、和<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>方法如何工作的詳細資訊, 請參閱[將資料儲存回資料庫](/visualstudio/data-tools/save-data-back-to-the-database)。

  此資料功能的交易式概念是由控制項<xref:System.Windows.Forms.DataGridView>所使用。

- <xref:System.ComponentModel.ICancelAddNew>介面

  執行<xref:System.ComponentModel.ICancelAddNew>介面的類別通常會實作為<xref:System.ComponentModel.IBindingList>介面, 並可讓您使用<xref:System.ComponentModel.IBindingList.AddNew%2A>方法來復原對資料來源所做的加法。 如果您的<xref:System.ComponentModel.IBindingList>資料來源會執行介面, 您也應該讓它實<xref:System.ComponentModel.ICancelAddNew>作為介面。

- <xref:System.ComponentModel.IDataErrorInfo>介面

  實作為<xref:System.ComponentModel.IDataErrorInfo>介面的類別可讓物件提供自訂錯誤資訊給繫結控制項:

  - <xref:System.ComponentModel.IDataErrorInfo.Error%2A>屬性會傳回一般錯誤訊息正文 (例如「發生錯誤」)。

  - 屬性會傳回字串, 其中包含資料行中的特定錯誤訊息 (例如「資料`State`行中的值無效」)。 <xref:System.ComponentModel.IDataErrorInfo.Item%2A>

- <xref:System.Collections.IEnumerable>介面

  ASP.NET 通常會使用實<xref:System.Collections.IEnumerable>作為介面的類別。 只有透過<xref:System.Windows.Forms.BindingSource>元件才能使用此介面的 Windows Forms 支援。

  > [!NOTE]
  > 元件會將所有<xref:System.Collections.IEnumerable>專案複製到不同的清單, 以供系結之用。 <xref:System.Windows.Forms.BindingSource>

- <xref:System.ComponentModel.ITypedList>介面

  實作為<xref:System.ComponentModel.ITypedList>介面的集合類別, 可讓您控制對繫結控制項所公開的順序和屬性集。

  > [!NOTE]
  > 當您執行<xref:System.ComponentModel.ITypedList.GetItemProperties%2A>方法, <xref:System.ComponentModel.PropertyDescriptor>而且陣列不是 null 時, 陣列中的最後一個專案會是描述清單屬性 (也就是另一個專案清單) 的屬性描述元。

- <xref:System.ComponentModel.ICustomTypeDescriptor>介面

  執行<xref:System.ComponentModel.ICustomTypeDescriptor>介面的類別會提供本身的動態資訊。 這個介面類別似于, <xref:System.ComponentModel.ITypedList>但會用於物件, 而不是清單。 這個介面是由<xref:System.Data.DataRowView>用來投影基礎資料列的架構。 的簡單執行<xref:System.ComponentModel.ICustomTypeDescriptor>是由類別所<xref:System.ComponentModel.CustomTypeDescriptor>提供。

  > [!NOTE]
  > 為了支援將設計階段系結至<xref:System.ComponentModel.ICustomTypeDescriptor>實作為的型別, 型別也必須在表單上實作為實例並做為實例來執行。 <xref:System.ComponentModel.IComponent>

- <xref:System.ComponentModel.IListSource>介面

  執行<xref:System.ComponentModel.IListSource>介面的類別會在非清單物件上啟用以清單為基礎的系結。 的<xref:System.ComponentModel.IListSource.GetList%2A> <xref:System.Collections.IList>方法是用來從不是繼承自的物件傳回可系結清單。 <xref:System.ComponentModel.IListSource> <xref:System.ComponentModel.IListSource>由<xref:System.Data.DataSet>類別使用。

- <xref:System.ComponentModel.IRaiseItemChangedEvents>介面

  實作為<xref:System.ComponentModel.IRaiseItemChangedEvents>介面的類別是可系結的清單, 它也<xref:System.ComponentModel.IBindingList>會執行介面。 這個介面是用來指出您的類型是否<xref:System.ComponentModel.IBindingList.ListChanged>會透過其<xref:System.ComponentModel.ListChangedType.ItemChanged> <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A>屬性來引發類型的事件。

  > [!NOTE]
  > <xref:System.ComponentModel.IRaiseItemChangedEvents>如果您的資料來源提供屬性來列出先前所述的事件轉換, 而且正在<xref:System.Windows.Forms.BindingSource>與元件互動, 您應該執行。 否則, <xref:System.Windows.Forms.BindingSource>也會執行屬性來列出事件轉換, 因而導致效能變慢。

- <xref:System.ComponentModel.ISupportInitialize>介面

  執行<xref:System.ComponentModel.ISupportInitialize>介面的元件會利用批次優化的優點來設定屬性和初始化共同相依屬性。 <xref:System.ComponentModel.ISupportInitialize>包含兩種方法:

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A>通知物件初始化正在啟動。

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A>通知物件初始化已完成。

- <xref:System.ComponentModel.ISupportInitializeNotification>介面

  執行<xref:System.ComponentModel.ISupportInitializeNotification>介面的元件也會<xref:System.ComponentModel.ISupportInitialize>實行介面。 此介面可讓您通知其他<xref:System.ComponentModel.ISupportInitialize>元件已完成初始化。 此<xref:System.ComponentModel.ISupportInitializeNotification>介面包含兩個成員:

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A>傳回表示元件是否已初始化的值。`boolean`

  - <xref:System.ComponentModel.ISupportInitializeNotification.Initialized><xref:System.ComponentModel.ISupportInitialize.EndInit%2A>呼叫時發生。

- <xref:System.ComponentModel.INotifyPropertyChanged>介面

  類別若實作此介面，代表其所屬的型別會在其任何屬性值變更時引發事件。 對於會讓控制項的每個屬性有一個變更事件的模式，我們設計了此介面來加以取代。 在中<xref:System.ComponentModel.BindingList%601>使用時, 商務物件應該會<xref:System.ComponentModel.INotifyPropertyChanged>執行介面, 而 BindingList\`1 會將事件<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>轉換成<xref:System.ComponentModel.BindingList%601.ListChanged>類型<xref:System.ComponentModel.ListChangedType.ItemChanged>的事件。

  > [!NOTE]
  > 若要讓變更通知發生在系結的用戶端與資料來源之間的系結中, 系結的資料來源<xref:System.ComponentModel.INotifyPropertyChanged>類型應執行介面 (慣用), 或者您可以提供系結類型的*propertyName* `Changed`事件。但您不應該這麼做。

### <a name="interfaces-for-implementation-by-component-authors"></a>可供元件作者實作的介面

下列介面是設計來供 Windows Forms 資料繫結引擎取用︰

- <xref:System.Windows.Forms.IBindableComponent>介面

  類別若實作此介面，就是可支援資料繫結的非控制項元件。 這個類別會透過這個介面的<xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>和<xref:System.Windows.Forms.IBindableComponent.BindingContext%2A>屬性, 傳回元件的資料系結和系結內容。

  > [!NOTE]
  > 如果您的元件繼承<xref:System.Windows.Forms.Control>自, 您就不需要<xref:System.Windows.Forms.IBindableComponent>執行介面。

- <xref:System.Windows.Forms.ICurrencyManagerProvider>介面

  實作為<xref:System.Windows.Forms.ICurrencyManagerProvider>介面的類別是一個元件, 它會提供自己<xref:System.Windows.Forms.CurrencyManager>的來管理與此特定元件相關聯的系結。 自訂<xref:System.Windows.Forms.CurrencyManager>的存取是<xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>由屬性提供。

  > [!NOTE]
  > 繼承自<xref:System.Windows.Forms.Control>的類別會透過其<xref:System.Windows.Forms.Control.BindingContext%2A>屬性自動管理系結, 因此, 您需要執行的<xref:System.Windows.Forms.ICurrencyManagerProvider>情況相當罕見。

## <a name="see-also"></a>另請參閱

- [資料繫結和 Windows Forms](data-binding-and-windows-forms.md)
- [如何：在 Windows Form 上建立簡單繫結控制項](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Windows Forms 資料繫結](windows-forms-data-binding.md)
