---
title: "資料與資料物件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WPF], drag-and-drop
- DataFormats class [WPF]
- DataObject class [WPF]
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb2354b61a0433981675ba55978f31937212cabc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="data-and-data-objects"></a><span data-ttu-id="92f6d-102">資料與資料物件</span><span class="sxs-lookup"><span data-stu-id="92f6d-102">Data and Data Objects</span></span>
<span data-ttu-id="92f6d-103">拖放作業期間傳輸的資料會儲存在資料物件。</span><span class="sxs-lookup"><span data-stu-id="92f6d-103">Data that is transferred as part of a drag-and-drop operation is stored in a data object.</span></span>  <span data-ttu-id="92f6d-104">就概念而言，資料物件包含一或多個下列配對：</span><span class="sxs-lookup"><span data-stu-id="92f6d-104">Conceptually, a data object consists of one or more of the following pairs:</span></span>  
  
-   <span data-ttu-id="92f6d-105"><xref:System.Object> ，其中包含實際資料。</span><span class="sxs-lookup"><span data-stu-id="92f6d-105">An <xref:System.Object> that contains the actual data.</span></span>  
  
-   <span data-ttu-id="92f6d-106">對應的資料格式識別項。</span><span class="sxs-lookup"><span data-stu-id="92f6d-106">A corresponding data format identifier.</span></span>  
  
 <span data-ttu-id="92f6d-107">資料本身可包含的任何項目可以表示做為基底<xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="92f6d-107">The data itself can consist of anything that can be represented as a base <xref:System.Object>.</span></span>  <span data-ttu-id="92f6d-108">對應的資料格式是字串或<xref:System.Type>，提供有關設定資料的格式的提示中。</span><span class="sxs-lookup"><span data-stu-id="92f6d-108">The corresponding data format is a string or <xref:System.Type> that provides a hint about what format the data is in.</span></span>  <span data-ttu-id="92f6d-109">資料物件支援裝載的多個/資料格式配對。這可讓單一資料物件，提供以多種格式的資料。</span><span class="sxs-lookup"><span data-stu-id="92f6d-109">Data objects support hosting multiple data/data format pairs; this enables a single data object to provide data in multiple formats.</span></span>  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a><span data-ttu-id="92f6d-110">資料物件</span><span class="sxs-lookup"><span data-stu-id="92f6d-110">Data Objects</span></span>  
 <span data-ttu-id="92f6d-111">所有資料物件必須都實作<xref:System.Windows.IDataObject>介面，提供下列一組標準的方法，啟用並加速資料傳輸方法。</span><span class="sxs-lookup"><span data-stu-id="92f6d-111">All data objects must implement the <xref:System.Windows.IDataObject> interface, which provides the following standard set of methods that enable and facilitate data transfer.</span></span>  
  
|<span data-ttu-id="92f6d-112">方法</span><span class="sxs-lookup"><span data-stu-id="92f6d-112">Method</span></span>|<span data-ttu-id="92f6d-113">總結</span><span class="sxs-lookup"><span data-stu-id="92f6d-113">Summary</span></span>|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|<span data-ttu-id="92f6d-114">擷取指定之資料格式的資料物件。</span><span class="sxs-lookup"><span data-stu-id="92f6d-114">Retrieves a data object in a specified data format.</span></span>|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|<span data-ttu-id="92f6d-115">檢查資料是否可用，或可以轉換成指定的格式。</span><span class="sxs-lookup"><span data-stu-id="92f6d-115">Checks to see whether the data is available in, or can be converted to, a specified format.</span></span>|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|<span data-ttu-id="92f6d-116">傳回這個資料物件中的資料會儲存在中，或可以轉換成的格式清單。</span><span class="sxs-lookup"><span data-stu-id="92f6d-116">Returns a list of formats that the data in this data object is stored in, or can be converted to.</span></span>|  
|<xref:System.Windows.IDataObject.SetData%2A>|<span data-ttu-id="92f6d-117">指定的資料儲存於這個資料物件。</span><span class="sxs-lookup"><span data-stu-id="92f6d-117">Stores the specified data in this data object.</span></span>|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="92f6d-118">提供的基本實作<xref:System.Windows.IDataObject>中<xref:System.Windows.DataObject>類別。</span><span class="sxs-lookup"><span data-stu-id="92f6d-118"> provides a basic implementation of <xref:System.Windows.IDataObject> in the <xref:System.Windows.DataObject> class.</span></span> <span data-ttu-id="92f6d-119">股票<xref:System.Windows.DataObject>類別已足以應付許多常見的資料傳輸案例。</span><span class="sxs-lookup"><span data-stu-id="92f6d-119">The stock <xref:System.Windows.DataObject> class is sufficient for many common data transfer scenarios.</span></span>  
  
 <span data-ttu-id="92f6d-120">有數個預先定義的格式，例如點陣圖、 CSV、 檔案、 HTML、 RTF、 字串、 文字和音訊。</span><span class="sxs-lookup"><span data-stu-id="92f6d-120">There are several pre-defined formats, such as bitmap, CSV, file, HTML, RTF, string, text, and audio.</span></span> <span data-ttu-id="92f6d-121">如需隨附的預先定義的資料格式資訊[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，請參閱<xref:System.Windows.DataFormats>類別參考主題。</span><span class="sxs-lookup"><span data-stu-id="92f6d-121">For information about pre-defined data formats provided with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see the <xref:System.Windows.DataFormats> class reference topic.</span></span>  
  
 <span data-ttu-id="92f6d-122">資料物件通常包括設備，以用於自動轉換資料儲存在不同格式的一種格式，在擷取資料;此功能稱為自動轉換。</span><span class="sxs-lookup"><span data-stu-id="92f6d-122">Data objects commonly include a facility for automatically converting data stored in one format to a different format while extracting data; this facility is referred to as auto-convert.</span></span> <span data-ttu-id="92f6d-123">查詢時資料物件中可用的資料格式，自動轉換的資料格式可以篩選從原生資料格式藉由呼叫<xref:System.Windows.DataObject.GetFormats%28System.Boolean%29>或<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>方法並指定`autoConvert`參數做為`false`。</span><span class="sxs-lookup"><span data-stu-id="92f6d-123">When querying for the data formats available in a data object, auto-convertible data formats can be filtered from native data formats by calling the <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> or <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> method and specifying the `autoConvert` parameter as `false`.</span></span>  <span data-ttu-id="92f6d-124">將資料加入至資料物件，但<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>方法時，資料的自動轉換可以藉由設定禁止`autoConvert`參數`false`。</span><span class="sxs-lookup"><span data-stu-id="92f6d-124">When adding data to a data object with the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> method, auto-conversion of data can be prohibited by setting the `autoConvert` parameter to `false`.</span></span>  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a><span data-ttu-id="92f6d-125">使用資料物件</span><span class="sxs-lookup"><span data-stu-id="92f6d-125">Working with Data Objects</span></span>  
 <span data-ttu-id="92f6d-126">本章節描述常見的技巧，用於建立和使用資料物件。</span><span class="sxs-lookup"><span data-stu-id="92f6d-126">This section describes common techniques for creating and working with data objects.</span></span>  
  
### <a name="creating-new-data-objects"></a><span data-ttu-id="92f6d-127">建立新的資料物件</span><span class="sxs-lookup"><span data-stu-id="92f6d-127">Creating New Data Objects</span></span>  
 <span data-ttu-id="92f6d-128"><xref:System.Windows.DataObject>類別提供數個多載建構函式，以便填入新<xref:System.Windows.DataObject>單一/資料格式組的執行個體。</span><span class="sxs-lookup"><span data-stu-id="92f6d-128">The <xref:System.Windows.DataObject> class provides several overloaded constructors that facilitate populating a new <xref:System.Windows.DataObject> instance with a single data/data format pair.</span></span>  
  
 <span data-ttu-id="92f6d-129">下列範例程式碼會建立新的資料物件，並使用其中一個多載建構函式<xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) 來初始化資料物件和指定的資料格式的字串。</span><span class="sxs-lookup"><span data-stu-id="92f6d-129">The following example code creates a new data object and uses one of the overloaded constructors <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="92f6d-130">在此情況下，字串; 字串所指定的資料格式<xref:System.Windows.DataFormats>類別會提供一組預先定義的型別字串。</span><span class="sxs-lookup"><span data-stu-id="92f6d-130">In this case, the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="92f6d-131">預設為允許自動轉換儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="92f6d-131">Auto-conversion of the stored data is allowed by default.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 <span data-ttu-id="92f6d-132">如需建立資料物件的程式碼範例，請參閱[建立資料物件](../../../../docs/framework/wpf/advanced/how-to-create-a-data-object.md)。</span><span class="sxs-lookup"><span data-stu-id="92f6d-132">For more examples of code that creates a data object, see [Create a Data Object](../../../../docs/framework/wpf/advanced/how-to-create-a-data-object.md).</span></span>  
  
### <a name="storing-data-in-multiple-formats"></a><span data-ttu-id="92f6d-133">以多種格式儲存資料</span><span class="sxs-lookup"><span data-stu-id="92f6d-133">Storing Data in Multiple Formats</span></span>  
 <span data-ttu-id="92f6d-134">單一資料物件都能夠以多種格式儲存資料。</span><span class="sxs-lookup"><span data-stu-id="92f6d-134">A single data object is able to store data in multiple formats.</span></span>   <span data-ttu-id="92f6d-135">策略使用多個單一資料物件中的資料格式可能會使資料物件更廣泛的置放目標比可取用如果只有單一資料格式可能會表示。</span><span class="sxs-lookup"><span data-stu-id="92f6d-135">Strategic use of multiple data formats within a single data object potentially makes the data object consumable by a wider variety of drop targets than if only a single data format could be represented.</span></span>  <span data-ttu-id="92f6d-136">請注意，在一般情況下，拖曳來源必須是無從驗證相關的資料格式會使用可能的置放目標。</span><span class="sxs-lookup"><span data-stu-id="92f6d-136">Note that, in general, a drag source must be agnostic about the data formats that are consumable by potential drop targets.</span></span>  
  
 <span data-ttu-id="92f6d-137">下列範例示範如何使用<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>方法，以將資料加入至多個格式中的資料物件。</span><span class="sxs-lookup"><span data-stu-id="92f6d-137">The following example shows how to use the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> method to add data to a data object in multiple formats.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a><span data-ttu-id="92f6d-138">查詢可用的格式資料物件</span><span class="sxs-lookup"><span data-stu-id="92f6d-138">Querying a Data Object for Available Formats</span></span>  
 <span data-ttu-id="92f6d-139">單一資料物件可以包含任意數目的資料格式，因為資料物件包含設備來擷取可用的資料格式的清單。</span><span class="sxs-lookup"><span data-stu-id="92f6d-139">Because a single data object can contain an arbitrary number of data formats, data objects include facilities for retrieving a list of available data formats.</span></span>  
  
 <span data-ttu-id="92f6d-140">下列範例程式碼使用<xref:System.Windows.DataObject.GetFormats%2A>多載來取得代表可用資料物件 （原生和的自動轉換） 中的所有資料格式的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="92f6d-140">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and by auto-convert).</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 <span data-ttu-id="92f6d-141">查詢可用的資料格式的資料物件的程式碼的其他範例，請參閱[清單資料物件中的資料格式](../../../../docs/framework/wpf/advanced/how-to-list-the-data-formats-in-a-data-object.md)。</span><span class="sxs-lookup"><span data-stu-id="92f6d-141">For more examples of code that queries a data object for available data formats, see [List the Data Formats in a Data Object](../../../../docs/framework/wpf/advanced/how-to-list-the-data-formats-in-a-data-object.md).</span></span>  <span data-ttu-id="92f6d-142">如需更多的查詢是否存在特定的資料格式的資料物件的範例，請參閱[判斷是否存在的資料格式資料物件中](../../../../docs/framework/wpf/advanced/how-to-determine-if-a-data-format-is-present-in-a-data-object.md)。</span><span class="sxs-lookup"><span data-stu-id="92f6d-142">For examples of querying a data object for the presence of a particular data format, see [Determine if a Data Format is Present in a Data Object](../../../../docs/framework/wpf/advanced/how-to-determine-if-a-data-format-is-present-in-a-data-object.md).</span></span>  
  
### <a name="retrieving-data-from-a-data-object"></a><span data-ttu-id="92f6d-143">從資料物件擷取資料</span><span class="sxs-lookup"><span data-stu-id="92f6d-143">Retrieving Data from a Data Object</span></span>  
 <span data-ttu-id="92f6d-144">從特定格式的資料物件擷取資料，只涉及呼叫其中一個<xref:System.Windows.DataObject.GetData%2A>方法並指定所需的資料格式。</span><span class="sxs-lookup"><span data-stu-id="92f6d-144">Retrieving data from a data object in a particular format simply involves calling one of the <xref:System.Windows.DataObject.GetData%2A> methods and specifying the desired data format.</span></span>  <span data-ttu-id="92f6d-145">其中一個<xref:System.Windows.DataObject.GetDataPresent%2A>方法可以用來檢查是否有特定的資料格式。</span><span class="sxs-lookup"><span data-stu-id="92f6d-145">One of the <xref:System.Windows.DataObject.GetDataPresent%2A> methods can be used to check for the presence of a particular data format.</span></span>  <span data-ttu-id="92f6d-146"><xref:System.Windows.DataObject.GetData%2A>會將資料<xref:System.Object>; 視資料格式，這個物件可以轉換成特定類型的容器。</span><span class="sxs-lookup"><span data-stu-id="92f6d-146"><xref:System.Windows.DataObject.GetData%2A> returns the data in an <xref:System.Object>; depending on the data format, this object can be cast to a type-specific container.</span></span>  
  
 <span data-ttu-id="92f6d-147">下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>多載，以檢查是否可以使用指定的資料格式 （原生或自動轉換）。</span><span class="sxs-lookup"><span data-stu-id="92f6d-147">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to check if a specified data format is available (native or by auto-convert).</span></span> <span data-ttu-id="92f6d-148">如果指定的格式使用時，此範例會擷取資料使用<xref:System.Windows.DataObject.GetData%28System.String%29>方法。</span><span class="sxs-lookup"><span data-stu-id="92f6d-148">If the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 <span data-ttu-id="92f6d-149">如需詳細的範例程式碼會從資料物件擷取資料，請參閱[擷取特定的資料格式的資料](../../../../docs/framework/wpf/advanced/how-to-retrieve-data-in-a-particular-data-format.md)。</span><span class="sxs-lookup"><span data-stu-id="92f6d-149">For more examples of code that retrieves data from a data object, see [Retrieve Data in a Particular Data Format](../../../../docs/framework/wpf/advanced/how-to-retrieve-data-in-a-particular-data-format.md).</span></span>  
  
### <a name="removing-data-from-a-data-object"></a><span data-ttu-id="92f6d-150">從資料物件中移除資料</span><span class="sxs-lookup"><span data-stu-id="92f6d-150">Removing Data From a Data Object</span></span>  
 <span data-ttu-id="92f6d-151">無法直接移除資料，從資料物件。</span><span class="sxs-lookup"><span data-stu-id="92f6d-151">Data cannot be directly removed from a data object.</span></span>  <span data-ttu-id="92f6d-152">若要有效地從資料物件中移除資料，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="92f6d-152">To effectively remove data from a data object, follow these steps:</span></span>  
  
1.  <span data-ttu-id="92f6d-153">建立新的資料物件會包含只有您想要保留的資料。</span><span class="sxs-lookup"><span data-stu-id="92f6d-153">Create a new data object that will contain only the data you want to retain.</span></span>  
  
2.  <span data-ttu-id="92f6d-154">「 複製 」 所需的資料從舊的資料物件至新的資料物件。</span><span class="sxs-lookup"><span data-stu-id="92f6d-154">"Copy" the desired data from the old data object to the new data object.</span></span>  <span data-ttu-id="92f6d-155">若要複製資料，請使用其中一種<xref:System.Windows.DataObject.GetData%2A>方法來擷取<xref:System.Object>包含原始資料，但使用其中一個<xref:System.Windows.DataObject.SetData%2A>方法，以將資料加入至新的資料物件。</span><span class="sxs-lookup"><span data-stu-id="92f6d-155">To copy the data, use one of the <xref:System.Windows.DataObject.GetData%2A> methods to retrieve an <xref:System.Object> that contains the raw data, and then use one of the <xref:System.Windows.DataObject.SetData%2A> methods to add the data to the new data object.</span></span>  
  
3.  <span data-ttu-id="92f6d-156">取代新舊資料物件。</span><span class="sxs-lookup"><span data-stu-id="92f6d-156">Replace the old data object with the new one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92f6d-157"><xref:System.Windows.DataObject.SetData%2A>方法只會將資料加入至資料物件，即使資料和資料格式並完全相同的上一個呼叫，但是並無法取代資料，則為。</span><span class="sxs-lookup"><span data-stu-id="92f6d-157">The <xref:System.Windows.DataObject.SetData%2A> methods only add data to a data object; they do not replace data, even if the data and data format are exactly the same as a previous call.</span></span> <span data-ttu-id="92f6d-158">呼叫<xref:System.Windows.DataObject.SetData%2A>兩次的相同資料和資料格式會導致出現兩次資料物件中的資料/資料格式。</span><span class="sxs-lookup"><span data-stu-id="92f6d-158">Calling <xref:System.Windows.DataObject.SetData%2A> twice for the same data and data format will result in the data/data format being present twice in the data object.</span></span>
