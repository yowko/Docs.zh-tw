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
# <a name="data-and-data-objects"></a><span data-ttu-id="679cb-102">資料與資料物件</span><span class="sxs-lookup"><span data-stu-id="679cb-102">Data and Data Objects</span></span>
<span data-ttu-id="679cb-103">作為拖放操作的一部分傳輸的資料存儲在資料物件中。</span><span class="sxs-lookup"><span data-stu-id="679cb-103">Data that is transferred as part of a drag-and-drop operation is stored in a data object.</span></span>  <span data-ttu-id="679cb-104">從概念上講，資料物件由以下一個或多個對組成：</span><span class="sxs-lookup"><span data-stu-id="679cb-104">Conceptually, a data object consists of one or more of the following pairs:</span></span>  
  
- <span data-ttu-id="679cb-105">包含<xref:System.Object>實際資料的 。</span><span class="sxs-lookup"><span data-stu-id="679cb-105">An <xref:System.Object> that contains the actual data.</span></span>  
  
- <span data-ttu-id="679cb-106">相應的資料格式識別碼。</span><span class="sxs-lookup"><span data-stu-id="679cb-106">A corresponding data format identifier.</span></span>  
  
 <span data-ttu-id="679cb-107">資料本身可以包含任何可以表示為基<xref:System.Object>的。</span><span class="sxs-lookup"><span data-stu-id="679cb-107">The data itself can consist of anything that can be represented as a base <xref:System.Object>.</span></span>  <span data-ttu-id="679cb-108">相應的資料格式是字串，或<xref:System.Type>提供有關資料格式的提示。</span><span class="sxs-lookup"><span data-stu-id="679cb-108">The corresponding data format is a string or <xref:System.Type> that provides a hint about what format the data is in.</span></span>  <span data-ttu-id="679cb-109">資料物件支援託管多個資料/資料格式對;這使單個資料物件能夠以多種格式提供資料。</span><span class="sxs-lookup"><span data-stu-id="679cb-109">Data objects support hosting multiple data/data format pairs; this enables a single data object to provide data in multiple formats.</span></span>  
  
<a name="Data_and_Data_Objects"></a>
## <a name="data-objects"></a><span data-ttu-id="679cb-110">資料物件</span><span class="sxs-lookup"><span data-stu-id="679cb-110">Data Objects</span></span>  
 <span data-ttu-id="679cb-111">所有資料物件都必須實現<xref:System.Windows.IDataObject>介面，該介面提供以下支援和促進資料傳輸的標準方法集。</span><span class="sxs-lookup"><span data-stu-id="679cb-111">All data objects must implement the <xref:System.Windows.IDataObject> interface, which provides the following standard set of methods that enable and facilitate data transfer.</span></span>  
  
|<span data-ttu-id="679cb-112">方法</span><span class="sxs-lookup"><span data-stu-id="679cb-112">Method</span></span>|<span data-ttu-id="679cb-113">摘要</span><span class="sxs-lookup"><span data-stu-id="679cb-113">Summary</span></span>|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|<span data-ttu-id="679cb-114">以指定的資料格式擷取資料物件。</span><span class="sxs-lookup"><span data-stu-id="679cb-114">Retrieves a data object in a specified data format.</span></span>|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|<span data-ttu-id="679cb-115">檢查資料是否以指定的格式儲存，或是否可轉換成指定的格式。</span><span class="sxs-lookup"><span data-stu-id="679cb-115">Checks to see whether the data is available in, or can be converted to, a specified format.</span></span>|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|<span data-ttu-id="679cb-116">傳回格式清單，這個資料物件中的資料是以這些格式儲存，或是可以轉換成這些格式。</span><span class="sxs-lookup"><span data-stu-id="679cb-116">Returns a list of formats that the data in this data object is stored in, or can be converted to.</span></span>|  
|<xref:System.Windows.IDataObject.SetData%2A>|<span data-ttu-id="679cb-117">將指定的資料儲存到這個資料物件中。</span><span class="sxs-lookup"><span data-stu-id="679cb-117">Stores the specified data in this data object.</span></span>|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="679cb-118">在<xref:System.Windows.DataObject>類中提供了<xref:System.Windows.IDataObject>的基本實現。</span><span class="sxs-lookup"><span data-stu-id="679cb-118">provides a basic implementation of <xref:System.Windows.IDataObject> in the <xref:System.Windows.DataObject> class.</span></span> <span data-ttu-id="679cb-119">股票<xref:System.Windows.DataObject>類足以用於許多常見的資料傳輸方案。</span><span class="sxs-lookup"><span data-stu-id="679cb-119">The stock <xref:System.Windows.DataObject> class is sufficient for many common data transfer scenarios.</span></span>  
  
 <span data-ttu-id="679cb-120">有幾種預定義的格式，如點陣圖、CSV、檔、HTML、RTF、字串、文本和音訊。</span><span class="sxs-lookup"><span data-stu-id="679cb-120">There are several pre-defined formats, such as bitmap, CSV, file, HTML, RTF, string, text, and audio.</span></span> <span data-ttu-id="679cb-121">有關 隨提供的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]預定義資料格式的資訊，<xref:System.Windows.DataFormats>請參閱類引用主題。</span><span class="sxs-lookup"><span data-stu-id="679cb-121">For information about pre-defined data formats provided with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see the <xref:System.Windows.DataFormats> class reference topic.</span></span>  
  
 <span data-ttu-id="679cb-122">資料物件通常包括一個工具，用於在提取資料時自動將存儲在一種格式的資料轉換為其他格式;此設施稱為自動轉換。</span><span class="sxs-lookup"><span data-stu-id="679cb-122">Data objects commonly include a facility for automatically converting data stored in one format to a different format while extracting data; this facility is referred to as auto-convert.</span></span> <span data-ttu-id="679cb-123">查詢資料物件中可用的資料格式時，可以通過調用<xref:System.Windows.DataObject.GetFormats%28System.Boolean%29>或<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>方法並將`autoConvert`參數指定為`false`從本機資料格式篩選自動可轉換資料格式。</span><span class="sxs-lookup"><span data-stu-id="679cb-123">When querying for the data formats available in a data object, auto-convertible data formats can be filtered from native data formats by calling the <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> or <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> method and specifying the `autoConvert` parameter as `false`.</span></span>  <span data-ttu-id="679cb-124">使用<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>方法將資料添加到資料物件時，可以通過將`autoConvert`參數設置為`false`禁止自動轉換資料。</span><span class="sxs-lookup"><span data-stu-id="679cb-124">When adding data to a data object with the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> method, auto-conversion of data can be prohibited by setting the `autoConvert` parameter to `false`.</span></span>  
  
<a name="Working_with_Data_Objects"></a>
## <a name="working-with-data-objects"></a><span data-ttu-id="679cb-125">使用資料物件</span><span class="sxs-lookup"><span data-stu-id="679cb-125">Working with Data Objects</span></span>  
 <span data-ttu-id="679cb-126">本節介紹創建和使用資料物件的常用技術。</span><span class="sxs-lookup"><span data-stu-id="679cb-126">This section describes common techniques for creating and working with data objects.</span></span>  
  
### <a name="creating-new-data-objects"></a><span data-ttu-id="679cb-127">創建新資料物件</span><span class="sxs-lookup"><span data-stu-id="679cb-127">Creating New Data Objects</span></span>  
 <span data-ttu-id="679cb-128">該<xref:System.Windows.DataObject>類提供了多個重載建構函式，便於使用單個資料/資料<xref:System.Windows.DataObject>格式對填充新實例。</span><span class="sxs-lookup"><span data-stu-id="679cb-128">The <xref:System.Windows.DataObject> class provides several overloaded constructors that facilitate populating a new <xref:System.Windows.DataObject> instance with a single data/data format pair.</span></span>  
  
 <span data-ttu-id="679cb-129">以下示例代碼創建新的資料物件，並使用其中一個重載建構函式<xref:System.Windows.DataObject.%23ctor%2A>（<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>） 使用字串和指定的資料格式初始化資料物件。</span><span class="sxs-lookup"><span data-stu-id="679cb-129">The following example code creates a new data object and uses one of the overloaded constructors <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="679cb-130">在這種情況下，資料格式由字串指定;例如，資料格式由字串指定。類<xref:System.Windows.DataFormats>提供一組預定義的類型字串。</span><span class="sxs-lookup"><span data-stu-id="679cb-130">In this case, the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="679cb-131">預設情況下允許自動轉換存儲的資料。</span><span class="sxs-lookup"><span data-stu-id="679cb-131">Auto-conversion of the stored data is allowed by default.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 <span data-ttu-id="679cb-132">有關創建資料物件的代碼的更多示例，請參閱[創建資料物件](how-to-create-a-data-object.md)。</span><span class="sxs-lookup"><span data-stu-id="679cb-132">For more examples of code that creates a data object, see [Create a Data Object](how-to-create-a-data-object.md).</span></span>  
  
### <a name="storing-data-in-multiple-formats"></a><span data-ttu-id="679cb-133">以多種格式存儲資料</span><span class="sxs-lookup"><span data-stu-id="679cb-133">Storing Data in Multiple Formats</span></span>  
 <span data-ttu-id="679cb-134">單個資料物件能夠以多種格式存儲資料。</span><span class="sxs-lookup"><span data-stu-id="679cb-134">A single data object is able to store data in multiple formats.</span></span>   <span data-ttu-id="679cb-135">在單個資料物件中戰略性地使用多種資料格式，可能會使資料物件被更廣泛的放置目標所消耗，而如果只能表示單個資料格式。</span><span class="sxs-lookup"><span data-stu-id="679cb-135">Strategic use of multiple data formats within a single data object potentially makes the data object consumable by a wider variety of drop targets than if only a single data format could be represented.</span></span>  <span data-ttu-id="679cb-136">請注意，通常，拖動源必須與潛在放置目標可消耗的資料格式無關。</span><span class="sxs-lookup"><span data-stu-id="679cb-136">Note that, in general, a drag source must be agnostic about the data formats that are consumable by potential drop targets.</span></span>  
  
 <span data-ttu-id="679cb-137">下面的示例演示如何使用 方法<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>以多種格式將資料添加到資料物件。</span><span class="sxs-lookup"><span data-stu-id="679cb-137">The following example shows how to use the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> method to add data to a data object in multiple formats.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a><span data-ttu-id="679cb-138">查詢資料物件以獲取可用格式</span><span class="sxs-lookup"><span data-stu-id="679cb-138">Querying a Data Object for Available Formats</span></span>  
 <span data-ttu-id="679cb-139">由於單個資料物件可以包含任意數量的資料格式，因此資料物件包括用於檢索可用資料格式清單的功能。</span><span class="sxs-lookup"><span data-stu-id="679cb-139">Because a single data object can contain an arbitrary number of data formats, data objects include facilities for retrieving a list of available data formats.</span></span>  
  
 <span data-ttu-id="679cb-140">下面的示例代碼使用<xref:System.Windows.DataObject.GetFormats%2A>重載獲取一個字串陣列，表示資料物件（本機和自動轉換）中可用的所有資料格式。</span><span class="sxs-lookup"><span data-stu-id="679cb-140">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and by auto-convert).</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 <span data-ttu-id="679cb-141">有關查詢資料物件可用資料格式的代碼的更多示例，請參閱[在資料物件中列出資料格式](how-to-list-the-data-formats-in-a-data-object.md)。</span><span class="sxs-lookup"><span data-stu-id="679cb-141">For more examples of code that queries a data object for available data formats, see [List the Data Formats in a Data Object](how-to-list-the-data-formats-in-a-data-object.md).</span></span>  <span data-ttu-id="679cb-142">有關查詢資料物件是否存在特定資料格式的示例，請參閱[確定資料物件中是否存在資料格式](how-to-determine-if-a-data-format-is-present-in-a-data-object.md)。</span><span class="sxs-lookup"><span data-stu-id="679cb-142">For examples of querying a data object for the presence of a particular data format, see [Determine if a Data Format is Present in a Data Object](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).</span></span>  
  
### <a name="retrieving-data-from-a-data-object"></a><span data-ttu-id="679cb-143">從資料物件檢索資料</span><span class="sxs-lookup"><span data-stu-id="679cb-143">Retrieving Data from a Data Object</span></span>  
 <span data-ttu-id="679cb-144">以特定格式從資料物件檢索資料只需調用其中一<xref:System.Windows.DataObject.GetData%2A>種方法並指定所需的資料格式。</span><span class="sxs-lookup"><span data-stu-id="679cb-144">Retrieving data from a data object in a particular format simply involves calling one of the <xref:System.Windows.DataObject.GetData%2A> methods and specifying the desired data format.</span></span>  <span data-ttu-id="679cb-145">其中一<xref:System.Windows.DataObject.GetDataPresent%2A>種方法可用於檢查是否存在特定資料格式。</span><span class="sxs-lookup"><span data-stu-id="679cb-145">One of the <xref:System.Windows.DataObject.GetDataPresent%2A> methods can be used to check for the presence of a particular data format.</span></span>  <span data-ttu-id="679cb-146"><xref:System.Windows.DataObject.GetData%2A>返回 中的<xref:System.Object>資料。根據資料格式，此物件可以強制轉換為特定于類型的容器。</span><span class="sxs-lookup"><span data-stu-id="679cb-146"><xref:System.Windows.DataObject.GetData%2A> returns the data in an <xref:System.Object>; depending on the data format, this object can be cast to a type-specific container.</span></span>  
  
 <span data-ttu-id="679cb-147">以下示例代碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>重載來檢查指定的資料格式是否可用（本機還是自動轉換）。</span><span class="sxs-lookup"><span data-stu-id="679cb-147">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to check if a specified data format is available (native or by auto-convert).</span></span> <span data-ttu-id="679cb-148">如果指定的格式可用，則示例使用 方法<xref:System.Windows.DataObject.GetData%28System.String%29>檢索資料。</span><span class="sxs-lookup"><span data-stu-id="679cb-148">If the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 <span data-ttu-id="679cb-149">有關從資料物件檢索資料的代碼的更多示例，請參閱[以特定資料格式檢索資料](how-to-retrieve-data-in-a-particular-data-format.md)。</span><span class="sxs-lookup"><span data-stu-id="679cb-149">For more examples of code that retrieves data from a data object, see [Retrieve Data in a Particular Data Format](how-to-retrieve-data-in-a-particular-data-format.md).</span></span>  
  
### <a name="removing-data-from-a-data-object"></a><span data-ttu-id="679cb-150">從資料物件中刪除資料</span><span class="sxs-lookup"><span data-stu-id="679cb-150">Removing Data From a Data Object</span></span>  
 <span data-ttu-id="679cb-151">無法直接從資料物件中刪除資料。</span><span class="sxs-lookup"><span data-stu-id="679cb-151">Data cannot be directly removed from a data object.</span></span>  <span data-ttu-id="679cb-152">要有效地從資料物件中刪除資料，請按照以下步驟操作：</span><span class="sxs-lookup"><span data-stu-id="679cb-152">To effectively remove data from a data object, follow these steps:</span></span>  
  
1. <span data-ttu-id="679cb-153">創建新的資料物件，該物件僅包含要保留的資料。</span><span class="sxs-lookup"><span data-stu-id="679cb-153">Create a new data object that will contain only the data you want to retain.</span></span>  
  
2. <span data-ttu-id="679cb-154">將所需資料從舊資料物件"複製到新資料物件"。</span><span class="sxs-lookup"><span data-stu-id="679cb-154">"Copy" the desired data from the old data object to the new data object.</span></span>  <span data-ttu-id="679cb-155">若要複製資料，請使用其中一<xref:System.Windows.DataObject.GetData%2A>種方法檢索包含原始資料的<xref:System.Object>， 然後使用其中一<xref:System.Windows.DataObject.SetData%2A>種方法將資料添加到新的資料物件。</span><span class="sxs-lookup"><span data-stu-id="679cb-155">To copy the data, use one of the <xref:System.Windows.DataObject.GetData%2A> methods to retrieve an <xref:System.Object> that contains the raw data, and then use one of the <xref:System.Windows.DataObject.SetData%2A> methods to add the data to the new data object.</span></span>  
  
3. <span data-ttu-id="679cb-156">將舊資料物件替換為新資料物件。</span><span class="sxs-lookup"><span data-stu-id="679cb-156">Replace the old data object with the new one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="679cb-157">這些方法<xref:System.Windows.DataObject.SetData%2A>僅將資料添加到資料物件;它們不會替換資料，即使資料和資料格式與上一個調用完全相同。</span><span class="sxs-lookup"><span data-stu-id="679cb-157">The <xref:System.Windows.DataObject.SetData%2A> methods only add data to a data object; they do not replace data, even if the data and data format are exactly the same as a previous call.</span></span> <span data-ttu-id="679cb-158">調用<xref:System.Windows.DataObject.SetData%2A>相同資料和資料格式兩次將導致資料/資料格式在資料物件中存在兩次。</span><span class="sxs-lookup"><span data-stu-id="679cb-158">Calling <xref:System.Windows.DataObject.SetData%2A> twice for the same data and data format will result in the data/data format being present twice in the data object.</span></span>
