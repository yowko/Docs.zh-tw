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
# <a name="data-and-data-objects"></a><span data-ttu-id="31899-102">資料與資料物件</span><span class="sxs-lookup"><span data-stu-id="31899-102">Data and Data Objects</span></span>
<span data-ttu-id="31899-103">當做拖放作業之一部分傳送的資料會儲存在資料物件中。</span><span class="sxs-lookup"><span data-stu-id="31899-103">Data that is transferred as part of a drag-and-drop operation is stored in a data object.</span></span>  <span data-ttu-id="31899-104">就概念而言, 資料物件是由下列一或多個配對所組成:</span><span class="sxs-lookup"><span data-stu-id="31899-104">Conceptually, a data object consists of one or more of the following pairs:</span></span>  
  
- <span data-ttu-id="31899-105"><xref:System.Object>包含實際資料的。</span><span class="sxs-lookup"><span data-stu-id="31899-105">An <xref:System.Object> that contains the actual data.</span></span>  
  
- <span data-ttu-id="31899-106">對應的資料格式識別碼。</span><span class="sxs-lookup"><span data-stu-id="31899-106">A corresponding data format identifier.</span></span>  
  
 <span data-ttu-id="31899-107">資料本身可以包含可表示為基底<xref:System.Object>的任何專案。</span><span class="sxs-lookup"><span data-stu-id="31899-107">The data itself can consist of anything that can be represented as a base <xref:System.Object>.</span></span>  <span data-ttu-id="31899-108">對應的資料格式為字串, 或<xref:System.Type>提供資料所使用之格式的提示。</span><span class="sxs-lookup"><span data-stu-id="31899-108">The corresponding data format is a string or <xref:System.Type> that provides a hint about what format the data is in.</span></span>  <span data-ttu-id="31899-109">資料物件支援裝載多個資料/資料格式配對;這可讓單一資料物件以多種格式提供資料。</span><span class="sxs-lookup"><span data-stu-id="31899-109">Data objects support hosting multiple data/data format pairs; this enables a single data object to provide data in multiple formats.</span></span>  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a><span data-ttu-id="31899-110">資料物件</span><span class="sxs-lookup"><span data-stu-id="31899-110">Data Objects</span></span>  
 <span data-ttu-id="31899-111">所有資料物件都必須實<xref:System.Windows.IDataObject>作為介面, 它提供了下列一組標準的方法, 可啟用並加速資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="31899-111">All data objects must implement the <xref:System.Windows.IDataObject> interface, which provides the following standard set of methods that enable and facilitate data transfer.</span></span>  
  
|<span data-ttu-id="31899-112">方法</span><span class="sxs-lookup"><span data-stu-id="31899-112">Method</span></span>|<span data-ttu-id="31899-113">總結</span><span class="sxs-lookup"><span data-stu-id="31899-113">Summary</span></span>|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|<span data-ttu-id="31899-114">以指定的資料格式抓取資料物件。</span><span class="sxs-lookup"><span data-stu-id="31899-114">Retrieves a data object in a specified data format.</span></span>|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|<span data-ttu-id="31899-115">檢查資料是否可在指定的格式中使用或轉換成。</span><span class="sxs-lookup"><span data-stu-id="31899-115">Checks to see whether the data is available in, or can be converted to, a specified format.</span></span>|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|<span data-ttu-id="31899-116">傳回此資料物件中的資料儲存所在的格式清單, 或者可以轉換成。</span><span class="sxs-lookup"><span data-stu-id="31899-116">Returns a list of formats that the data in this data object is stored in, or can be converted to.</span></span>|  
|<xref:System.Windows.IDataObject.SetData%2A>|<span data-ttu-id="31899-117">將指定的資料儲存在此資料物件中。</span><span class="sxs-lookup"><span data-stu-id="31899-117">Stores the specified data in this data object.</span></span>|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="31899-118">在類別中提供的<xref:System.Windows.IDataObject>基本實作為。<xref:System.Windows.DataObject></span><span class="sxs-lookup"><span data-stu-id="31899-118">provides a basic implementation of <xref:System.Windows.IDataObject> in the <xref:System.Windows.DataObject> class.</span></span> <span data-ttu-id="31899-119">Stock <xref:System.Windows.DataObject>類別足以應付許多常見的資料傳輸案例。</span><span class="sxs-lookup"><span data-stu-id="31899-119">The stock <xref:System.Windows.DataObject> class is sufficient for many common data transfer scenarios.</span></span>  
  
 <span data-ttu-id="31899-120">有數個預先定義的格式, 例如 bitmap、CSV、file、HTML、RTF、string、text 和音訊。</span><span class="sxs-lookup"><span data-stu-id="31899-120">There are several pre-defined formats, such as bitmap, CSV, file, HTML, RTF, string, text, and audio.</span></span> <span data-ttu-id="31899-121">如需隨附[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]之預先定義資料格式的詳細資訊, <xref:System.Windows.DataFormats>請參閱類別參考主題。</span><span class="sxs-lookup"><span data-stu-id="31899-121">For information about pre-defined data formats provided with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see the <xref:System.Windows.DataFormats> class reference topic.</span></span>  
  
 <span data-ttu-id="31899-122">資料物件通常包含一項功能, 可讓您在解壓縮資料時, 自動將以某種格式儲存的資料轉換成不同的格式;此功能稱為「自動轉換」。</span><span class="sxs-lookup"><span data-stu-id="31899-122">Data objects commonly include a facility for automatically converting data stored in one format to a different format while extracting data; this facility is referred to as auto-convert.</span></span> <span data-ttu-id="31899-123">查詢資料物件中可用的資料格式時, 可以藉由<xref:System.Windows.DataObject.GetFormats%28System.Boolean%29>呼叫或<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>方法, 並將`autoConvert`參數指定為`false`, 以從原生資料格式篩選自動轉換的資料格式。</span><span class="sxs-lookup"><span data-stu-id="31899-123">When querying for the data formats available in a data object, auto-convertible data formats can be filtered from native data formats by calling the <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> or <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> method and specifying the `autoConvert` parameter as `false`.</span></span>  <span data-ttu-id="31899-124">使用<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>方法將資料新增至資料物件時, 您可以將`autoConvert`參數設定為, 以`false`禁止自動轉換資料。</span><span class="sxs-lookup"><span data-stu-id="31899-124">When adding data to a data object with the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> method, auto-conversion of data can be prohibited by setting the `autoConvert` parameter to `false`.</span></span>  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a><span data-ttu-id="31899-125">使用資料物件</span><span class="sxs-lookup"><span data-stu-id="31899-125">Working with Data Objects</span></span>  
 <span data-ttu-id="31899-126">本節說明建立和使用資料物件的常見技術。</span><span class="sxs-lookup"><span data-stu-id="31899-126">This section describes common techniques for creating and working with data objects.</span></span>  
  
### <a name="creating-new-data-objects"></a><span data-ttu-id="31899-127">建立新的資料物件</span><span class="sxs-lookup"><span data-stu-id="31899-127">Creating New Data Objects</span></span>  
 <span data-ttu-id="31899-128">類別提供數個多載的函式, 可<xref:System.Windows.DataObject>讓您以單一資料/資料格式配對來填入新的實例。 <xref:System.Windows.DataObject></span><span class="sxs-lookup"><span data-stu-id="31899-128">The <xref:System.Windows.DataObject> class provides several overloaded constructors that facilitate populating a new <xref:System.Windows.DataObject> instance with a single data/data format pair.</span></span>  
  
 <span data-ttu-id="31899-129">下列範例程式碼會建立新的資料物件, 並使用其中一個多<xref:System.Windows.DataObject.%23ctor%2A>載<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>的函式 (), 以字串和指定的資料格式來初始化資料物件。</span><span class="sxs-lookup"><span data-stu-id="31899-129">The following example code creates a new data object and uses one of the overloaded constructors <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="31899-130">在此情況下, 資料格式是由字串指定。<xref:System.Windows.DataFormats>類別會提供一組預先定義的類型字串。</span><span class="sxs-lookup"><span data-stu-id="31899-130">In this case, the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="31899-131">預設允許自動轉換儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="31899-131">Auto-conversion of the stored data is allowed by default.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 <span data-ttu-id="31899-132">如需建立資料物件之程式碼的更多範例, 請參閱[建立資料物件](how-to-create-a-data-object.md)。</span><span class="sxs-lookup"><span data-stu-id="31899-132">For more examples of code that creates a data object, see [Create a Data Object](how-to-create-a-data-object.md).</span></span>  
  
### <a name="storing-data-in-multiple-formats"></a><span data-ttu-id="31899-133">以多種格式儲存資料</span><span class="sxs-lookup"><span data-stu-id="31899-133">Storing Data in Multiple Formats</span></span>  
 <span data-ttu-id="31899-134">單一資料物件能夠以多種格式儲存資料。</span><span class="sxs-lookup"><span data-stu-id="31899-134">A single data object is able to store data in multiple formats.</span></span>   <span data-ttu-id="31899-135">在單一資料物件內使用多個資料格式的策略, 可能會使資料物件可供更廣泛的卸載目標使用, 而不是只能表示單一資料格式。</span><span class="sxs-lookup"><span data-stu-id="31899-135">Strategic use of multiple data formats within a single data object potentially makes the data object consumable by a wider variety of drop targets than if only a single data format could be represented.</span></span>  <span data-ttu-id="31899-136">請注意, 一般而言, 拖曳來源必須不知道可能的放置目標所能使用的資料格式。</span><span class="sxs-lookup"><span data-stu-id="31899-136">Note that, in general, a drag source must be agnostic about the data formats that are consumable by potential drop targets.</span></span>  
  
 <span data-ttu-id="31899-137">下列範例示範如何使用<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>方法, 以多種格式將資料新增至資料物件。</span><span class="sxs-lookup"><span data-stu-id="31899-137">The following example shows how to use the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> method to add data to a data object in multiple formats.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a><span data-ttu-id="31899-138">查詢資料物件的可用格式</span><span class="sxs-lookup"><span data-stu-id="31899-138">Querying a Data Object for Available Formats</span></span>  
 <span data-ttu-id="31899-139">由於單一資料物件可以包含任意數目的資料格式, 因此資料物件會包含用來抓取可用資料格式清單的功能。</span><span class="sxs-lookup"><span data-stu-id="31899-139">Because a single data object can contain an arbitrary number of data formats, data objects include facilities for retrieving a list of available data formats.</span></span>  
  
 <span data-ttu-id="31899-140">下列範例程式碼會使用<xref:System.Windows.DataObject.GetFormats%2A>多載來取得字串陣列, 表示資料物件中可用的所有資料格式 (原生和自動轉換)。</span><span class="sxs-lookup"><span data-stu-id="31899-140">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and by auto-convert).</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 <span data-ttu-id="31899-141">如需查詢資料物件以取得可用資料格式之程式碼的更多範例, 請參閱[列出資料物件中的資料格式](how-to-list-the-data-formats-in-a-data-object.md)。</span><span class="sxs-lookup"><span data-stu-id="31899-141">For more examples of code that queries a data object for available data formats, see [List the Data Formats in a Data Object](how-to-list-the-data-formats-in-a-data-object.md).</span></span>  <span data-ttu-id="31899-142">如需查詢資料物件是否存在特定資料格式的範例, 請參閱判斷資料[物件中是否有資料格式](how-to-determine-if-a-data-format-is-present-in-a-data-object.md)。</span><span class="sxs-lookup"><span data-stu-id="31899-142">For examples of querying a data object for the presence of a particular data format, see [Determine if a Data Format is Present in a Data Object](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).</span></span>  
  
### <a name="retrieving-data-from-a-data-object"></a><span data-ttu-id="31899-143">從資料物件中抓取資料</span><span class="sxs-lookup"><span data-stu-id="31899-143">Retrieving Data from a Data Object</span></span>  
 <span data-ttu-id="31899-144">以特定格式從資料物件中抓取資料, 只需要呼叫其中一個<xref:System.Windows.DataObject.GetData%2A>方法, 並指定所需的資料格式。</span><span class="sxs-lookup"><span data-stu-id="31899-144">Retrieving data from a data object in a particular format simply involves calling one of the <xref:System.Windows.DataObject.GetData%2A> methods and specifying the desired data format.</span></span>  <span data-ttu-id="31899-145">其中一個方法可以用來檢查特定資料格式是否存在。 <xref:System.Windows.DataObject.GetDataPresent%2A></span><span class="sxs-lookup"><span data-stu-id="31899-145">One of the <xref:System.Windows.DataObject.GetDataPresent%2A> methods can be used to check for the presence of a particular data format.</span></span>  <span data-ttu-id="31899-146"><xref:System.Windows.DataObject.GetData%2A>傳回中<xref:System.Object>的資料。根據資料格式, 這個物件可以轉換成特定類型的容器。</span><span class="sxs-lookup"><span data-stu-id="31899-146"><xref:System.Windows.DataObject.GetData%2A> returns the data in an <xref:System.Object>; depending on the data format, this object can be cast to a type-specific container.</span></span>  
  
 <span data-ttu-id="31899-147">下列範例程式碼會使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>多載來檢查指定的資料格式是否可用 (原生或自動轉換)。</span><span class="sxs-lookup"><span data-stu-id="31899-147">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to check if a specified data format is available (native or by auto-convert).</span></span> <span data-ttu-id="31899-148">如果指定的格式可用, 此範例會使用<xref:System.Windows.DataObject.GetData%28System.String%29>方法來抓取資料。</span><span class="sxs-lookup"><span data-stu-id="31899-148">If the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 <span data-ttu-id="31899-149">如需從資料物件中抓取資料之程式碼的更多範例, 請參閱[以特定資料格式抓取資料](how-to-retrieve-data-in-a-particular-data-format.md)。</span><span class="sxs-lookup"><span data-stu-id="31899-149">For more examples of code that retrieves data from a data object, see [Retrieve Data in a Particular Data Format](how-to-retrieve-data-in-a-particular-data-format.md).</span></span>  
  
### <a name="removing-data-from-a-data-object"></a><span data-ttu-id="31899-150">從資料物件移除資料</span><span class="sxs-lookup"><span data-stu-id="31899-150">Removing Data From a Data Object</span></span>  
 <span data-ttu-id="31899-151">資料無法直接從資料物件移除。</span><span class="sxs-lookup"><span data-stu-id="31899-151">Data cannot be directly removed from a data object.</span></span>  <span data-ttu-id="31899-152">若要有效地移除資料物件中的資料, 請遵循下列步驟:</span><span class="sxs-lookup"><span data-stu-id="31899-152">To effectively remove data from a data object, follow these steps:</span></span>  
  
1. <span data-ttu-id="31899-153">建立新的資料物件, 其中只會包含您要保留的資料。</span><span class="sxs-lookup"><span data-stu-id="31899-153">Create a new data object that will contain only the data you want to retain.</span></span>  
  
2. <span data-ttu-id="31899-154">將所需的資料從舊的資料物件「複製」到新的資料物件。</span><span class="sxs-lookup"><span data-stu-id="31899-154">"Copy" the desired data from the old data object to the new data object.</span></span>  <span data-ttu-id="31899-155">若要複製資料, 請使用其中一個<xref:System.Windows.DataObject.GetData%2A>方法來<xref:System.Object>抓取包含原始資料的, 然後使用其中一<xref:System.Windows.DataObject.SetData%2A>種方法將資料加入至新的資料物件。</span><span class="sxs-lookup"><span data-stu-id="31899-155">To copy the data, use one of the <xref:System.Windows.DataObject.GetData%2A> methods to retrieve an <xref:System.Object> that contains the raw data, and then use one of the <xref:System.Windows.DataObject.SetData%2A> methods to add the data to the new data object.</span></span>  
  
3. <span data-ttu-id="31899-156">將舊的資料物件取代為新的物件。</span><span class="sxs-lookup"><span data-stu-id="31899-156">Replace the old data object with the new one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31899-157"><xref:System.Windows.DataObject.SetData%2A>方法只會將資料新增至資料物件, 而不會取代資料, 即使資料和資料格式與先前的呼叫完全相同也一樣。</span><span class="sxs-lookup"><span data-stu-id="31899-157">The <xref:System.Windows.DataObject.SetData%2A> methods only add data to a data object; they do not replace data, even if the data and data format are exactly the same as a previous call.</span></span> <span data-ttu-id="31899-158">針對<xref:System.Windows.DataObject.SetData%2A>相同的資料和資料格式呼叫兩次, 將會導致資料/資料格式出現在資料物件中兩次。</span><span class="sxs-lookup"><span data-stu-id="31899-158">Calling <xref:System.Windows.DataObject.SetData%2A> twice for the same data and data format will result in the data/data format being present twice in the data object.</span></span>
