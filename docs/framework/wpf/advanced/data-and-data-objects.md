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
ms.openlocfilehash: 532c254f997da183b073ddc9e00b4364ecfcd739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186342"
---
# <a name="data-and-data-objects"></a>資料與資料物件
作為拖放操作的一部分傳輸的資料存儲在資料物件中。  從概念上講，資料物件由以下一個或多個對組成：  
  
- 包含<xref:System.Object>實際資料的 。  
  
- 相應的資料格式識別碼。  
  
 資料本身可以包含任何可以表示為基<xref:System.Object>的。  相應的資料格式是字串，或<xref:System.Type>提供有關資料格式的提示。  資料物件支援託管多個資料/資料格式對;這使單個資料物件能夠以多種格式提供資料。  
  
<a name="Data_and_Data_Objects"></a>
## <a name="data-objects"></a>資料物件  
 所有資料物件都必須實現<xref:System.Windows.IDataObject>介面，該介面提供以下支援和促進資料傳輸的標準方法集。  
  
|方法|摘要|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|以指定的資料格式擷取資料物件。|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|檢查資料是否以指定的格式儲存，或是否可轉換成指定的格式。|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|傳回格式清單，這個資料物件中的資料是以這些格式儲存，或是可以轉換成這些格式。|  
|<xref:System.Windows.IDataObject.SetData%2A>|將指定的資料儲存到這個資料物件中。|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]在<xref:System.Windows.DataObject>類中提供了<xref:System.Windows.IDataObject>的基本實現。 股票<xref:System.Windows.DataObject>類足以用於許多常見的資料傳輸方案。  
  
 有幾種預定義的格式，如點陣圖、CSV、檔、HTML、RTF、字串、文本和音訊。 有關 隨提供的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]預定義資料格式的資訊，<xref:System.Windows.DataFormats>請參閱類引用主題。  
  
 資料物件通常包括一個工具，用於在提取資料時自動將存儲在一種格式的資料轉換為其他格式;此設施稱為自動轉換。 查詢資料物件中可用的資料格式時，可以通過調用<xref:System.Windows.DataObject.GetFormats%28System.Boolean%29>或<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>方法並將`autoConvert`參數指定為`false`從本機資料格式篩選自動可轉換資料格式。  使用<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>方法將資料添加到資料物件時，可以通過將`autoConvert`參數設置為`false`禁止自動轉換資料。  
  
<a name="Working_with_Data_Objects"></a>
## <a name="working-with-data-objects"></a>使用資料物件  
 本節介紹創建和使用資料物件的常用技術。  
  
### <a name="creating-new-data-objects"></a>創建新資料物件  
 該<xref:System.Windows.DataObject>類提供了多個重載建構函式，便於使用單個資料/資料<xref:System.Windows.DataObject>格式對填充新實例。  
  
 以下示例代碼創建新的資料物件，並使用其中一個重載建構函式<xref:System.Windows.DataObject.%23ctor%2A>（<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>） 使用字串和指定的資料格式初始化資料物件。  在這種情況下，資料格式由字串指定;例如，資料格式由字串指定。類<xref:System.Windows.DataFormats>提供一組預定義的類型字串。 預設情況下允許自動轉換存儲的資料。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 有關創建資料物件的代碼的更多示例，請參閱[創建資料物件](how-to-create-a-data-object.md)。  
  
### <a name="storing-data-in-multiple-formats"></a>以多種格式存儲資料  
 單個資料物件能夠以多種格式存儲資料。   在單個資料物件中戰略性地使用多種資料格式，可能會使資料物件被更廣泛的放置目標所消耗，而如果只能表示單個資料格式。  請注意，通常，拖動源必須與潛在放置目標可消耗的資料格式無關。  
  
 下面的示例演示如何使用 方法<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>以多種格式將資料添加到資料物件。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>查詢資料物件以獲取可用格式  
 由於單個資料物件可以包含任意數量的資料格式，因此資料物件包括用於檢索可用資料格式清單的功能。  
  
 下面的示例代碼使用<xref:System.Windows.DataObject.GetFormats%2A>重載獲取一個字串陣列，表示資料物件（本機和自動轉換）中可用的所有資料格式。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 有關查詢資料物件可用資料格式的代碼的更多示例，請參閱[在資料物件中列出資料格式](how-to-list-the-data-formats-in-a-data-object.md)。  有關查詢資料物件是否存在特定資料格式的示例，請參閱[確定資料物件中是否存在資料格式](how-to-determine-if-a-data-format-is-present-in-a-data-object.md)。  
  
### <a name="retrieving-data-from-a-data-object"></a>從資料物件檢索資料  
 以特定格式從資料物件檢索資料只需調用其中一<xref:System.Windows.DataObject.GetData%2A>種方法並指定所需的資料格式。  其中一<xref:System.Windows.DataObject.GetDataPresent%2A>種方法可用於檢查是否存在特定資料格式。  <xref:System.Windows.DataObject.GetData%2A>返回 中的<xref:System.Object>資料。根據資料格式，此物件可以強制轉換為特定于類型的容器。  
  
 以下示例代碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>重載來檢查指定的資料格式是否可用（本機還是自動轉換）。 如果指定的格式可用，則示例使用 方法<xref:System.Windows.DataObject.GetData%28System.String%29>檢索資料。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 有關從資料物件檢索資料的代碼的更多示例，請參閱[以特定資料格式檢索資料](how-to-retrieve-data-in-a-particular-data-format.md)。  
  
### <a name="removing-data-from-a-data-object"></a>從資料物件中刪除資料  
 無法直接從資料物件中刪除資料。  要有效地從資料物件中刪除資料，請按照以下步驟操作：  
  
1. 創建新的資料物件，該物件僅包含要保留的資料。  
  
2. 將所需資料從舊資料物件"複製到新資料物件"。  若要複製資料，請使用其中一<xref:System.Windows.DataObject.GetData%2A>種方法檢索包含原始資料的<xref:System.Object>， 然後使用其中一<xref:System.Windows.DataObject.SetData%2A>種方法將資料添加到新的資料物件。  
  
3. 將舊資料物件替換為新資料物件。  
  
> [!NOTE]
> 這些方法<xref:System.Windows.DataObject.SetData%2A>僅將資料添加到資料物件;它們不會替換資料，即使資料和資料格式與上一個調用完全相同。 調用<xref:System.Windows.DataObject.SetData%2A>相同資料和資料格式兩次將導致資料/資料格式在資料物件中存在兩次。
