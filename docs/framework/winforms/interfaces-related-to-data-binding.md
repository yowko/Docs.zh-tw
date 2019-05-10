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
ms.openlocfilehash: 1609fbd8cbb24d6f2c10fbc3a235f01a451eb0fa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754072"
---
# <a name="interfaces-related-to-data-binding"></a>與資料繫結相關的介面

透過 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]，您可以建立許多不同的資料結構，以滿足您正在使用之應用程式和資料的繫結需求。 您或許會想要建立自有類別以在 Windows Forms 中提供或取用資料。 這些物件可以提供不同程度的功能和複雜度，從基本的資料繫結，到提供設計階段支援、錯誤檢查、變更通知，或甚至對資料本身所做變更的結構化回復支援。

## <a name="consumers-of-data-binding-interfaces"></a>資料繫結介面的取用者

下列幾節會說明兩個群組的介面物件。 第一個群組所列出的介面會由資料來源作者實作到資料來源上。 這些介面是設計來供資料來源取用者取用，而在大部分情況下，這些取用者就是 Windows Forms 控制項或元件。 第二個群組所列出的介面則是設計來供元件作者使用。 元件作者在建立可支援資料繫結的元件以供 Windows Forms 資料繫結引擎取用時，就會使用這些介面。 您可以在與表單相關聯的類別內實作這些介面，以啟用資料繫結；下列每個案例都會提出一個類別，該類別會實作可與資料互動的介面。 Visual Studio 的快速應用程式開發 (RAD) 的資料設計體驗工具已利用這項功能。

### <a name="interfaces-for-implementation-by-data-source-authors"></a>可供資料來源作者實作的介面

下列介面是設計來供 Windows Forms 控制項取用︰

- <xref:System.Collections.IList> 介面

  類別若實作<xref:System.Collections.IList>介面可能<xref:System.Array>， <xref:System.Collections.ArrayList>，或<xref:System.Collections.CollectionBase>。 這些是型別項目的索引的清單<xref:System.Object>。 這些清單必須包含同質型別，因為此索引的第一個項目會決定其型別。 <xref:System.Collections.IList> 會在適用於只能在執行階段的繫結。

  > [!NOTE]
  >  如果您想要使用 Windows Form 建立商務物件繫結的清單，您應該考慮使用<xref:System.ComponentModel.BindingList%601>。 <xref:System.ComponentModel.BindingList%601>是一個可延伸的類別，實作雙向 Windows Form 資料繫結所需的主要介面。

- <xref:System.ComponentModel.IBindingList> 介面

  類別若實作<xref:System.ComponentModel.IBindingList>介面提供更高層級的資料繫結功能。 此實作可提供您基本的排序功能和變更通知，讓您在清單項目變更時 (例如，客戶清單的第三個項目變更了 [位址] 欄位) 以及在清單本身變更時 (例如，清單的項目數增加或減少) 使用。 如果您打算讓多個控制項繫結至相同資料，並想要讓其中一個控制項的資料變更傳播到其他繫結控制項，變更通知就很重要。

  > [!NOTE]
  > 已啟用變更通知<xref:System.ComponentModel.IBindingList>透過介面<xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A>屬性的當`true`，會引發<xref:System.ComponentModel.IBindingList.ListChanged>變更事件，表示清單已變更或清單中的項目。

  所描述的變更類型<xref:System.ComponentModel.ListChangedType>屬性<xref:System.ComponentModel.ListChangedEventArgs>參數。 因此，每當資料模型更新時，所有相依的檢視 (例如其他繫結至相同資料來源的控制項) 也會隨之更新。 不過，在清單中包含的物件會有變更，因此，清單才能引發時，通知清單<xref:System.ComponentModel.IBindingList.ListChanged>事件。

  > [!NOTE]
  > <xref:System.ComponentModel.BindingList%601>提供的泛型實作<xref:System.ComponentModel.IBindingList>介面。

- <xref:System.ComponentModel.IBindingListView> 介面

  類別若實作<xref:System.ComponentModel.IBindingListView>介面提供的實作的所有功能<xref:System.ComponentModel.IBindingList>，以及篩選和進階排序功能。 此實作可提供以字串為基礎的篩選功能，以及利用屬性描述元與方向配對來進行的多欄排序功能。

- <xref:System.ComponentModel.IEditableObject> 介面

  類別若實作<xref:System.ComponentModel.IEditableObject>介面可讓要控制何時進行永久變更該物件的物件。 這個實作可提供您<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>， <xref:System.ComponentModel.IEditableObject.EndEdit%2A>，和<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>方法，可讓您回復物件所做的變更。 以下是簡短說明的運作<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>， <xref:System.ComponentModel.IEditableObject.EndEdit%2A>，和<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>方法，以及它們如何搭配另一個啟用得以復原您的資料所做的變更：

  - <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>方法表示的物件上開始編輯。 實作此介面的物件必須儲存所有更新後,<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>方法呼叫的方式，可捨棄更新如果<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>呼叫方法。 在資料繫結 Windows Form 中，您可以呼叫<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>多個時間範圍內的單一編輯交易 (例如<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>， <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>， <xref:System.ComponentModel.IEditableObject.EndEdit%2A>)。 實作<xref:System.ComponentModel.IEditableObject>應該追蹤是否<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>已經呼叫，並忽略後續呼叫<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>。 因為可以多次呼叫這個方法，是很重要的後續呼叫是破壞性;也就是說，後續<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>呼叫不能終結已進行，或變更已儲存的資料更新第一天<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>呼叫。

  - <xref:System.ComponentModel.IEditableObject.EndEdit%2A>方法會將推入的任何變更<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>呼叫到基礎物件，如果物件目前處於編輯模式。

  - <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>方法會捨棄任何物件所做的變更。

  如需有關如何<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>， <xref:System.ComponentModel.IEditableObject.EndEdit%2A>，並<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>方法運作，請參閱[將資料儲存回資料庫](/visualstudio/data-tools/save-data-back-to-the-database)。

  資料功能的這個交易性概念由<xref:System.Windows.Forms.DataGridView>控制項。

- <xref:System.ComponentModel.ICancelAddNew> 介面

  類別若實作<xref:System.ComponentModel.ICancelAddNew>通常會實作介面<xref:System.ComponentModel.IBindingList>介面，並可讓您回復所進行的資料來源<xref:System.ComponentModel.IBindingList.AddNew%2A>方法。 如果您的資料來源會實作<xref:System.ComponentModel.IBindingList>介面，您應該讓它也實作<xref:System.ComponentModel.ICancelAddNew>介面。

- <xref:System.ComponentModel.IDataErrorInfo> 介面

  類別若實作<xref:System.ComponentModel.IDataErrorInfo>介面可讓物件能夠繫結控制項的自訂錯誤資訊：

  - <xref:System.ComponentModel.IDataErrorInfo.Error%2A>屬性會傳回一般錯誤訊息文字 （例如，「 已發生錯誤 」）。

  - <xref:System.ComponentModel.IDataErrorInfo.Item%2A>屬性會傳回含有特定的錯誤訊息的字串資料行 (例如，"中的值`State`資料行無效 」)。

- <xref:System.Collections.IEnumerable> 介面

  類別若實作<xref:System.Collections.IEnumerable>介面通常由[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]。 此介面的 Windows Form 支援僅可透過<xref:System.Windows.Forms.BindingSource>元件。

  > [!NOTE]
  > <xref:System.Windows.Forms.BindingSource>元件會複製所有<xref:System.Collections.IEnumerable>到不同的清單，供繫結使用的項目。

- <xref:System.ComponentModel.ITypedList> 介面

  集合類別若實作<xref:System.ComponentModel.ITypedList>介面讓您能夠控制的順序，以及一組屬性公開至繫結的控制項。

  > [!NOTE]
  > 當您實作<xref:System.ComponentModel.ITypedList.GetItemProperties%2A>方法，而<xref:System.ComponentModel.PropertyDescriptor>陣列不是 null，在陣列中的最後一個項目會描述已是另一個項目清單的清單屬性的屬性描述元。

- <xref:System.ComponentModel.ICustomTypeDescriptor> 介面

  類別若實作<xref:System.ComponentModel.ICustomTypeDescriptor>介面會提供有關本身的動態資訊。 這個介面是類似於<xref:System.ComponentModel.ITypedList>，但用於物件，而不是清單。 這個介面由<xref:System.Data.DataRowView>投影基礎資料列的結構描述。 簡單實作<xref:System.ComponentModel.ICustomTypeDescriptor>係由<xref:System.ComponentModel.CustomTypeDescriptor>類別。

  > [!NOTE]
  > 若要支援設計階段繫結至型別都會實作<xref:System.ComponentModel.ICustomTypeDescriptor>，也必須實作的型別<xref:System.ComponentModel.IComponent>，做為表單上的執行個體存在。

- <xref:System.ComponentModel.IListSource> 介面

  類別若實作<xref:System.ComponentModel.IListSource>介面可讓非 list 物件上的清單架構繫結。 <xref:System.ComponentModel.IListSource.GetList%2A>方法<xref:System.ComponentModel.IListSource>用來傳回可繫結的清單，從並非繼承自物件<xref:System.Collections.IList>。 <xref:System.ComponentModel.IListSource> 會使用<xref:System.Data.DataSet>類別。

- <xref:System.ComponentModel.IRaiseItemChangedEvents> 介面

  類別若實作<xref:System.ComponentModel.IRaiseItemChangedEvents>介面是以可繫結的清單，也會實作<xref:System.ComponentModel.IBindingList>介面。 此介面用來指出您的型別是否引發<xref:System.ComponentModel.IBindingList.ListChanged>類型的事件<xref:System.ComponentModel.ListChangedType.ItemChanged>透過其<xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A>屬性。

  > [!NOTE]
  > 您應該實作<xref:System.ComponentModel.IRaiseItemChangedEvents>如果您的資料來源提供的屬性至清單事件 」 轉換先前所述，而且正在與互動<xref:System.Windows.Forms.BindingSource>元件。 否則，<xref:System.Windows.Forms.BindingSource>也會執行 「 屬性至清單事件 」 轉換導致效能變慢。

- <xref:System.ComponentModel.ISupportInitialize> 介面

  元件若實作<xref:System.ComponentModel.ISupportInitialize>介面就會利用批次最佳化來設定屬性，並初始化共同相依的屬性。 <xref:System.ComponentModel.ISupportInitialize>包含兩個方法：

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> 表示正在啟動該物件初始化。

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> 表示已完成的物件初始設定。

- <xref:System.ComponentModel.ISupportInitializeNotification> 介面

  實作的元件<xref:System.ComponentModel.ISupportInitializeNotification>介面也會實作<xref:System.ComponentModel.ISupportInitialize>介面。 此介面可讓您通知其他<xref:System.ComponentModel.ISupportInitialize>元件表示初始化已完成。 <xref:System.ComponentModel.ISupportInitializeNotification>介面包含兩個成員：

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> 傳回`boolean`值，指出元件是否已初始化。

  - <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> 發生時<xref:System.ComponentModel.ISupportInitialize.EndInit%2A>呼叫。

- <xref:System.ComponentModel.INotifyPropertyChanged> 介面

  類別若實作此介面，代表其所屬的型別會在其任何屬性值變更時引發事件。 對於會讓控制項的每個屬性有一個變更事件的模式，我們設計了此介面來加以取代。 在中使用時<xref:System.ComponentModel.BindingList%601>，應該實作的商務物件<xref:System.ComponentModel.INotifyPropertyChanged>介面，而且 BindingList\`1 會將轉換<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>事件<xref:System.ComponentModel.BindingList%601.ListChanged>型別事件<xref:System.ComponentModel.ListChangedType.ItemChanged>。

  > [!NOTE]
  > 變更通知，以在繫結的用戶端和資料之間的繫結來源繫結的資料來源類型應該實作<xref:System.ComponentModel.INotifyPropertyChanged>介面 （慣用） 或您可以提供*propertyName* `Changed`事件繫結的型別，但您不應該進行這兩項。

### <a name="interfaces-for-implementation-by-component-authors"></a>可供元件作者實作的介面

下列介面是設計來供 Windows Forms 資料繫結引擎取用︰

- <xref:System.Windows.Forms.IBindableComponent> 介面

  類別若實作此介面，就是可支援資料繫結的非控制項元件。 這個類別會傳回的資料繫結和繫結內容的元件，透過<xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>和<xref:System.Windows.Forms.IBindableComponent.BindingContext%2A>此介面的屬性。

  > [!NOTE]
  > 如果您的元件繼承自<xref:System.Windows.Forms.Control>，您不需要實作<xref:System.Windows.Forms.IBindableComponent>介面。

- <xref:System.Windows.Forms.ICurrencyManagerProvider> 介面

  類別若實作<xref:System.Windows.Forms.ICurrencyManagerProvider>介面是一個元件，提供它自己<xref:System.Windows.Forms.CurrencyManager>來管理這個特定元件相關聯的繫結。 存取自訂<xref:System.Windows.Forms.CurrencyManager>係由<xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>屬性。

  > [!NOTE]
  > 類別繼承自<xref:System.Windows.Forms.Control>管理繫結會自動透過其<xref:System.Windows.Forms.Control.BindingContext%2A>屬性，因此您需要實作的情況下<xref:System.Windows.Forms.ICurrencyManagerProvider>很少見。

## <a name="see-also"></a>另請參閱

- [資料繫結和 Windows Forms](data-binding-and-windows-forms.md)
- [如何：建立 Windows Form 上的簡單繫結控制項](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Windows Forms 資料繫結](windows-forms-data-binding.md)
