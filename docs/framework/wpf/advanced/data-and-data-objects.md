---
title: 資料與資料物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WPF], drag-and-drop
- DataFormats class [WPF]
- DataObject class [WPF]
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
ms.openlocfilehash: 4b948a64a14df7ea79b54b810f734056d57ef406
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964856"
---
# <a name="data-and-data-objects"></a>資料與資料物件
當做拖放作業之一部分傳送的資料會儲存在資料物件中。  就概念而言, 資料物件是由下列一或多個配對所組成:  
  
- <xref:System.Object>包含實際資料的。  
  
- 對應的資料格式識別碼。  
  
 資料本身可以包含可表示為基底<xref:System.Object>的任何專案。  對應的資料格式為字串, 或<xref:System.Type>提供資料所使用之格式的提示。  資料物件支援裝載多個資料/資料格式配對;這可讓單一資料物件以多種格式提供資料。  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>資料物件  
 所有資料物件都必須實<xref:System.Windows.IDataObject>作為介面, 它提供了下列一組標準的方法, 可啟用並加速資料傳輸。  
  
|方法|總結|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|以指定的資料格式抓取資料物件。|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|檢查資料是否可在指定的格式中使用或轉換成。|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|傳回此資料物件中的資料儲存所在的格式清單, 或者可以轉換成。|  
|<xref:System.Windows.IDataObject.SetData%2A>|將指定的資料儲存在此資料物件中。|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]在類別中提供的<xref:System.Windows.IDataObject>基本實作為。<xref:System.Windows.DataObject> Stock <xref:System.Windows.DataObject>類別足以應付許多常見的資料傳輸案例。  
  
 有數個預先定義的格式, 例如 bitmap、CSV、file、HTML、RTF、string、text 和音訊。 如需隨附[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]之預先定義資料格式的詳細資訊, <xref:System.Windows.DataFormats>請參閱類別參考主題。  
  
 資料物件通常包含一項功能, 可讓您在解壓縮資料時, 自動將以某種格式儲存的資料轉換成不同的格式;此功能稱為「自動轉換」。 查詢資料物件中可用的資料格式時, 可以藉由<xref:System.Windows.DataObject.GetFormats%28System.Boolean%29>呼叫或<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>方法, 並將`autoConvert`參數指定為`false`, 以從原生資料格式篩選自動轉換的資料格式。  使用<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>方法將資料新增至資料物件時, 您可以將`autoConvert`參數設定為, 以`false`禁止自動轉換資料。  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>使用資料物件  
 本節說明建立和使用資料物件的常見技術。  
  
### <a name="creating-new-data-objects"></a>建立新的資料物件  
 類別提供數個多載的函式, 可<xref:System.Windows.DataObject>讓您以單一資料/資料格式配對來填入新的實例。 <xref:System.Windows.DataObject>  
  
 下列範例程式碼會建立新的資料物件, 並使用其中一個多<xref:System.Windows.DataObject.%23ctor%2A>載<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>的函式 (), 以字串和指定的資料格式來初始化資料物件。  在此情況下, 資料格式是由字串指定。<xref:System.Windows.DataFormats>類別會提供一組預先定義的類型字串。 預設允許自動轉換儲存的資料。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 如需建立資料物件之程式碼的更多範例, 請參閱[建立資料物件](how-to-create-a-data-object.md)。  
  
### <a name="storing-data-in-multiple-formats"></a>以多種格式儲存資料  
 單一資料物件能夠以多種格式儲存資料。   在單一資料物件內使用多個資料格式的策略, 可能會使資料物件可供更廣泛的卸載目標使用, 而不是只能表示單一資料格式。  請注意, 一般而言, 拖曳來源必須不知道可能的放置目標所能使用的資料格式。  
  
 下列範例示範如何使用<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>方法, 以多種格式將資料新增至資料物件。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>查詢資料物件的可用格式  
 由於單一資料物件可以包含任意數目的資料格式, 因此資料物件會包含用來抓取可用資料格式清單的功能。  
  
 下列範例程式碼會使用<xref:System.Windows.DataObject.GetFormats%2A>多載來取得字串陣列, 表示資料物件中可用的所有資料格式 (原生和自動轉換)。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 如需查詢資料物件以取得可用資料格式之程式碼的更多範例, 請參閱[列出資料物件中的資料格式](how-to-list-the-data-formats-in-a-data-object.md)。  如需查詢資料物件是否存在特定資料格式的範例, 請參閱判斷資料[物件中是否有資料格式](how-to-determine-if-a-data-format-is-present-in-a-data-object.md)。  
  
### <a name="retrieving-data-from-a-data-object"></a>從資料物件中抓取資料  
 以特定格式從資料物件中抓取資料, 只需要呼叫其中一個<xref:System.Windows.DataObject.GetData%2A>方法, 並指定所需的資料格式。  其中一個方法可以用來檢查特定資料格式是否存在。 <xref:System.Windows.DataObject.GetDataPresent%2A>  <xref:System.Windows.DataObject.GetData%2A>傳回中<xref:System.Object>的資料。根據資料格式, 這個物件可以轉換成特定類型的容器。  
  
 下列範例程式碼會使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>多載來檢查指定的資料格式是否可用 (原生或自動轉換)。 如果指定的格式可用, 此範例會使用<xref:System.Windows.DataObject.GetData%28System.String%29>方法來抓取資料。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 如需從資料物件中抓取資料之程式碼的更多範例, 請參閱[以特定資料格式抓取資料](how-to-retrieve-data-in-a-particular-data-format.md)。  
  
### <a name="removing-data-from-a-data-object"></a>從資料物件移除資料  
 資料無法直接從資料物件移除。  若要有效地移除資料物件中的資料, 請遵循下列步驟:  
  
1. 建立新的資料物件, 其中只會包含您要保留的資料。  
  
2. 將所需的資料從舊的資料物件「複製」到新的資料物件。  若要複製資料, 請使用其中一個<xref:System.Windows.DataObject.GetData%2A>方法來<xref:System.Object>抓取包含原始資料的, 然後使用其中一<xref:System.Windows.DataObject.SetData%2A>種方法將資料加入至新的資料物件。  
  
3. 將舊的資料物件取代為新的物件。  
  
> [!NOTE]
> <xref:System.Windows.DataObject.SetData%2A>方法只會將資料新增至資料物件, 而不會取代資料, 即使資料和資料格式與先前的呼叫完全相同也一樣。 針對<xref:System.Windows.DataObject.SetData%2A>相同的資料和資料格式呼叫兩次, 將會導致資料/資料格式出現在資料物件中兩次。
