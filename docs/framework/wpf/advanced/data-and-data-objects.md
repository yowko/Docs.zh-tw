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
ms.openlocfilehash: 9dc195ece60739cf0c137a2893c9e9150e0d4d3f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312055"
---
# <a name="data-and-data-objects"></a>資料與資料物件
拖放作業的一部分傳送的資料會儲存在資料物件。  就概念而言，資料物件包含一或多個下列組合：  
  
-   <xref:System.Object>包含實際的資料。  
  
-   對應的資料格式識別項。  
  
 資料本身可以包含任何項目可以表示做為基底<xref:System.Object>。  對應的資料格式是字串或<xref:System.Type>，提供有關在設定資料的格式為。  資料物件支援裝載多個/資料格式組;這可讓單一資料物件，提供多種格式的資料。  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>資料物件  
 所有的資料物件必須實作<xref:System.Windows.IDataObject>介面，可提供下列標準集的啟用，並加速資料傳輸的方法。  
  
|方法|總結|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|擷取指定之資料格式中的資料物件。|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|檢查以查看資料，或可以轉換成指定的格式。|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|傳回這個資料物件中的資料會儲存在或可以轉換成的格式清單。|  
|<xref:System.Windows.IDataObject.SetData%2A>|指定的資料儲存在這個資料物件中。|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供的基本實作<xref:System.Windows.IDataObject>在<xref:System.Windows.DataObject>類別。 股票<xref:System.Windows.DataObject>類別就足以應付許多常見的資料傳輸案例。  
  
 有數個預先定義的格式的詳細資訊，例如點陣圖、 CSV、 檔案、 HTML、 RTF、 字串、 文字及音訊。 如需隨附的預先定義的資料格式的詳細資訊[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，請參閱<xref:System.Windows.DataFormats>類別參考主題。  
  
 資料物件通常包含一項工具供自動轉換資料格式儲存在一個不同的格式時擷取資料;這項功能稱為自動轉換。 當查詢使用資料物件中的資料格式，自動轉換的資料格式可以篩選從原生資料格式藉由呼叫<xref:System.Windows.DataObject.GetFormats%28System.Boolean%29>或是<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>方法並指定`autoConvert`參數做為`false`。  將資料加入至資料物件與<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>方法中，資料的自動轉換可以藉由設定禁止`autoConvert`參數來`false`。  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>使用資料物件  
 本節描述常見的技巧，來建立和使用資料物件。  
  
### <a name="creating-new-data-objects"></a>建立新的資料物件  
 <xref:System.Windows.DataObject>類別提供數個多載建構函式，以便填入新<xref:System.Windows.DataObject>單一/資料格式組的執行個體。  
  
 下列範例程式碼會建立新的資料物件，並使用其中一個多載的建構函式<xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) 來初始化字串與指定的資料格式的資料物件。  在此情況下，指定資料格式由字串;<xref:System.Windows.DataFormats>類別提供一組預先定義的型別字串。 預設為允許的已儲存資料的自動轉換。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 如需建立資料物件的程式碼的更多範例，請參閱[建立資料物件](how-to-create-a-data-object.md)。  
  
### <a name="storing-data-in-multiple-formats"></a>將資料儲存在多個格式  
 單一的資料物件是能夠以多種格式儲存資料。   策略使用單一資料物件中的多個資料格式可能會使資料物件適用於更廣泛的置放目標比只有可能代表單一資料格式。  請注意，在一般情況下，為拖曳來源必須是關於適用於潛在的置放目標的資料格式無從驗證。  
  
 下列範例示範如何使用<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>方法，以將資料加入至多個格式中的資料物件。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>查詢可用的格式資料物件  
 因為單一資料物件可以包含任意數目的資料格式，資料物件會包含用於擷取一份可用的資料格式的功能。  
  
 下列範例程式碼使用<xref:System.Windows.DataObject.GetFormats%2A>多載，以取得用來表示資料物件 （原生和的自動轉換） 中可用的所有資料格式的字串陣列。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 查詢可用的資料格式的資料物件的程式碼的更多範例，請參閱[列出資料物件中的資料格式](how-to-list-the-data-formats-in-a-data-object.md)。  如需更多的查詢是否有特定的資料格式的資料物件的範例，請參閱[判斷資料格式是否出現在資料物件](how-to-determine-if-a-data-format-is-present-in-a-data-object.md)。  
  
### <a name="retrieving-data-from-a-data-object"></a>從資料物件擷取資料  
 擷取以特定格式的資料物件中的資料，只涉及呼叫其中一個<xref:System.Windows.DataObject.GetData%2A>方法和指定的所需的資料格式。  其中一個<xref:System.Windows.DataObject.GetDataPresent%2A>方法可用來檢查是否有特定的資料格式。  <xref:System.Windows.DataObject.GetData%2A> 會將資料傳入<xref:System.Object>; 視資料格式，這個物件可以轉換成特定類型的容器。  
  
 下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>多載，以檢查是否有可用的指定的資料格式 （原生或自動轉換）。 如果指定的格式使用時，範例會使用擷取資料<xref:System.Windows.DataObject.GetData%28System.String%29>方法。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 如需從資料物件擷取資料的程式碼範例，請參閱[擷取特定資料格式的資料](how-to-retrieve-data-in-a-particular-data-format.md)。  
  
### <a name="removing-data-from-a-data-object"></a>從資料物件中移除資料  
 無法直接移除資料，從資料物件。  若要有效地從資料物件中移除資料，請遵循下列步驟：  
  
1. 建立新的資料物件，包含只有您想要保留的資料。  
  
2. 「 複製 」 所需的資料從舊的資料物件新的資料物件。  若要複製資料，請使用其中一種<xref:System.Windows.DataObject.GetData%2A>方法來擷取<xref:System.Object>包含原始資料，但接著會使用其中一種<xref:System.Windows.DataObject.SetData%2A>方法，以將資料加入新的資料物件。  
  
3. 以新的取代舊的資料物件。  
  
> [!NOTE]
>  <xref:System.Windows.DataObject.SetData%2A>方法只會將資料加入至資料物件; 它們並不會取代資料，即使資料和資料格式是完全由先前呼叫相同。 呼叫<xref:System.Windows.DataObject.SetData%2A>兩次，針對相同的資料和資料格式會導致出現兩次相同的資料物件的資料/資料格式。
