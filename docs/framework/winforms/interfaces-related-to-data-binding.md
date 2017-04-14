---
title: "與資料繫結相關的介面 | Microsoft Docs"
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
  - "資料 [Windows Form], 資料繫結介面"
  - "資料繫結, 介面"
  - "IBindingList 介面, Windows Form 資料繫結"
  - "IBindingListView 介面"
  - "IDataErrorInfo 介面, Windows Form 資料繫結"
  - "IEditableObject 介面, Windows Form 資料繫結"
  - "IList 介面, Windows Form 資料繫結"
  - "INotifyPropertyChanged 介面"
  - "介面, Windows Form 資料繫結"
ms.assetid: 14e49a2e-3e46-47ca-b491-70d546333277
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# 與資料繫結相關的介面
使用 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]，您可以建立許多不同的資料結構，以滿足應用程式和您所使用資料的繫結需求。  您可能會想建立自己的類別來提供或使用 Windows Form 中的資料。  這些物件能提供不同層次的功能和複雜度，從基本資料繫結到提供設計階段支援、錯誤檢查、變更告知，甚至對資料本身的變更提供結構性復原。  
  
## 資枓繫結介面的消費者  
 下列章節將說明介面物件的兩個群組。  第一個群組所列出的介面是由資料來源的作者在資料來源上實作。  這些介面是設計給資料來源的消費者使用，在大部分情況下是 Windows Form 控制項或元件。  第二個群組所列出的介面是由元件作者為使用者所設計。  當元件作者要建立一個支援資料繫結的元件給 Windows Form 的資料繫結引擎使用時，他們會使用這些介面。  您可以在與表單關聯的類別中實作這些介面來啟用資料繫結；每個案例所呈現的類別，都實作可與資料互動的介面。  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 的快速應用程式開發 \(Rapid Application Development，RAD\) 資料設計經驗工具已經充分利用這個功能的優點。  
  
### 由資料來源作者實作的介面  
 下列介面是設計給 Windows Form 的控制項使用：  
  
-   <xref:System.Collections.IList> 介面  
  
     實作 <xref:System.Collections.IList> 介面的類別可以是 <xref:System.Array>、<xref:System.Collections.ArrayList> 或 <xref:System.Collections.CollectionBase>。  這些是 <xref:System.Object> 型別的項目之索引清單。  這些清單必須包含同質性型別，因為索引的第一個項目就決定了清單的型別。  <xref:System.Collections.IList> 只能在執行階段繫結。  
  
    > [!NOTE]
    >  如果您想要建立一個商務物件的清單來與 Windows Form 繫結，您應該考慮使用 <xref:System.ComponentModel.BindingList%601>。  <xref:System.ComponentModel.BindingList%601> 是一個用來實作雙向 Windows Form 資料繫結所需之主要介面的擴充類別。  
  
-   <xref:System.ComponentModel.IBindingList> 介面  
  
     實作 <xref:System.ComponentModel.IBindingList> 介面的類別，提供了更高層級的資料繫結功能。  這個實作所提供的基本排序功能和變更告知，可用於清單項目變更時 \(例如，客戶清單的第三個項目變更了地址欄的內容\)，也可用於清單本身變更時 \(例如，清單項目的數量增加\/減少\)。  如果您打算將多個控制項繫結至相同的資料，而且您希望在其中一個控制項所做的資料變更能傳播到其他繫結控制項，變更告知就變得很重要。  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.IBindingList> 介面的變更告知可藉由設定 <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> 屬性來啟用，而當屬性值為 `true` 時，就會引發 <xref:System.ComponentModel.IBindingList.ListChanged> 事件，指出清單變更或清單中的項目變更。  
  
     變更類型是由 <xref:System.ComponentModel.ListChangedEventArgs> 參數的 <xref:System.ComponentModel.ListChangedType> 屬性所描述。  因此，只要資料模型更新，所有相依的檢視 \(例如其他繫結至相同資料來源的控制項\) 也會隨之更新。  然而，包含於清單中的物件在發生變更時必須通知清單，以便讓清單引發 <xref:System.ComponentModel.IBindingList.ListChanged> 事件。  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BindingList%601> 提供了 <xref:System.ComponentModel.IBindingList> 介面的泛用實作。  
  
-   <xref:System.ComponentModel.IBindingListView> 介面  
  
     實作 <xref:System.ComponentModel.IBindingListView> 介面的類別可提供 <xref:System.ComponentModel.IBindingList> 實作的所有功能，以及篩選和進階排序的功能。  這種實作提供了字串架構的篩選，並透過屬性描述項方向配對來提供多資料行排序。  
  
-   <xref:System.ComponentModel.IEditableObject> 介面  
  
     實作 <xref:System.ComponentModel.IEditableObject> 介面的類別，當物件遭遇永久性變更時，允許該物件控制。  這項實作讓您擁有 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、<xref:System.ComponentModel.IEditableObject.EndEdit%2A> 和 <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> 方法，它們使您可以復原對物件所做的變更。  以下為 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、<xref:System.ComponentModel.IEditableObject.EndEdit%2A> 和 <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> 方法的簡短說明，以及如何將它們搭配使用以復原對資料所做的變更：  
  
    -   <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> 發出信號告知開始對物件編輯。  實作這個介面的物件必須儲存 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> 方法呼叫之後的任何更新，並必須在 <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> 方法被呼叫時，將更新捨棄。  在資料繫結  Windows Form 時，您可以在單次編輯異動中多次呼叫 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> \(例如：<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、<xref:System.ComponentModel.IEditableObject.EndEdit%2A>\)。  <xref:System.ComponentModel.IEditableObject> 的實作應該追蹤是否已呼叫 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>，並忽略對 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> 的後續呼叫。  由於本方法可被多次呼叫，所以後續對它的呼叫必須為非破壞性的，也就是說，後續的 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> 呼叫不可破壞已完成的更新，或變更第一次呼叫 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> 時儲存的資料。  
  
    -   <xref:System.ComponentModel.IEditableObject.EndEdit%2A> 方法會將 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> 呼叫後所發生的任何變更推入目前物件 \(如果該物件目前正處於編輯模式\)。  
  
    -   <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> 方法會捨棄任何對物件所做的變更。  
  
     如需 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、<xref:System.ComponentModel.IEditableObject.EndEdit%2A> 和 <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> 方法如何運作的詳細資訊，請參閱 [儲存資料集中的資料](../Topic/Save%20data%20back%20to%20the%20database.md)。  
  
     這種資料功能異動的概念應用於 <xref:System.Windows.Forms.DataGridView> 控制項中。  
  
-   <xref:System.ComponentModel.ICancelAddNew> 介面  
  
     實作 <xref:System.ComponentModel.ICancelAddNew> 介面的類別通常也會實作 <xref:System.ComponentModel.IBindingList> 介面，並允許您使用 <xref:System.ComponentModel.IBindingList.AddNew%2A> 方法來復原對資料所做的一個額外變更。  如果您的資料來源實作了 <xref:System.ComponentModel.IBindingList> 介面，您也應該要實作 <xref:System.ComponentModel.ICancelAddNew> 介面。  
  
-   <xref:System.ComponentModel.IDataErrorInfo> 介面  
  
     實作 <xref:System.ComponentModel.IDataErrorInfo> 介面的類別可允許物件提供自訂錯誤訊息給繫結的控制項：  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Error%2A> 屬性會傳回一般性的錯誤訊息文字 \(例如：「發生錯誤」\)。  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Item%2A> 屬性會傳回字串，其中包含來自資料行的特定錯誤訊息 \(例如，「在 `State`  資料行中的值無效」\)。  
  
-   <xref:System.Collections.IEnumerable> 介面  
  
     實作 <xref:System.Collections.IEnumerable> 介面的屬性通常會由 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 使用。  這個介面的 Windows Form 支援只能透過 <xref:System.Windows.Forms.BindingSource> 元件來達成。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource> 元件會將所有 <xref:System.Collections.IEnumerable> 項目複製到一個單獨的清單中以供繫結使用。  
  
-   <xref:System.ComponentModel.ITypedList> 介面  
  
     實作 <xref:System.ComponentModel.ITypedList> 介面的集合類別可提供控制順序以及公開 \(Expose\) 給繫結控制項的屬性組之能力。  
  
    > [!NOTE]
    >  當您實作了 <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> 方法，而且 <xref:System.ComponentModel.PropertyDescriptor> 陣列不是 null 時，陣列中的最後一個項目會是描述 list 屬性 \(另一個項目清單\) 的屬性描述項。  
  
-   <xref:System.ComponentModel.ICustomTypeDescriptor> 介面  
  
     實作 <xref:System.ComponentModel.ICustomTypeDescriptor> 介面的類別可提供該類別本身的動態資訊。  這個介面與 <xref:System.ComponentModel.ITypedList> 類似，但是使用於物件而不是清單。  <xref:System.Data.DataRowView> 使用此介面來呈現基礎資料列的結構描述。  <xref:System.ComponentModel.CustomTypeDescriptor> 類別提供了一個 <xref:System.ComponentModel.ICustomTypeDescriptor> 的簡單實作。  
  
    > [!NOTE]
    >  若要支援在設計階段繫結至實作 <xref:System.ComponentModel.ICustomTypeDescriptor> 的型別，型別必須同時實作 <xref:System.ComponentModel.IComponent>，而且在表單中以執行個體形式存在。  
  
-   <xref:System.ComponentModel.IListSource> 介面  
  
     實作 <xref:System.ComponentModel.IListSource> 介面的類別可在非清單物件上啟用清單架構繫結。  <xref:System.ComponentModel.IListSource> 的 <xref:System.ComponentModel.IListSource.GetList%2A> 方法可用來從不是繼承自 <xref:System.Collections.IList> 的物件傳回可繫結清單。  <xref:System.ComponentModel.IListSource> 是由 <xref:System.Data.DataSet> 類別所使用。  
  
-   <xref:System.ComponentModel.IRaiseItemChangedEvents> 介面  
  
     實作 <xref:System.ComponentModel.IRaiseItemChangedEvents> 介面的類別是一個同時實作 <xref:System.ComponentModel.IBindingList> 介面的可繫結清單。  如果您的型別透過其 <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> 屬性引發 <xref:System.ComponentModel.ListChangedType> 型別的 <xref:System.ComponentModel.IBindingList.ListChanged> 事件，會使用這個介面來指示。  
  
    > [!NOTE]
    >  如果您的資料來源提供前面所述的屬性，可列出事件的轉換，而且資料來源會與 <xref:System.Windows.Forms.BindingSource> 元件互動，您就應該實作 <xref:System.ComponentModel.IRaiseItemChangedEvents>。  否則 <xref:System.Windows.Forms.BindingSource> 也將執行屬性以列出事件轉換，這會造成效能低落。  
  
-   <xref:System.ComponentModel.ISupportInitialize> 介面  
  
     實作 <xref:System.ComponentModel.ISupportInitialize> 介面的元件會利用批次最佳化來設定屬性和初始化相依的屬性。  <xref:System.ComponentModel.ISupportInitialize> 包含兩個方法：  
  
    -   <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> 會發出物件初始化正在啟動的信號。  
  
    -   <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> 會發出物件初始化正要完成的信號。  
  
-   <xref:System.ComponentModel.ISupportInitializeNotification> 介面  
  
     實作 <xref:System.ComponentModel.ISupportInitializeNotification> 介面的元件也會同時實作 <xref:System.ComponentModel.ISupportInitialize> 介面。  這個介面允許您通知其他 <xref:System.ComponentModel.ISupportInitialize> 元件初始化已完成。  <xref:System.ComponentModel.ISupportInitializeNotification> 介面包含兩個成員：  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> 傳回一個 `boolean` 值，指示元件是否已初始化。  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> 會在 <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> 被呼叫時出現。  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged> 介面  
  
     實作這個介面的類別是一個型別，會在其任何屬性值變更時引發事件。  這個介面的設計目的，是要取代在控制項的每個屬性中都有變更事件的這種模式。  當在 <xref:System.ComponentModel.BindingList%601> 中使用時，商務物件應該實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，而 BindingList\`1 則會將 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件轉換成 <xref:System.ComponentModel.ListChangedType> 型別的 <xref:System.ComponentModel.BindingList%601.ListChanged> 事件。  
  
    > [!NOTE]
    >  .若要讓變更告知出現在受繫結之用戶端與資料來源之間的繫結上，繫結的資料來源型別應該要實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面 \(優先使用\)，或是您要提供 *propertyName*`Changed` 事件給繫結的型別，但請勿同時採用這兩種方式。  
  
### 由元件作者實作的介面  
 下列介面是設計給 Windows Form 的資料繫結引擎使用：  
  
-   <xref:System.Windows.Forms.IBindableComponent> 介面  
  
     實作這個介面的類別是一個支援資料繫結的非控制項元件。  這個類別會透過這個介面的  <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> 和 <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> 屬性，傳回資料繫結和元件中的繫結內容。  
  
    > [!NOTE]
    >  如果元件繼承自 <xref:System.Windows.Forms.Control>，您就不需要實作 <xref:System.Windows.Forms.IBindableComponent> 介面。  
  
-   <xref:System.Windows.Forms.ICurrencyManagerProvider> 介面  
  
     實作 <xref:System.Windows.Forms.ICurrencyManagerProvider> 介面的類別是一個元件，會提供自身的 <xref:System.Windows.Forms.CurrencyManager> 來管理與這個特定元件關聯的繫結。  藉由 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> 屬性提供對自訂 <xref:System.Windows.Forms.CurrencyManager> 的存取權限。  
  
    > [!NOTE]
    >  繼承自 <xref:System.Windows.Forms.Control> 的類別會自動透過其 <xref:System.Windows.Forms.Control.BindingContext%2A> 屬性來管理繫結，所以您需要實作 <xref:System.Windows.Forms.ICurrencyManagerProvider> 的情況微乎其微。  
  
## 請參閱  
 [資料繫結和 Windows Form](../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [如何：在 Windows Form 上建立簡單繫結控制項](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)   
 [Windows Form 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)