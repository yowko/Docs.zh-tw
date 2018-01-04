---
title: "如何：建立資料物件"
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
- DataObject class [WPF], creating
- data objects [WPF], creating
- drag-and-drop [WPF], creating data objects
ms.assetid: 022fa142-717d-4fea-a53c-3b52e9d91aff
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 014d5229026a6fdaab203c82932742c7b2c7639e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-data-object"></a><span data-ttu-id="0e74c-102">如何：建立資料物件</span><span class="sxs-lookup"><span data-stu-id="0e74c-102">How to: Create a Data Object</span></span>
<span data-ttu-id="0e74c-103">下列範例顯示建立資料物件，使用所提供的建構函式的各種方式<xref:System.Windows.DataObject>類別。</span><span class="sxs-lookup"><span data-stu-id="0e74c-103">The following examples show various ways to create a data object using the constructors provided by the <xref:System.Windows.DataObject> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e74c-104">範例</span><span class="sxs-lookup"><span data-stu-id="0e74c-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0e74c-105">描述</span><span class="sxs-lookup"><span data-stu-id="0e74c-105">Description</span></span>  
 <span data-ttu-id="0e74c-106">下列範例程式碼會建立新的資料物件，並使用其中一個多載建構函式 (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) 來初始化資料物件的字串。</span><span class="sxs-lookup"><span data-stu-id="0e74c-106">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) to initialize the data object with a string.</span></span>  <span data-ttu-id="0e74c-107">在此情況下，根據儲存的資料類型自動決定適當的資料格式，預設會允許儲存資料的自動轉換。</span><span class="sxs-lookup"><span data-stu-id="0e74c-107">In this case, an appropriate data format is determined automatically according to the stored data's type, and auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0e74c-108">程式碼</span><span class="sxs-lookup"><span data-stu-id="0e74c-108">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### <a name="description"></a><span data-ttu-id="0e74c-109">描述</span><span class="sxs-lookup"><span data-stu-id="0e74c-109">Description</span></span>  
 <span data-ttu-id="0e74c-110">下列程式碼範例是上述程式碼壓縮的版本。</span><span class="sxs-lookup"><span data-stu-id="0e74c-110">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0e74c-111">程式碼</span><span class="sxs-lookup"><span data-stu-id="0e74c-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## <a name="example"></a><span data-ttu-id="0e74c-112">範例</span><span class="sxs-lookup"><span data-stu-id="0e74c-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0e74c-113">描述</span><span class="sxs-lookup"><span data-stu-id="0e74c-113">Description</span></span>  
 <span data-ttu-id="0e74c-114">下列範例程式碼會建立新的資料物件，並使用其中一個多載建構函式 (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) 來初始化資料物件和指定的資料格式的字串。</span><span class="sxs-lookup"><span data-stu-id="0e74c-114">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="0e74c-115">的字串; 在此情況下指定的資料格式<xref:System.Windows.DataFormats>類別會提供一組預先定義的型別字串。</span><span class="sxs-lookup"><span data-stu-id="0e74c-115">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="0e74c-116">根據預設，允許使用預存資料的自動轉換。</span><span class="sxs-lookup"><span data-stu-id="0e74c-116">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0e74c-117">程式碼</span><span class="sxs-lookup"><span data-stu-id="0e74c-117">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### <a name="description"></a><span data-ttu-id="0e74c-118">描述</span><span class="sxs-lookup"><span data-stu-id="0e74c-118">Description</span></span>  
 <span data-ttu-id="0e74c-119">下列程式碼範例是上述程式碼壓縮的版本。</span><span class="sxs-lookup"><span data-stu-id="0e74c-119">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0e74c-120">程式碼</span><span class="sxs-lookup"><span data-stu-id="0e74c-120">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## <a name="example"></a><span data-ttu-id="0e74c-121">範例</span><span class="sxs-lookup"><span data-stu-id="0e74c-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0e74c-122">描述</span><span class="sxs-lookup"><span data-stu-id="0e74c-122">Description</span></span>  
 <span data-ttu-id="0e74c-123">下列範例程式碼會建立新的資料物件，並使用其中一個多載建構函式 (<xref:System.Windows.DataObject.%23ctor%2A>) 來初始化資料物件和指定的資料格式的字串。</span><span class="sxs-lookup"><span data-stu-id="0e74c-123">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%2A>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="0e74c-124">在此情況下所指定的資料格式<xref:System.Type>參數。</span><span class="sxs-lookup"><span data-stu-id="0e74c-124">In this case the data format is specified by a <xref:System.Type> parameter.</span></span>  <span data-ttu-id="0e74c-125">根據預設，允許使用預存資料的自動轉換。</span><span class="sxs-lookup"><span data-stu-id="0e74c-125">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0e74c-126">程式碼</span><span class="sxs-lookup"><span data-stu-id="0e74c-126">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### <a name="description"></a><span data-ttu-id="0e74c-127">描述</span><span class="sxs-lookup"><span data-stu-id="0e74c-127">Description</span></span>  
 <span data-ttu-id="0e74c-128">下列程式碼範例是上述程式碼壓縮的版本。</span><span class="sxs-lookup"><span data-stu-id="0e74c-128">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0e74c-129">程式碼</span><span class="sxs-lookup"><span data-stu-id="0e74c-129">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## <a name="example"></a><span data-ttu-id="0e74c-130">範例</span><span class="sxs-lookup"><span data-stu-id="0e74c-130">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0e74c-131">描述</span><span class="sxs-lookup"><span data-stu-id="0e74c-131">Description</span></span>  
 <span data-ttu-id="0e74c-132">下列範例程式碼會建立新的資料物件，並使用其中一個多載建構函式 (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) 來初始化資料物件和指定的資料格式的字串。</span><span class="sxs-lookup"><span data-stu-id="0e74c-132">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="0e74c-133">的字串; 在此情況下指定的資料格式<xref:System.Windows.DataFormats>類別會提供一組預先定義的型別字串。</span><span class="sxs-lookup"><span data-stu-id="0e74c-133">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="0e74c-134">這個特定的建構函式多載可讓呼叫端指定是否允許自動轉換。</span><span class="sxs-lookup"><span data-stu-id="0e74c-134">This particular constructor overload enables the caller to specify whether auto-converting is allowed.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0e74c-135">程式碼</span><span class="sxs-lookup"><span data-stu-id="0e74c-135">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### <a name="description"></a><span data-ttu-id="0e74c-136">描述</span><span class="sxs-lookup"><span data-stu-id="0e74c-136">Description</span></span>  
 <span data-ttu-id="0e74c-137">下列程式碼範例是上述程式碼壓縮的版本。</span><span class="sxs-lookup"><span data-stu-id="0e74c-137">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0e74c-138">程式碼</span><span class="sxs-lookup"><span data-stu-id="0e74c-138">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## <a name="see-also"></a><span data-ttu-id="0e74c-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="0e74c-139">See Also</span></span>  
 <xref:System.Windows.IDataObject>
