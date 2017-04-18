---
title: "資料與資料物件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "資料轉送 [WPF], 拖放"
  - "DataFormats 類別 [WPF]"
  - "DataObject 類別 [WPF]"
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 資料與資料物件
在拖放作業中傳輸的資料，會儲存在資料物件中。  就概念而言，資料物件由一個或多個下列項目的配對組成：  
  
-   包含實際資料的 <xref:System.Object>。  
  
-   對應的資料格式識別項。  
  
 資料本身可包含任何能以基底 <xref:System.Object> 表示的項目。  對應的資料格式是字串或 <xref:System.Type>，可提供資料所使用格式的相關提示。  資料物件支援裝載多個資料\/資料格式組，這樣可讓單一資料物件提供多種格式的資料。  
  
<a name="Data_and_Data_Objects"></a>   
## 資料物件  
 所有資料物件都必須實作 <xref:System.Windows.IDataObject> 介面，這個介面可提供下列標準方法集以啟用並加速資料傳輸。  
  
|方法|摘要|  
|--------|--------|  
|<xref:System.Windows.IDataObject.GetData%2A>|以指定的資料格式擷取資料物件。|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|檢查資料是否以指定的格式儲存，或是否可轉換成指定的格式。|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|傳回格式清單，這個資料物件中的資料是以這些格式儲存，或是可以轉換成這些格式。|  
|<xref:System.Windows.IDataObject.SetData%2A>|將指定的資料儲存到這個資料物件中。|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供 <xref:System.Windows.DataObject> 類別的 <xref:System.Windows.IDataObject> 基礎實作。  庫存 <xref:System.Windows.DataObject> 類別對於應付許多常見的資料轉送案例已很足夠。  
  
 目前有數個預先定義的格式，例如點陣圖、CSV、檔案、HTML、RTF、字串、文字和音訊。  如需隨 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供之預先定義資料格式的詳細資訊，請參閱 <xref:System.Windows.DataFormats> 類別參考主題。  
  
 資料物件通常包括一項在擷取資料時會將以某種格式儲存的資料自動轉換為另一種格式的機能，這項機能稱為自動轉換。  查詢資料物件中可用的資料格式時，可以藉由呼叫 <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> 或 <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> 方法並指定 `autoConvert` 參數為 `false`，從原生資料格式中篩選可自動轉換的資料格式。  使用 <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> 方法將資料加入至資料物件時，可以將 `autoConvert` 參數設定為 `false` 以禁止自動轉換資料。  
  
<a name="Working_with_Data_Objects"></a>   
## 使用資料物件  
 本節說明建立和使用資料物件的常用技術。  
  
### 建立新的資料物件  
 <xref:System.Windows.DataObject> 類別提供數個多載建構函式，可協助以單一資料\/資料格式組填入新 <xref:System.Windows.DataObject> 執行個體。  
  
 下列範例程式碼會建立新的資料物件，並使用其中一個多載建構函式 <xref:System.Windows.DataObject.%23ctor%2A>\(<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>\) 以用字串和指定的資料格式初始化資料物件。  在這個案例中，資料格式是以字串指定。<xref:System.Windows.DataFormats> 類別可提供一組預先定義的型別字串。  預設會允許對儲存的資料進行自動轉換。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 如需建立資料物件的其他範例程式碼，請參閱 [建立資料庫物件](../../../../docs/framework/wpf/advanced/how-to-create-a-data-object.md)。  
  
### 以多種格式儲存資料  
 一個資料物件可以儲存多種格式的資料。  比起只代表一種資料格式，在單一資料物件中策略性使用多個資料格式，可以讓資料物件能夠適用於更多種類的置放目標。  請注意，一般而言，拖曳來源一定不知道可能的置放目標會使用的資料格式。  
  
 下列範例顯示如何使用 <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> 方法，以多種格式將資料加入至資料物件。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### 查詢資料物件的可用格式  
 因為單一資料物件可包含任意數量的資料格式，所以資料物件附有能擷取可用資料格式清單的機能。  
  
 下列範例程式碼會使用 <xref:System.Windows.DataObject.GetFormats%2A> 多載取得字串陣列，這個字串陣列表示資料物件中所有可用的資料格式 \(包括原生格式和自動轉換的格式\)。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 如需查詢資料物件之可用資料格式的其他範例程式碼，請參閱 [列出資料物件中的資料格式](../../../../docs/framework/wpf/advanced/how-to-list-the-data-formats-in-a-data-object.md)。  如需查詢資料物件是否有特定資料格式的範例，請參閱 [判斷資料格式是否出現在資料物件中](../../../../docs/framework/wpf/advanced/how-to-determine-if-a-data-format-is-present-in-a-data-object.md)。  
  
### 從資料物件擷取資料  
 從資料物件擷取特定格式的資料，只需要呼叫其中一個 <xref:System.Windows.DataObject.GetData%2A> 方法並指定所要的資料格式即可辦到。  有一個 <xref:System.Windows.DataObject.GetDataPresent%2A> 方法可以用來檢查是否有特定的資料格式。  <xref:System.Windows.DataObject.GetData%2A> 會以 <xref:System.Object> 傳回資料。視資料格式而定，這個物件可能會轉型為型別特有的容器。  
  
 下列範例程式碼會使用 <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> 多載，檢查指定的資料格式 \(原生格式或自動轉換的格式\) 是否可用。  如果指定的資料格式可用，則這個範例會使用 <xref:System.Windows.DataObject.GetData%28System.String%29> 方法擷取資料。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 如需從資料物件擷取資料的其他範例程式碼，請參閱 [擷取特定資料格式的資料](../../../../docs/framework/wpf/advanced/how-to-retrieve-data-in-a-particular-data-format.md)。  
  
### 從資料物件移除資料  
 資料無法從資料物件直接移除。  若要從資料物件有效移除資料，請遵循下列步驟：  
  
1.  建立新的資料庫件，這個資料物件將只存放您要保留的資料。  
  
2.  將所要的資料從舊資料物件「複製」到新資料物件。  若要複製資料，請使用其中一個 <xref:System.Windows.DataObject.GetData%2A> 方法來擷取包含未經處理資料 \(Raw Data\) 的 <xref:System.Object>，然後使用其中一個 <xref:System.Windows.DataObject.SetData%2A> 方法將資料加入至新的資料物件。  
  
3.  以新的資料物件取代舊的資料物件。  
  
> [!NOTE]
>  <xref:System.Windows.DataObject.SetData%2A> 方法只會將資料加入至資料物件，並不會取代資料，即使資料和資料格式與先前的資料和資料格式完全相同也一樣。  如果針對同樣的資料和資料格式呼叫兩次 <xref:System.Windows.DataObject.SetData%2A>，則資料物件中會出現兩份資料\/資料格式。