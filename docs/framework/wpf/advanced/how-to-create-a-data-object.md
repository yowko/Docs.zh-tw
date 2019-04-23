---
title: HOW TO：建立資料物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], creating
- data objects [WPF], creating
- drag-and-drop [WPF], creating data objects
ms.assetid: 022fa142-717d-4fea-a53c-3b52e9d91aff
ms.openlocfilehash: deae8751518d9322e8d924a1b1fcbc20e25b35ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771799"
---
# <a name="how-to-create-a-data-object"></a><span data-ttu-id="3b051-102">HOW TO：建立資料物件</span><span class="sxs-lookup"><span data-stu-id="3b051-102">How to: Create a Data Object</span></span>
<span data-ttu-id="3b051-103">下列範例顯示建立資料物件，使用所提供的建構函式的各種方式<xref:System.Windows.DataObject>類別。</span><span class="sxs-lookup"><span data-stu-id="3b051-103">The following examples show various ways to create a data object using the constructors provided by the <xref:System.Windows.DataObject> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b051-104">範例</span><span class="sxs-lookup"><span data-stu-id="3b051-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3b051-105">描述</span><span class="sxs-lookup"><span data-stu-id="3b051-105">Description</span></span>  
 <span data-ttu-id="3b051-106">下列範例程式碼會建立新的資料物件，並使用其中一個多載的建構函式 (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) 來初始化資料物件的字串。</span><span class="sxs-lookup"><span data-stu-id="3b051-106">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) to initialize the data object with a string.</span></span>  <span data-ttu-id="3b051-107">在此情況下，根據儲存的資料類型自動決定適當的資料格式，並允許設定預設的已儲存資料進行自動轉換。</span><span class="sxs-lookup"><span data-stu-id="3b051-107">In this case, an appropriate data format is determined automatically according to the stored data's type, and auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3b051-108">程式碼</span><span class="sxs-lookup"><span data-stu-id="3b051-108">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### <a name="description"></a><span data-ttu-id="3b051-109">描述</span><span class="sxs-lookup"><span data-stu-id="3b051-109">Description</span></span>  
 <span data-ttu-id="3b051-110">下列範例程式碼是如上所示的程式碼的精簡的版本。</span><span class="sxs-lookup"><span data-stu-id="3b051-110">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3b051-111">程式碼</span><span class="sxs-lookup"><span data-stu-id="3b051-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## <a name="example"></a><span data-ttu-id="3b051-112">範例</span><span class="sxs-lookup"><span data-stu-id="3b051-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3b051-113">描述</span><span class="sxs-lookup"><span data-stu-id="3b051-113">Description</span></span>  
 <span data-ttu-id="3b051-114">下列範例程式碼會建立新的資料物件，並使用其中一個多載的建構函式 (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) 來初始化字串與指定的資料格式的資料物件。</span><span class="sxs-lookup"><span data-stu-id="3b051-114">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="3b051-115">在此情況下的字串; 所指定的資料格式<xref:System.Windows.DataFormats>類別提供一組預先定義的型別字串。</span><span class="sxs-lookup"><span data-stu-id="3b051-115">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="3b051-116">根據預設，允許使用的預存的資料進行自動轉換。</span><span class="sxs-lookup"><span data-stu-id="3b051-116">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3b051-117">程式碼</span><span class="sxs-lookup"><span data-stu-id="3b051-117">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### <a name="description"></a><span data-ttu-id="3b051-118">描述</span><span class="sxs-lookup"><span data-stu-id="3b051-118">Description</span></span>  
 <span data-ttu-id="3b051-119">下列範例程式碼是如上所示的程式碼的精簡的版本。</span><span class="sxs-lookup"><span data-stu-id="3b051-119">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3b051-120">程式碼</span><span class="sxs-lookup"><span data-stu-id="3b051-120">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## <a name="example"></a><span data-ttu-id="3b051-121">範例</span><span class="sxs-lookup"><span data-stu-id="3b051-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3b051-122">描述</span><span class="sxs-lookup"><span data-stu-id="3b051-122">Description</span></span>  
 <span data-ttu-id="3b051-123">下列範例程式碼會建立新的資料物件，並使用其中一個多載的建構函式 (<xref:System.Windows.DataObject.%23ctor%2A>) 來初始化字串與指定的資料格式的資料物件。</span><span class="sxs-lookup"><span data-stu-id="3b051-123">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%2A>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="3b051-124">在此情況下所指定的資料格式<xref:System.Type>參數。</span><span class="sxs-lookup"><span data-stu-id="3b051-124">In this case the data format is specified by a <xref:System.Type> parameter.</span></span>  <span data-ttu-id="3b051-125">根據預設，允許使用的預存的資料進行自動轉換。</span><span class="sxs-lookup"><span data-stu-id="3b051-125">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3b051-126">程式碼</span><span class="sxs-lookup"><span data-stu-id="3b051-126">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### <a name="description"></a><span data-ttu-id="3b051-127">描述</span><span class="sxs-lookup"><span data-stu-id="3b051-127">Description</span></span>  
 <span data-ttu-id="3b051-128">下列範例程式碼是如上所示的程式碼的精簡的版本。</span><span class="sxs-lookup"><span data-stu-id="3b051-128">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3b051-129">程式碼</span><span class="sxs-lookup"><span data-stu-id="3b051-129">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## <a name="example"></a><span data-ttu-id="3b051-130">範例</span><span class="sxs-lookup"><span data-stu-id="3b051-130">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3b051-131">描述</span><span class="sxs-lookup"><span data-stu-id="3b051-131">Description</span></span>  
 <span data-ttu-id="3b051-132">下列範例程式碼會建立新的資料物件，並使用其中一個多載的建構函式 (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) 來初始化字串與指定的資料格式的資料物件。</span><span class="sxs-lookup"><span data-stu-id="3b051-132">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="3b051-133">在此情況下的字串; 所指定的資料格式<xref:System.Windows.DataFormats>類別提供一組預先定義的型別字串。</span><span class="sxs-lookup"><span data-stu-id="3b051-133">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="3b051-134">這個特定的建構函式多載可讓呼叫端指定是否允許自動轉換。</span><span class="sxs-lookup"><span data-stu-id="3b051-134">This particular constructor overload enables the caller to specify whether auto-converting is allowed.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3b051-135">程式碼</span><span class="sxs-lookup"><span data-stu-id="3b051-135">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### <a name="description"></a><span data-ttu-id="3b051-136">描述</span><span class="sxs-lookup"><span data-stu-id="3b051-136">Description</span></span>  
 <span data-ttu-id="3b051-137">下列範例程式碼是如上所示的程式碼的精簡的版本。</span><span class="sxs-lookup"><span data-stu-id="3b051-137">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3b051-138">程式碼</span><span class="sxs-lookup"><span data-stu-id="3b051-138">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## <a name="see-also"></a><span data-ttu-id="3b051-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b051-139">See also</span></span>

- <xref:System.Windows.IDataObject>
