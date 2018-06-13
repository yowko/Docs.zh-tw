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
ms.openlocfilehash: ff596dc7428c9d105a27999f216d33e735e35a22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540315"
---
# <a name="data-and-data-objects"></a>資料與資料物件
拖放作業期間傳輸的資料會儲存在資料物件。  就概念而言，資料物件包含一或多個下列配對：  
  
-   <xref:System.Object> ，其中包含實際資料。  
  
-   對應的資料格式識別項。  
  
 資料本身可包含的任何項目可以表示做為基底<xref:System.Object>。  對應的資料格式是字串或<xref:System.Type>，提供有關設定資料的格式的提示中。  資料物件支援裝載的多個/資料格式配對。這可讓單一資料物件，提供以多種格式的資料。  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>資料物件  
 所有資料物件必須都實作<xref:System.Windows.IDataObject>介面，提供下列一組標準的方法，啟用並加速資料傳輸方法。  
  
|方法|總結|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|擷取指定之資料格式的資料物件。|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|檢查資料是否可用，或可以轉換成指定的格式。|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|傳回這個資料物件中的資料會儲存在中，或可以轉換成的格式清單。|  
|<xref:System.Windows.IDataObject.SetData%2A>|指定的資料儲存於這個資料物件。|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供的基本實作<xref:System.Windows.IDataObject>中<xref:System.Windows.DataObject>類別。 股票<xref:System.Windows.DataObject>類別已足以應付許多常見的資料傳輸案例。  
  
 有數個預先定義的格式，例如點陣圖、 CSV、 檔案、 HTML、 RTF、 字串、 文字和音訊。 如需隨附的預先定義的資料格式資訊[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，請參閱<xref:System.Windows.DataFormats>類別參考主題。  
  
 資料物件通常包括設備，以用於自動轉換資料儲存在不同格式的一種格式，在擷取資料;此功能稱為自動轉換。 查詢時資料物件中可用的資料格式，自動轉換的資料格式可以篩選從原生資料格式藉由呼叫<xref:System.Windows.DataObject.GetFormats%28System.Boolean%29>或<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>方法並指定`autoConvert`參數做為`false`。  將資料加入至資料物件，但<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>方法時，資料的自動轉換可以藉由設定禁止`autoConvert`參數`false`。  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>使用資料物件  
 本章節描述常見的技巧，用於建立和使用資料物件。  
  
### <a name="creating-new-data-objects"></a>建立新的資料物件  
 <xref:System.Windows.DataObject>類別提供數個多載建構函式，以便填入新<xref:System.Windows.DataObject>單一/資料格式組的執行個體。  
  
 下列範例程式碼會建立新的資料物件，並使用其中一個多載建構函式<xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) 來初始化資料物件和指定的資料格式的字串。  在此情況下，字串; 字串所指定的資料格式<xref:System.Windows.DataFormats>類別會提供一組預先定義的型別字串。 預設為允許自動轉換儲存的資料。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 如需建立資料物件的程式碼範例，請參閱[建立資料物件](../../../../docs/framework/wpf/advanced/how-to-create-a-data-object.md)。  
  
### <a name="storing-data-in-multiple-formats"></a>以多種格式儲存資料  
 單一資料物件都能夠以多種格式儲存資料。   策略使用多個單一資料物件中的資料格式可能會使資料物件更廣泛的置放目標比可取用如果只有單一資料格式可能會表示。  請注意，在一般情況下，拖曳來源必須是無從驗證相關的資料格式會使用可能的置放目標。  
  
 下列範例示範如何使用<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>方法，以將資料加入至多個格式中的資料物件。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>查詢可用的格式資料物件  
 單一資料物件可以包含任意數目的資料格式，因為資料物件包含設備來擷取可用的資料格式的清單。  
  
 下列範例程式碼使用<xref:System.Windows.DataObject.GetFormats%2A>多載來取得代表可用資料物件 （原生和的自動轉換） 中的所有資料格式的字串陣列。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 查詢可用的資料格式的資料物件的程式碼的其他範例，請參閱[清單資料物件中的資料格式](../../../../docs/framework/wpf/advanced/how-to-list-the-data-formats-in-a-data-object.md)。  如需更多的查詢是否存在特定的資料格式的資料物件的範例，請參閱[判斷是否存在的資料格式資料物件中](../../../../docs/framework/wpf/advanced/how-to-determine-if-a-data-format-is-present-in-a-data-object.md)。  
  
### <a name="retrieving-data-from-a-data-object"></a>從資料物件擷取資料  
 從特定格式的資料物件擷取資料，只涉及呼叫其中一個<xref:System.Windows.DataObject.GetData%2A>方法並指定所需的資料格式。  其中一個<xref:System.Windows.DataObject.GetDataPresent%2A>方法可以用來檢查是否有特定的資料格式。  <xref:System.Windows.DataObject.GetData%2A> 會將資料<xref:System.Object>; 視資料格式，這個物件可以轉換成特定類型的容器。  
  
 下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>多載，以檢查是否可以使用指定的資料格式 （原生或自動轉換）。 如果指定的格式使用時，此範例會擷取資料使用<xref:System.Windows.DataObject.GetData%28System.String%29>方法。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 如需詳細的範例程式碼會從資料物件擷取資料，請參閱[擷取特定的資料格式的資料](../../../../docs/framework/wpf/advanced/how-to-retrieve-data-in-a-particular-data-format.md)。  
  
### <a name="removing-data-from-a-data-object"></a>從資料物件中移除資料  
 無法直接移除資料，從資料物件。  若要有效地從資料物件中移除資料，請遵循下列步驟：  
  
1.  建立新的資料物件會包含只有您想要保留的資料。  
  
2.  「 複製 」 所需的資料從舊的資料物件至新的資料物件。  若要複製資料，請使用其中一種<xref:System.Windows.DataObject.GetData%2A>方法來擷取<xref:System.Object>包含原始資料，但使用其中一個<xref:System.Windows.DataObject.SetData%2A>方法，以將資料加入至新的資料物件。  
  
3.  取代新舊資料物件。  
  
> [!NOTE]
>  <xref:System.Windows.DataObject.SetData%2A>方法只會將資料加入至資料物件，即使資料和資料格式並完全相同的上一個呼叫，但是並無法取代資料，則為。 呼叫<xref:System.Windows.DataObject.SetData%2A>兩次的相同資料和資料格式會導致出現兩次資料物件中的資料/資料格式。
