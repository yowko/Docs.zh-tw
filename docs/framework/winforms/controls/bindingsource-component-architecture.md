---
title: "BindingSource 元件架構 | Microsoft Docs"
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
  - "BindingSource 元件 [Windows Form], 關於 BindingSource 元件"
  - "BindingSource 元件, 架構"
  - "資料繫結, BindingSource 元件"
  - "Windows Form, 資料繫結"
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# BindingSource 元件架構
透過 <xref:System.Windows.Forms.BindingSource> 元件，您可以將所有的 Windows Form 控制項全部繫結至資料來源。  
  
 <xref:System.Windows.Forms.BindingSource> 元件簡化了將控制項繫結至資料來源的程序，同時提供了優於舊式資料繫結的下列各項特點：  
  
-   可以讓商務物件 \(Business Object\) 使用設計階段繫結。  
  
-   可以在設計階段封裝 <xref:System.Windows.Forms.CurrencyManager> 功能和公開 \(Expose\) <xref:System.Windows.Forms.CurrencyManager> 事件。  
  
-   藉由為原本不支援清單變更告知的資料來源，提供清單變更告知功能，可以簡化支援 <xref:System.ComponentModel.IBindingList> 介面的清單建立程序。  
  
-   為 <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=fullName> 方法提供了擴充性點。  
  
-   在資料來源和控制項之間提供了間接取值 \(Indirection\) 層級。  當資料來源可以在執行階段變更時，間接取值非常重要。  
  
-   可以與其他資料相關的 Windows Form 控制項 \(特別是 <xref:System.Windows.Forms.BindingNavigator> 和 <xref:System.Windows.Forms.DataGridView> 控制項\) 相互操作。  
  
 基於這些理由，<xref:System.Windows.Forms.BindingSource> 元件是當您將 Windows Form 控制項繫結至資料來源時的慣用方式。  
  
## BindingSource 功能  
 <xref:System.Windows.Forms.BindingSource> 元件提供了數種可將控制項繫結至資料的功能。  利用這些功能，幾乎不太需要撰寫程式碼，就可以實作大部分的資料繫結案例。  
  
 <xref:System.Windows.Forms.BindingSource> 元件藉由提供一致的介面做為存取各種不同資料來源之用，即可完成此項工作。  這意味著不論是繫結至何種型別，都是使用相同的程序。  例如，可以將 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 屬性附加至 <xref:System.Data.DataSet> 或商務物件。這兩種情況都是使用同一組屬性、方法和事件來管理資料來源。  
  
 <xref:System.Windows.Forms.BindingSource> 元件所提供的一致介面大幅簡化了資料至控制項的繫結程序。  對於提供變更告知的資料來源型別，<xref:System.Windows.Forms.BindingSource> 元件會自動在控制項與資料來源之間傳遞變更。  對於不提供變更告知的資料來源型別，會提供可讓您引發變更告知的事件。  下列是 <xref:System.Windows.Forms.BindingSource> 元件支援的功能：  
  
-   間接取值。  
  
-   功能轉換管理。  
  
-   資料來源做為清單。  
  
-   <xref:System.Windows.Forms.BindingSource> 做為 <xref:System.ComponentModel.IBindingList>。  
  
-   建立自訂項目。  
  
-   建立異動項目。  
  
-   <xref:System.Collections.IEnumerable> 支援。  
  
-   設計階段支援。  
  
-   靜態 <xref:System.Windows.Forms.ListBindingHelper> 方法。  
  
-   使用 <xref:System.ComponentModel.IBindingListView> 介面進行排序和篩選。  
  
-   使用 <xref:System.Windows.Forms.BindingNavigator> 進行整合。  
  
### 間接  
 <xref:System.Windows.Forms.BindingSource> 元件在資料來源和控制項之間，提供了可以進行間接取值的層級。  您不是將控制項直接繫結至資料來源，而是先將控制項繫結至 <xref:System.Windows.Forms.BindingSource>，然後再將資料來源附加至 <xref:System.Windows.Forms.BindingSource> 元件的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 屬性。  
  
 利用這個間接取值層級，您不需要重新設定控制項繫結即可變更資料來源，  因而能夠：  
  
-   將 <xref:System.Windows.Forms.BindingSource> 附加至不同的資料來源，而且同時又能保留目前的控制項繫結。  
  
-   變更資料來源中的項目，然後告知繫結控制項。  如需詳細資訊，請參閱 [如何：使用 BindingSource 反映 Windows Form 控制項中的資料來源更新](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)。  
  
-   可以繫結至 <xref:System.Type>，而不是記憶體中的物件。  如需詳細資訊，請參閱 [如何：將 Windows Form 控制項繫結至類型](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)。  接著可以在執行階段繫結至物件。  
  
### 貨幣管理  
 <xref:System.Windows.Forms.BindingSource> 元件會實作 <xref:System.Windows.Forms.ICurrencyManagerProvider> 介面，來為您處理貨幣管理。  透過 <xref:System.Windows.Forms.ICurrencyManagerProvider> 介面，除了其他繫結至相同 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 之 <xref:System.Windows.Forms.BindingSource> 的 Currency 管理員以外，您還可以存取 <xref:System.Windows.Forms.BindingSource> 的 Currency 管理員。  
  
 <xref:System.Windows.Forms.BindingSource> 元件可封裝 <xref:System.Windows.Forms.CurrencyManager> 功能和公開最常用的 <xref:System.Windows.Forms.CurrencyManager> 屬性和事件。  下表說明部分與貨幣管理相關的成員。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> 屬性  
 取得與 <xref:System.Windows.Forms.BindingSource> 關聯的 Currency 管理員。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A> 方法  
 如果有其他 <xref:System.Windows.Forms.BindingSource> 繫結至指定的資料成員，則取得它的 Currency 管理員。  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A> 屬性  
 取得資料來源的目前項目。  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A> 屬性  
 取得或設定基礎清單中的目前位置。  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 方法  
 將暫止的變更套用至基礎資料來源。  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> 方法  
 取消目前的編輯作業。  
  
### 資料來源做為清單。  
 <xref:System.Windows.Forms.BindingSource> 元件可實作 <xref:System.ComponentModel.IBindingListView> 和 <xref:System.ComponentModel.ITypedList> 介面。  利用這個實作，您不需要任何外部儲存體即可將 <xref:System.Windows.Forms.BindingSource> 元件本身當做資料來源使用。  
  
 當 <xref:System.Windows.Forms.BindingSource> 元件附加至資料來源時，它會將資料來源公開為清單。  
  
 您可以將 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 屬性設定為數種資料來源，  包括型別、物件和型別清單。  產生的資料來源將公開為清單。  下表顯示部分的通用資料來源以及產生的清單評估。  
  
|DataSource 屬性|列出結果|  
|-------------------|----------|  
|null 參考 \(在 Visual Basic 中為 `Nothing`\)|物件的空 <xref:System.ComponentModel.IBindingList>。  藉由加入項目即可將清單設為已加入之項目的型別。|  
|含有 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 集合的 null 參考 \(在 Visual Basic 中為 `Nothing`\)|不支援，會引發 <xref:System.ArgumentException>。|  
|非清單型別或 型別 "T" 的物件|"T" 型別的空 <xref:System.ComponentModel.IBindingList>。|  
|陣列執行個體|包含陣列項目的 <xref:System.ComponentModel.IBindingList>。|  
|<xref:System.Collections.IEnumerable> 執行個體|包含 <xref:System.Collections.IEnumerable> 項目的 <xref:System.ComponentModel.IBindingList>|  
|包含 "T" 型別的清單執行個體|包含 "T" 型別的 <xref:System.ComponentModel.IBindingList>。|  
  
 此外，也可以將 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 設定為其他清單型別 \(例如 <xref:System.ComponentModel.IListSource> 和 <xref:System.ComponentModel.ITypedList>\)，並且將由 <xref:System.Windows.Forms.BindingSource> 適當地處理這些型別。  在這種情況下，清單中所包含的型別應該要有預設的建構函式。  
  
### BindingSource 做為 IBindingList  
 <xref:System.Windows.Forms.BindingSource> 元件提供存取和管理基礎資料的成員做為 <xref:System.ComponentModel.IBindingList>。  下表說明這些成員中的一部分。  
  
|成員|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.BindingSource.List%2A> 屬性|取得經由評估 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 或 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性而得到的清單。|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> 方法|將新的項目加入至基礎清單中。  套用至實作 <xref:System.ComponentModel.IBindingList> 介面的資料來源 \(也就是將 <xref:System.Windows.Forms.BindingSource.AllowNew%2A> 屬性設為 `true`\)。|  
  
### 建立自訂項目。  
 您可以處理 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件以提供自己的項目建立邏輯。  在 <xref:System.Windows.Forms.BindingSource> 加入新物件之前會發生 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件。  這個事件是發生於呼叫 <xref:System.Windows.Forms.BindingSource.AddNew%2A> 方法之後，但基礎清單加入新項目之前。  藉由處理這個事件，不需從 <xref:System.Windows.Forms.BindingSource> 類別衍生即可提供建立自訂項目行為。  如需詳細資訊，請參閱 [如何：使用 Windows Form BindingSource 自訂加入項目](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)。  
  
### 建立異動項目。  
 <xref:System.Windows.Forms.BindingSource> 元件可實作 <xref:System.ComponentModel.ICancelAddNew> 介面，此介面可建立異動項目。  隨著呼叫 <xref:System.Windows.Forms.BindingSource.AddNew%2A> 而暫時建立了新項目之後，這個加入項目的動作可利用下列方式加以認可或復原：  
  
-   <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> 方法會明確認可這項暫止的加入動作。  
  
-   執行其他集合作業 \(例如插入、移除或移動\) 即隱含認可這項暫止的加入動作。  
  
-   <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> 方法會復原暫止的加入動作 \(如果此方法尚未經過認可的話\)。  
  
### IEnumerable 支援  
 <xref:System.Windows.Forms.BindingSource> 元件可將控制項繫結至 <xref:System.Collections.IEnumerable> 資料來源。  利用這個元件，可繫結至資料來源 \(例如 <xref:System.Data.SqlClient.SqlDataReader?displayProperty=fullName>\)。  
  
 當 <xref:System.Collections.IEnumerable> 資料來源指派給 <xref:System.Windows.Forms.BindingSource> 元件時，<xref:System.Windows.Forms.BindingSource> 會建立 <xref:System.ComponentModel.IBindingList> 並將 <xref:System.Collections.IEnumerable> 資料來源的內容加入至清單。  
  
### 設計階段支援  
 有些物件型別無法在設計階段建立，例如，建立自 Factory 類別的物件或是由 Web 服務傳回的物件。  有時候，您可能必須在設計階段將控制項繫結至這些型別，即使記憶體中並沒有控制項可以繫結的物件。  例如，此時可能必須使用自訂型別的公用屬性名稱來標記 <xref:System.Windows.Forms.DataGridView> 控制項的資料行行首。  
  
 為了支援這樣的案例，<xref:System.Windows.Forms.BindingSource> 元件將會支援繫結至 <xref:System.Type>。  當您將 <xref:System.Type> 指派給 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 屬性時，<xref:System.Windows.Forms.BindingSource> 元件會建立 <xref:System.Type> 項目的空 <xref:System.ComponentModel.BindingList%601>。  如果型別的屬性或結構描述在設計階段或執行階段中出現，那麼後續繫結至 <xref:System.Windows.Forms.BindingSource> 元件的所有控制項都將會收到警示。  如需詳細資訊，請參閱 [如何：將 Windows Form 控制項繫結至類型](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)。  
  
### 靜態 ListBindingHelper 方法  
 <xref:System.Windows.Forms.BindingContext?displayProperty=fullName>、<xref:System.Windows.Forms.CurrencyManager?displayProperty=fullName> 和 <xref:System.Windows.Forms.BindingSource> 型別都共用一般邏輯，藉此從成對的 `DataSource`\/`DataMember` 組合產生清單。  此外，這個通用邏輯會透過下列 `static` 方法進行公開，以供控制項作者和其他協力廠商使用：  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### 使用 IBindingListView 介面進行排序和篩選。  
 <xref:System.Windows.Forms.BindingSource> 元件可實作 <xref:System.ComponentModel.IBindingListView> 介面，而此介面可延伸 <xref:System.ComponentModel.IBindingList> 介面。  <xref:System.ComponentModel.IBindingList> 提供單一資料行排序，而 <xref:System.ComponentModel.IBindingListView> 則提供進階排序和篩選。  如果資料來源也會實作其中一個介面，您可以使用 <xref:System.ComponentModel.IBindingListView> 來排序和篩選資料來源中的項目。  <xref:System.Windows.Forms.BindingSource> 元件並不提供這些成員的參考實作。  而呼叫會轉送到底層清單。  
  
 下表說明在排序和篩選時所使用的屬性。  
  
|成員|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> 屬性|如果資料來源是 <xref:System.ComponentModel.IBindingListView>，則可取得或設定運算式，此運算式是用於篩選檢視中的資料列。|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> 屬性|如果資料來源是 <xref:System.ComponentModel.IBindingList>，則可取得或設定資料行名稱，此資料行名稱是用於排序以及排序次序資訊。<br /><br /> \-或\-<br /><br /> 如果資料來源是 <xref:System.ComponentModel.IBindingListView> 並且支援進階排序，則可取得多重資料行名稱，此資料行名稱是用於排序以及排序次序。|  
  
### 使用 BindingNavigator 進行整合  
 可以使用 <xref:System.Windows.Forms.BindingSource> 元件將任何 Windows Form 控制項繫結至資料來源，但 <xref:System.Windows.Forms.BindingNavigator> 控制項是特別設計用來與 <xref:System.Windows.Forms.BindingSource> 元件搭配使用。  <xref:System.Windows.Forms.BindingNavigator> 控制項所提供的介面用於控制 <xref:System.Windows.Forms.BindingSource> 元件的目前項目。  根據預設，<xref:System.Windows.Forms.BindingNavigator> 控制項所提供的按鈕是對應到 <xref:System.Windows.Forms.BindingSource> 元件上的巡覽方法。  如需詳細資訊，請參閱 [如何：使用 Windows Form BindingNavigator 控制項巡覽資料](../../../../docs/framework/winforms/controls/how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.BindingNavigator>   
 [BindingSource 元件概觀](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)   
 [BindingNavigator 控制項](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)   
 [Windows Form 資料繫結](../../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [如何：將 Windows Form 控制項繫結至類型](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)   
 [如何：使用 BindingSource 反映 Windows Form 控制項中的資料來源更新](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)