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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312055"
---
# <a name="data-and-data-objects"></a><span data-ttu-id="8ac51-102">資料與資料物件</span><span class="sxs-lookup"><span data-stu-id="8ac51-102">Data and Data Objects</span></span>
<span data-ttu-id="8ac51-103">拖放作業的一部分傳送的資料會儲存在資料物件。</span><span class="sxs-lookup"><span data-stu-id="8ac51-103">Data that is transferred as part of a drag-and-drop operation is stored in a data object.</span></span>  <span data-ttu-id="8ac51-104">就概念而言，資料物件包含一或多個下列組合：</span><span class="sxs-lookup"><span data-stu-id="8ac51-104">Conceptually, a data object consists of one or more of the following pairs:</span></span>  
  
-   <span data-ttu-id="8ac51-105"><xref:System.Object>包含實際的資料。</span><span class="sxs-lookup"><span data-stu-id="8ac51-105">An <xref:System.Object> that contains the actual data.</span></span>  
  
-   <span data-ttu-id="8ac51-106">對應的資料格式識別項。</span><span class="sxs-lookup"><span data-stu-id="8ac51-106">A corresponding data format identifier.</span></span>  
  
 <span data-ttu-id="8ac51-107">資料本身可以包含任何項目可以表示做為基底<xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="8ac51-107">The data itself can consist of anything that can be represented as a base <xref:System.Object>.</span></span>  <span data-ttu-id="8ac51-108">對應的資料格式是字串或<xref:System.Type>，提供有關在設定資料的格式為。</span><span class="sxs-lookup"><span data-stu-id="8ac51-108">The corresponding data format is a string or <xref:System.Type> that provides a hint about what format the data is in.</span></span>  <span data-ttu-id="8ac51-109">資料物件支援裝載多個/資料格式組;這可讓單一資料物件，提供多種格式的資料。</span><span class="sxs-lookup"><span data-stu-id="8ac51-109">Data objects support hosting multiple data/data format pairs; this enables a single data object to provide data in multiple formats.</span></span>  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a><span data-ttu-id="8ac51-110">資料物件</span><span class="sxs-lookup"><span data-stu-id="8ac51-110">Data Objects</span></span>  
 <span data-ttu-id="8ac51-111">所有的資料物件必須實作<xref:System.Windows.IDataObject>介面，可提供下列標準集的啟用，並加速資料傳輸的方法。</span><span class="sxs-lookup"><span data-stu-id="8ac51-111">All data objects must implement the <xref:System.Windows.IDataObject> interface, which provides the following standard set of methods that enable and facilitate data transfer.</span></span>  
  
|<span data-ttu-id="8ac51-112">方法</span><span class="sxs-lookup"><span data-stu-id="8ac51-112">Method</span></span>|<span data-ttu-id="8ac51-113">總結</span><span class="sxs-lookup"><span data-stu-id="8ac51-113">Summary</span></span>|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|<span data-ttu-id="8ac51-114">擷取指定之資料格式中的資料物件。</span><span class="sxs-lookup"><span data-stu-id="8ac51-114">Retrieves a data object in a specified data format.</span></span>|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|<span data-ttu-id="8ac51-115">檢查以查看資料，或可以轉換成指定的格式。</span><span class="sxs-lookup"><span data-stu-id="8ac51-115">Checks to see whether the data is available in, or can be converted to, a specified format.</span></span>|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|<span data-ttu-id="8ac51-116">傳回這個資料物件中的資料會儲存在或可以轉換成的格式清單。</span><span class="sxs-lookup"><span data-stu-id="8ac51-116">Returns a list of formats that the data in this data object is stored in, or can be converted to.</span></span>|  
|<xref:System.Windows.IDataObject.SetData%2A>|<span data-ttu-id="8ac51-117">指定的資料儲存在這個資料物件中。</span><span class="sxs-lookup"><span data-stu-id="8ac51-117">Stores the specified data in this data object.</span></span>|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="8ac51-118">提供的基本實作<xref:System.Windows.IDataObject>在<xref:System.Windows.DataObject>類別。</span><span class="sxs-lookup"><span data-stu-id="8ac51-118">provides a basic implementation of <xref:System.Windows.IDataObject> in the <xref:System.Windows.DataObject> class.</span></span> <span data-ttu-id="8ac51-119">股票<xref:System.Windows.DataObject>類別就足以應付許多常見的資料傳輸案例。</span><span class="sxs-lookup"><span data-stu-id="8ac51-119">The stock <xref:System.Windows.DataObject> class is sufficient for many common data transfer scenarios.</span></span>  
  
 <span data-ttu-id="8ac51-120">有數個預先定義的格式的詳細資訊，例如點陣圖、 CSV、 檔案、 HTML、 RTF、 字串、 文字及音訊。</span><span class="sxs-lookup"><span data-stu-id="8ac51-120">There are several pre-defined formats, such as bitmap, CSV, file, HTML, RTF, string, text, and audio.</span></span> <span data-ttu-id="8ac51-121">如需隨附的預先定義的資料格式的詳細資訊[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，請參閱<xref:System.Windows.DataFormats>類別參考主題。</span><span class="sxs-lookup"><span data-stu-id="8ac51-121">For information about pre-defined data formats provided with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see the <xref:System.Windows.DataFormats> class reference topic.</span></span>  
  
 <span data-ttu-id="8ac51-122">資料物件通常包含一項工具供自動轉換資料格式儲存在一個不同的格式時擷取資料;這項功能稱為自動轉換。</span><span class="sxs-lookup"><span data-stu-id="8ac51-122">Data objects commonly include a facility for automatically converting data stored in one format to a different format while extracting data; this facility is referred to as auto-convert.</span></span> <span data-ttu-id="8ac51-123">當查詢使用資料物件中的資料格式，自動轉換的資料格式可以篩選從原生資料格式藉由呼叫<xref:System.Windows.DataObject.GetFormats%28System.Boolean%29>或是<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>方法並指定`autoConvert`參數做為`false`。</span><span class="sxs-lookup"><span data-stu-id="8ac51-123">When querying for the data formats available in a data object, auto-convertible data formats can be filtered from native data formats by calling the <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> or <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> method and specifying the `autoConvert` parameter as `false`.</span></span>  <span data-ttu-id="8ac51-124">將資料加入至資料物件與<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>方法中，資料的自動轉換可以藉由設定禁止`autoConvert`參數來`false`。</span><span class="sxs-lookup"><span data-stu-id="8ac51-124">When adding data to a data object with the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> method, auto-conversion of data can be prohibited by setting the `autoConvert` parameter to `false`.</span></span>  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a><span data-ttu-id="8ac51-125">使用資料物件</span><span class="sxs-lookup"><span data-stu-id="8ac51-125">Working with Data Objects</span></span>  
 <span data-ttu-id="8ac51-126">本節描述常見的技巧，來建立和使用資料物件。</span><span class="sxs-lookup"><span data-stu-id="8ac51-126">This section describes common techniques for creating and working with data objects.</span></span>  
  
### <a name="creating-new-data-objects"></a><span data-ttu-id="8ac51-127">建立新的資料物件</span><span class="sxs-lookup"><span data-stu-id="8ac51-127">Creating New Data Objects</span></span>  
 <span data-ttu-id="8ac51-128"><xref:System.Windows.DataObject>類別提供數個多載建構函式，以便填入新<xref:System.Windows.DataObject>單一/資料格式組的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8ac51-128">The <xref:System.Windows.DataObject> class provides several overloaded constructors that facilitate populating a new <xref:System.Windows.DataObject> instance with a single data/data format pair.</span></span>  
  
 <span data-ttu-id="8ac51-129">下列範例程式碼會建立新的資料物件，並使用其中一個多載的建構函式<xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) 來初始化字串與指定的資料格式的資料物件。</span><span class="sxs-lookup"><span data-stu-id="8ac51-129">The following example code creates a new data object and uses one of the overloaded constructors <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="8ac51-130">在此情況下，指定資料格式由字串;<xref:System.Windows.DataFormats>類別提供一組預先定義的型別字串。</span><span class="sxs-lookup"><span data-stu-id="8ac51-130">In this case, the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="8ac51-131">預設為允許的已儲存資料的自動轉換。</span><span class="sxs-lookup"><span data-stu-id="8ac51-131">Auto-conversion of the stored data is allowed by default.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 <span data-ttu-id="8ac51-132">如需建立資料物件的程式碼的更多範例，請參閱[建立資料物件](how-to-create-a-data-object.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac51-132">For more examples of code that creates a data object, see [Create a Data Object](how-to-create-a-data-object.md).</span></span>  
  
### <a name="storing-data-in-multiple-formats"></a><span data-ttu-id="8ac51-133">將資料儲存在多個格式</span><span class="sxs-lookup"><span data-stu-id="8ac51-133">Storing Data in Multiple Formats</span></span>  
 <span data-ttu-id="8ac51-134">單一的資料物件是能夠以多種格式儲存資料。</span><span class="sxs-lookup"><span data-stu-id="8ac51-134">A single data object is able to store data in multiple formats.</span></span>   <span data-ttu-id="8ac51-135">策略使用單一資料物件中的多個資料格式可能會使資料物件適用於更廣泛的置放目標比只有可能代表單一資料格式。</span><span class="sxs-lookup"><span data-stu-id="8ac51-135">Strategic use of multiple data formats within a single data object potentially makes the data object consumable by a wider variety of drop targets than if only a single data format could be represented.</span></span>  <span data-ttu-id="8ac51-136">請注意，在一般情況下，為拖曳來源必須是關於適用於潛在的置放目標的資料格式無從驗證。</span><span class="sxs-lookup"><span data-stu-id="8ac51-136">Note that, in general, a drag source must be agnostic about the data formats that are consumable by potential drop targets.</span></span>  
  
 <span data-ttu-id="8ac51-137">下列範例示範如何使用<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>方法，以將資料加入至多個格式中的資料物件。</span><span class="sxs-lookup"><span data-stu-id="8ac51-137">The following example shows how to use the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> method to add data to a data object in multiple formats.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a><span data-ttu-id="8ac51-138">查詢可用的格式資料物件</span><span class="sxs-lookup"><span data-stu-id="8ac51-138">Querying a Data Object for Available Formats</span></span>  
 <span data-ttu-id="8ac51-139">因為單一資料物件可以包含任意數目的資料格式，資料物件會包含用於擷取一份可用的資料格式的功能。</span><span class="sxs-lookup"><span data-stu-id="8ac51-139">Because a single data object can contain an arbitrary number of data formats, data objects include facilities for retrieving a list of available data formats.</span></span>  
  
 <span data-ttu-id="8ac51-140">下列範例程式碼使用<xref:System.Windows.DataObject.GetFormats%2A>多載，以取得用來表示資料物件 （原生和的自動轉換） 中可用的所有資料格式的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="8ac51-140">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and by auto-convert).</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 <span data-ttu-id="8ac51-141">查詢可用的資料格式的資料物件的程式碼的更多範例，請參閱[列出資料物件中的資料格式](how-to-list-the-data-formats-in-a-data-object.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac51-141">For more examples of code that queries a data object for available data formats, see [List the Data Formats in a Data Object](how-to-list-the-data-formats-in-a-data-object.md).</span></span>  <span data-ttu-id="8ac51-142">如需更多的查詢是否有特定的資料格式的資料物件的範例，請參閱[判斷資料格式是否出現在資料物件](how-to-determine-if-a-data-format-is-present-in-a-data-object.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac51-142">For examples of querying a data object for the presence of a particular data format, see [Determine if a Data Format is Present in a Data Object](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).</span></span>  
  
### <a name="retrieving-data-from-a-data-object"></a><span data-ttu-id="8ac51-143">從資料物件擷取資料</span><span class="sxs-lookup"><span data-stu-id="8ac51-143">Retrieving Data from a Data Object</span></span>  
 <span data-ttu-id="8ac51-144">擷取以特定格式的資料物件中的資料，只涉及呼叫其中一個<xref:System.Windows.DataObject.GetData%2A>方法和指定的所需的資料格式。</span><span class="sxs-lookup"><span data-stu-id="8ac51-144">Retrieving data from a data object in a particular format simply involves calling one of the <xref:System.Windows.DataObject.GetData%2A> methods and specifying the desired data format.</span></span>  <span data-ttu-id="8ac51-145">其中一個<xref:System.Windows.DataObject.GetDataPresent%2A>方法可用來檢查是否有特定的資料格式。</span><span class="sxs-lookup"><span data-stu-id="8ac51-145">One of the <xref:System.Windows.DataObject.GetDataPresent%2A> methods can be used to check for the presence of a particular data format.</span></span>  <span data-ttu-id="8ac51-146"><xref:System.Windows.DataObject.GetData%2A> 會將資料傳入<xref:System.Object>; 視資料格式，這個物件可以轉換成特定類型的容器。</span><span class="sxs-lookup"><span data-stu-id="8ac51-146"><xref:System.Windows.DataObject.GetData%2A> returns the data in an <xref:System.Object>; depending on the data format, this object can be cast to a type-specific container.</span></span>  
  
 <span data-ttu-id="8ac51-147">下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>多載，以檢查是否有可用的指定的資料格式 （原生或自動轉換）。</span><span class="sxs-lookup"><span data-stu-id="8ac51-147">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to check if a specified data format is available (native or by auto-convert).</span></span> <span data-ttu-id="8ac51-148">如果指定的格式使用時，範例會使用擷取資料<xref:System.Windows.DataObject.GetData%28System.String%29>方法。</span><span class="sxs-lookup"><span data-stu-id="8ac51-148">If the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 <span data-ttu-id="8ac51-149">如需從資料物件擷取資料的程式碼範例，請參閱[擷取特定資料格式的資料](how-to-retrieve-data-in-a-particular-data-format.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac51-149">For more examples of code that retrieves data from a data object, see [Retrieve Data in a Particular Data Format](how-to-retrieve-data-in-a-particular-data-format.md).</span></span>  
  
### <a name="removing-data-from-a-data-object"></a><span data-ttu-id="8ac51-150">從資料物件中移除資料</span><span class="sxs-lookup"><span data-stu-id="8ac51-150">Removing Data From a Data Object</span></span>  
 <span data-ttu-id="8ac51-151">無法直接移除資料，從資料物件。</span><span class="sxs-lookup"><span data-stu-id="8ac51-151">Data cannot be directly removed from a data object.</span></span>  <span data-ttu-id="8ac51-152">若要有效地從資料物件中移除資料，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="8ac51-152">To effectively remove data from a data object, follow these steps:</span></span>  
  
1. <span data-ttu-id="8ac51-153">建立新的資料物件，包含只有您想要保留的資料。</span><span class="sxs-lookup"><span data-stu-id="8ac51-153">Create a new data object that will contain only the data you want to retain.</span></span>  
  
2. <span data-ttu-id="8ac51-154">「 複製 」 所需的資料從舊的資料物件新的資料物件。</span><span class="sxs-lookup"><span data-stu-id="8ac51-154">"Copy" the desired data from the old data object to the new data object.</span></span>  <span data-ttu-id="8ac51-155">若要複製資料，請使用其中一種<xref:System.Windows.DataObject.GetData%2A>方法來擷取<xref:System.Object>包含原始資料，但接著會使用其中一種<xref:System.Windows.DataObject.SetData%2A>方法，以將資料加入新的資料物件。</span><span class="sxs-lookup"><span data-stu-id="8ac51-155">To copy the data, use one of the <xref:System.Windows.DataObject.GetData%2A> methods to retrieve an <xref:System.Object> that contains the raw data, and then use one of the <xref:System.Windows.DataObject.SetData%2A> methods to add the data to the new data object.</span></span>  
  
3. <span data-ttu-id="8ac51-156">以新的取代舊的資料物件。</span><span class="sxs-lookup"><span data-stu-id="8ac51-156">Replace the old data object with the new one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ac51-157"><xref:System.Windows.DataObject.SetData%2A>方法只會將資料加入至資料物件; 它們並不會取代資料，即使資料和資料格式是完全由先前呼叫相同。</span><span class="sxs-lookup"><span data-stu-id="8ac51-157">The <xref:System.Windows.DataObject.SetData%2A> methods only add data to a data object; they do not replace data, even if the data and data format are exactly the same as a previous call.</span></span> <span data-ttu-id="8ac51-158">呼叫<xref:System.Windows.DataObject.SetData%2A>兩次，針對相同的資料和資料格式會導致出現兩次相同的資料物件的資料/資料格式。</span><span class="sxs-lookup"><span data-stu-id="8ac51-158">Calling <xref:System.Windows.DataObject.SetData%2A> twice for the same data and data format will result in the data/data format being present twice in the data object.</span></span>
