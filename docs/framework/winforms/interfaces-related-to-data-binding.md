---
title: "與資料繫結相關的介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a0e48ddc6f74d3c4e030bc953ac4f853660a00d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="interfaces-related-to-data-binding"></a>與資料繫結相關的介面
透過 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]，您可以建立許多不同的資料結構，以滿足您正在使用之應用程式和資料的繫結需求。 您或許會想要建立自有類別以在 Windows Forms 中提供或取用資料。 這些物件可以提供不同程度的功能和複雜度，從基本的資料繫結，到提供設計階段支援、錯誤檢查、變更通知，或甚至對資料本身所做變更的結構化回復支援。  
  
## <a name="consumers-of-data-binding-interfaces"></a>資料繫結介面的取用者  
 下列幾節會說明兩個群組的介面物件。 第一個群組所列出的介面會由資料來源作者實作到資料來源上。 這些介面是設計來供資料來源取用者取用，而在大部分情況下，這些取用者就是 Windows Forms 控制項或元件。 第二個群組所列出的介面則是設計來供元件作者使用。 元件作者在建立可支援資料繫結的元件以供 Windows Forms 資料繫結引擎取用時，就會使用這些介面。 您可以在與表單相關聯的類別內實作這些介面，以啟用資料繫結；下列每個案例都會提出一個類別，該類別會實作可與資料互動的介面。 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 快速應用程式開發 (RAD) 的資料設計體驗工具已利用這項功能。  
  
### <a name="interfaces-for-implementation-by-data-source-authors"></a>可供資料來源作者實作的介面  
 下列介面是設計來供 Windows Forms 控制項取用︰  
  
-   <xref:System.Collections.IList>介面  
  
     類別可實作<xref:System.Collections.IList>介面可能是<xref:System.Array>， <xref:System.Collections.ArrayList>，或<xref:System.Collections.CollectionBase>。 這些是項目類型的索引的清單<xref:System.Object>。 這些清單必須包含同質型別，因為此索引的第一個項目會決定其型別。 <xref:System.Collections.IList>就可以使用只能在執行階段的繫結。  
  
    > [!NOTE]
    >  如果您想要利用 Windows Form 中建立商務物件繫結的清單，您應該考慮使用<xref:System.ComponentModel.BindingList%601>。 <xref:System.ComponentModel.BindingList%601>是一種可延伸的類別，實作雙向 Windows Form 資料繫結所需的主要介面。  
  
-   <xref:System.ComponentModel.IBindingList>介面  
  
     類別可實作<xref:System.ComponentModel.IBindingList>介面會提供更高層級的資料繫結功能。 此實作可提供您基本的排序功能和變更通知，讓您在清單項目變更時 (例如，客戶清單的第三個項目變更了 [位址] 欄位) 以及在清單本身變更時 (例如，清單的項目數增加或減少) 使用。 如果您打算讓多個控制項繫結至相同資料，並想要讓其中一個控制項的資料變更傳播到其他繫結控制項，變更通知就很重要。  
  
    > [!NOTE]
    >  已啟用變更通知<xref:System.ComponentModel.IBindingList>介面透過<xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A>屬性的當`true`，引發<xref:System.ComponentModel.IBindingList.ListChanged>變更事件，指出變更的清單中的項目。  
  
     所描述的變更類型<xref:System.ComponentModel.ListChangedType>屬性<xref:System.ComponentModel.ListChangedEventArgs>參數。 因此，每當資料模型更新時，所有相依的檢視 (例如其他繫結至相同資料來源的控制項) 也會隨之更新。 不過，清單中包含的物件必須隨之變更，以便可以引發清單時，通知清單<xref:System.ComponentModel.IBindingList.ListChanged>事件。  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BindingList%601>提供的泛型實作<xref:System.ComponentModel.IBindingList>介面。  
  
-   <xref:System.ComponentModel.IBindingListView>介面  
  
     類別可實作<xref:System.ComponentModel.IBindingListView>介面提供的實作的所有功能<xref:System.ComponentModel.IBindingList>，以及為篩選和進階排序功能。 此實作可提供以字串為基礎的篩選功能，以及利用屬性描述元與方向配對來進行的多欄排序功能。  
  
-   <xref:System.ComponentModel.IEditableObject>介面  
  
     類別可實作<xref:System.ComponentModel.IEditableObject>介面可讓要控制時進行永久變更，該物件的物件。 這項實作帶給您<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>， <xref:System.ComponentModel.IEditableObject.EndEdit%2A>，和<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>方法，可讓您復原物件所做的變更。 以下是的運作的簡短說明<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>， <xref:System.ComponentModel.IEditableObject.EndEdit%2A>，和<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>方法，以及它們如何彼此啟用資料所做的變更可能回復搭配：  
  
    -   <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>方法發出訊號的物件上開始編輯。 實作這個介面的物件必須儲存任何更新之後<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>方法呼叫的方式更新，可捨棄如果<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>方法呼叫。 在資料繫結 Windows Form，您可以呼叫<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>多次範圍內的單一編輯交易 (例如， <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>， <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>， <xref:System.ComponentModel.IEditableObject.EndEdit%2A>)。 實作<xref:System.ComponentModel.IEditableObject>應該追蹤是否<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>已經呼叫，並忽略後續呼叫<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>。 可以多次呼叫這個方法，因為它是很重要的後續呼叫會恢復。也就是說，後續<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>呼叫無法終結已進行，或變更已儲存的資料在第一個<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>呼叫。  
  
    -   <xref:System.ComponentModel.IEditableObject.EndEdit%2A>方法推入後的任何變更<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>物件目前處於編輯模式，如果呼叫的基礎物件中。  
  
    -   <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>方法會捨棄任何物件所做的變更。  
  
     如需有關如何<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>， <xref:System.ComponentModel.IEditableObject.EndEdit%2A>，和<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>方法運作，請參閱[將資料儲存回資料庫](/visualstudio/data-tools/save-data-back-to-the-database)。  
  
     資料功能的這個交易的概念由<xref:System.Windows.Forms.DataGridView>控制項。  
  
-   <xref:System.ComponentModel.ICancelAddNew>介面  
  
     類別可實作<xref:System.ComponentModel.ICancelAddNew>介面通常會實作<xref:System.ComponentModel.IBindingList>介面，並可讓您復原的資料來源所做的額外<xref:System.ComponentModel.IBindingList.AddNew%2A>方法。 如果您的資料來源實作<xref:System.ComponentModel.IBindingList>介面，您也應該擁有它實作<xref:System.ComponentModel.ICancelAddNew>介面。  
  
-   <xref:System.ComponentModel.IDataErrorInfo>介面  
  
     類別可實作<xref:System.ComponentModel.IDataErrorInfo>介面可讓物件提供自訂的錯誤繫結控制項的資訊：  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Error%2A>屬性會傳回一般錯誤訊息文字 （例如，「 已發生錯誤 」）。  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Item%2A>屬性會傳回具有特定錯誤訊息的字串資料行 (例如，"中的值`State`資料行無效 」)。  
  
-   <xref:System.Collections.IEnumerable>介面  
  
     類別可實作<xref:System.Collections.IEnumerable>介面通常由[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]。 僅可透過此介面的 Windows Form 支援<xref:System.Windows.Forms.BindingSource>元件。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource>元件會複製所有<xref:System.Collections.IEnumerable>成個別的清單，供繫結使用的項目。  
  
-   <xref:System.ComponentModel.ITypedList>介面  
  
     實作的集合類別<xref:System.ComponentModel.ITypedList>介面提供了可控制公開至繫結控制項的屬性集和順序。  
  
    > [!NOTE]
    >  當您實作<xref:System.ComponentModel.ITypedList.GetItemProperties%2A>方法，而<xref:System.ComponentModel.PropertyDescriptor>陣列不是 null，陣列中的最後一個項目會描述為另一個項目清單的清單屬性的屬性描述元。  
  
-   <xref:System.ComponentModel.ICustomTypeDescriptor>介面  
  
     類別可實作<xref:System.ComponentModel.ICustomTypeDescriptor>介面提供與其本身相關的動態資訊。 這個介面是類似於<xref:System.ComponentModel.ITypedList>，但用於物件，而不是清單。 這個介面由<xref:System.Data.DataRowView>加入專案的結構描述的基礎資料列。 簡單實作<xref:System.ComponentModel.ICustomTypeDescriptor>係由<xref:System.ComponentModel.CustomTypeDescriptor>類別。  
  
    > [!NOTE]
    >  若要支援設計階段繫結至型別都會實作<xref:System.ComponentModel.ICustomTypeDescriptor>，型別也必須實作<xref:System.ComponentModel.IComponent>，做為表單上的執行個體存在。  
  
-   <xref:System.ComponentModel.IListSource>介面  
  
     類別可實作<xref:System.ComponentModel.IListSource>介面可讓非 list 物件上的清單架構繫結。 <xref:System.ComponentModel.IListSource.GetList%2A>方法<xref:System.ComponentModel.IListSource>用來傳回可繫結的清單不是繼承自 object <xref:System.Collections.IList>。 <xref:System.ComponentModel.IListSource>正由<xref:System.Data.DataSet>類別。  
  
-   <xref:System.ComponentModel.IRaiseItemChangedEvents>介面  
  
     類別可實作<xref:System.ComponentModel.IRaiseItemChangedEvents>介面是以可繫結的清單，也會實作<xref:System.ComponentModel.IBindingList>介面。 這個介面用來表示是否您的型別就會引發<xref:System.ComponentModel.IBindingList.ListChanged>類型的事件<xref:System.ComponentModel.ListChangedType.ItemChanged>透過其<xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A>屬性。  
  
    > [!NOTE]
    >  您應該實作<xref:System.ComponentModel.IRaiseItemChangedEvents>如果資料來源提供先前所述的清單事件轉換成該屬性，而在互動<xref:System.Windows.Forms.BindingSource>元件。 否則，<xref:System.Windows.Forms.BindingSource>也會導致效能變慢的清單事件轉換成屬性。  
  
-   <xref:System.ComponentModel.ISupportInitialize>介面  
  
     實作的元件<xref:System.ComponentModel.ISupportInitialize>介面會設定屬性和初始化共同相依的屬性批次最佳化的優點。 <xref:System.ComponentModel.ISupportInitialize>包含兩個方法：  
  
    -   <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A>表示正在啟動該物件初始設定。  
  
    -   <xref:System.ComponentModel.ISupportInitialize.EndInit%2A>表示已完成的物件初始設定。  
  
-   <xref:System.ComponentModel.ISupportInitializeNotification>介面  
  
     實作的元件<xref:System.ComponentModel.ISupportInitializeNotification>介面也會實作<xref:System.ComponentModel.ISupportInitialize>介面。 這個介面可讓您通知其他<xref:System.ComponentModel.ISupportInitialize>元件初始化已完成。 <xref:System.ComponentModel.ISupportInitializeNotification>介面包含兩個成員：  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A>傳回`boolean`值，指出元件是否已初始化。  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.Initialized>發生時<xref:System.ComponentModel.ISupportInitialize.EndInit%2A>呼叫。  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged>介面  
  
     類別若實作此介面，代表其所屬的型別會在其任何屬性值變更時引發事件。 對於會讓控制項的每個屬性有一個變更事件的模式，我們設計了此介面來加以取代。 當用於<xref:System.ComponentModel.BindingList%601>，應實作商務物件<xref:System.ComponentModel.INotifyPropertyChanged>介面和 BindingList\`1 會將轉換<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>事件<xref:System.ComponentModel.BindingList%601.ListChanged>類型的事件<xref:System.ComponentModel.ListChangedType.ItemChanged>。  
  
    > [!NOTE]
    >  變更通知會出現在 繫結的用戶端和資料之間的繫結來源繫結的資料來源類型應該是實作<xref:System.ComponentModel.INotifyPropertyChanged>介面 （慣用） 或您可以提供*propertyName* `Changed`事件繫結的型別，但是您不應該執行。  
  
### <a name="interfaces-for-implementation-by-component-authors"></a>可供元件作者實作的介面  
 下列介面是設計來供 Windows Forms 資料繫結引擎取用︰  
  
-   <xref:System.Windows.Forms.IBindableComponent>介面  
  
     類別若實作此介面，就是可支援資料繫結的非控制項元件。 這個類別會傳回的資料繫結和繫結內容的元件透過<xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>和<xref:System.Windows.Forms.IBindableComponent.BindingContext%2A>此介面的屬性。  
  
    > [!NOTE]
    >  如果您的元件繼承自<xref:System.Windows.Forms.Control>，您不需要實作<xref:System.Windows.Forms.IBindableComponent>介面。  
  
-   <xref:System.Windows.Forms.ICurrencyManagerProvider>介面  
  
     類別可實作<xref:System.Windows.Forms.ICurrencyManagerProvider>介面會提供自己的元件<xref:System.Windows.Forms.CurrencyManager>來管理此特定元件相關聯的繫結。 存取自訂<xref:System.Windows.Forms.CurrencyManager>係由<xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>屬性。  
  
    > [!NOTE]
    >  類別繼承自<xref:System.Windows.Forms.Control>管理繫結會自動透過其<xref:System.Windows.Forms.Control.BindingContext%2A>屬性，這樣的情況下，需要實作<xref:System.Windows.Forms.ICurrencyManagerProvider>都相當少見。  
  
## <a name="see-also"></a>請參閱  
 [資料繫結和 Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [操作說明：在 Windows Forms 上建立簡單繫結控制項](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [Windows Forms 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)
