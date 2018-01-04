---
title: "BindingSource 元件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08b55bc2bd5af78eb6c3d0f5adce3ec39d288a9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="bindingsource-component"></a><span data-ttu-id="10ae1-102">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="10ae1-102">BindingSource Component</span></span>
<span data-ttu-id="10ae1-103">封裝資料來源以繫結至控制項。</span><span class="sxs-lookup"><span data-stu-id="10ae1-103">Encapsulates a data source for binding to controls.</span></span>  
  
 <span data-ttu-id="10ae1-104"><xref:System.Windows.Forms.BindingSource> 元件有兩種用途。</span><span class="sxs-lookup"><span data-stu-id="10ae1-104">The <xref:System.Windows.Forms.BindingSource> component serves two purposes.</span></span> <span data-ttu-id="10ae1-105">首先，在將表單上的控制項繫結至資料時，它會提供一層間接取值。</span><span class="sxs-lookup"><span data-stu-id="10ae1-105">First, it provides a layer of indirection when binding the controls on a form to data.</span></span> <span data-ttu-id="10ae1-106">其作法是將 <xref:System.Windows.Forms.BindingSource> 元件繫結至您的資料來源，然後將表單上的控制項繫結至 <xref:System.Windows.Forms.BindingSource> 元件。</span><span class="sxs-lookup"><span data-stu-id="10ae1-106">This is accomplished by binding the <xref:System.Windows.Forms.BindingSource> component to your data source, and then binding the controls on your form to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="10ae1-107">與資料的所有進一步互動，包括巡覽、排序、篩選和更新，都會透過呼叫 <xref:System.Windows.Forms.BindingSource> 元件來完成。</span><span class="sxs-lookup"><span data-stu-id="10ae1-107">All further interaction with the data, including navigating, sorting, filtering, and updating, is accomplished with calls to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="10ae1-108">第二，<xref:System.Windows.Forms.BindingSource> 元件可以做為強類型資料來源。</span><span class="sxs-lookup"><span data-stu-id="10ae1-108">Second, the <xref:System.Windows.Forms.BindingSource> component can act as a strongly typed data source.</span></span> <span data-ttu-id="10ae1-109">使用 <xref:System.Windows.Forms.BindingSource.Add%2A> 方法將類型加入 <xref:System.Windows.Forms.BindingSource> 元件時，會建立該類型的清單。</span><span class="sxs-lookup"><span data-stu-id="10ae1-109">Adding a type to the <xref:System.Windows.Forms.BindingSource> component with the <xref:System.Windows.Forms.BindingSource.Add%2A> method creates a list of that type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10ae1-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="10ae1-110">In This Section</span></span>  
 [<span data-ttu-id="10ae1-111">BindingSource 元件概觀</span><span class="sxs-lookup"><span data-stu-id="10ae1-111">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 <span data-ttu-id="10ae1-112">介紹 <xref:System.Windows.Forms.BindingSource> 元件的一般概念，此元件可讓您將資料來源繫結至控制項。</span><span class="sxs-lookup"><span data-stu-id="10ae1-112">Introduces the general concepts of the <xref:System.Windows.Forms.BindingSource> component, which allows you to bind a data source to a control.</span></span>  
  
 [<span data-ttu-id="10ae1-113">操作說明：將 Windows Forms 控制項繫結至 DBNull 資料庫值</span><span class="sxs-lookup"><span data-stu-id="10ae1-113">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 <span data-ttu-id="10ae1-114">示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件來處理來自該資料來源的 <xref:System.DBNull> 值。</span><span class="sxs-lookup"><span data-stu-id="10ae1-114">Shows how to handle a <xref:System.DBNull> value from the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="10ae1-115">操作說明：使用 Windows Forms BindingSource 元件排序和篩選 ADO.NET 資料</span><span class="sxs-lookup"><span data-stu-id="10ae1-115">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 <span data-ttu-id="10ae1-116">示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件，將排序和篩選套用至所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="10ae1-116">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to apply sorts and filters to displayed data.</span></span>  
  
 [<span data-ttu-id="10ae1-117">操作說明：使用 Windows Forms BindingSource 繫結至 Web 服務</span><span class="sxs-lookup"><span data-stu-id="10ae1-117">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="10ae1-118">示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件繫結至 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="10ae1-118">Shows how to use the <xref:System.Windows.Forms.BindingSource> component to bind to a Web service.</span></span>  
  
 [<span data-ttu-id="10ae1-119">操作說明：處理資料繫結時所發生的錯誤和例外狀況</span><span class="sxs-lookup"><span data-stu-id="10ae1-119">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 <span data-ttu-id="10ae1-120">示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件，正常處理資料繫結作業中發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="10ae1-120">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to gracefully handle errors that occur in a data binding operation.</span></span>  
  
 [<span data-ttu-id="10ae1-121">操作說明：將 Windows Forms 控制項繫結至型別</span><span class="sxs-lookup"><span data-stu-id="10ae1-121">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 <span data-ttu-id="10ae1-122">示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件繫結至類型。</span><span class="sxs-lookup"><span data-stu-id="10ae1-122">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a type.</span></span>  
  
 [<span data-ttu-id="10ae1-123">操作說明：將 Windows Forms 控制項繫結至 Factory 物件</span><span class="sxs-lookup"><span data-stu-id="10ae1-123">How to: Bind a Windows Forms Control to a Factory Object</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 <span data-ttu-id="10ae1-124">示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件繫結至 Factory 物件或方法。</span><span class="sxs-lookup"><span data-stu-id="10ae1-124">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a factory object or method.</span></span>  
  
 [<span data-ttu-id="10ae1-125">操作說明：使用 Windows Forms BindingSource 自訂加入項目</span><span class="sxs-lookup"><span data-stu-id="10ae1-125">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="10ae1-126">示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件來建立新的項目，並將其加入資料來源中。</span><span class="sxs-lookup"><span data-stu-id="10ae1-126">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to create new items and add them to a data source.</span></span>  
  
 [<span data-ttu-id="10ae1-127">操作說明：使用 BindingSource ResetItem 方法引發變更通知</span><span class="sxs-lookup"><span data-stu-id="10ae1-127">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 <span data-ttu-id="10ae1-128">示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件，針對不支援變更通知的資料來源，引發變更通知事件。</span><span class="sxs-lookup"><span data-stu-id="10ae1-128">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to raise change-notification events for data sources that do not support change notification.</span></span>  
  
 [<span data-ttu-id="10ae1-129">操作說明：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更通知</span><span class="sxs-lookup"><span data-stu-id="10ae1-129">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](../../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 <span data-ttu-id="10ae1-130">示範如何使用繼承自 <xref:System.ComponentModel.INotifyPropertyChanged>，具有 <xref:System.Windows.Forms.BindingSource> 控制項的類型。</span><span class="sxs-lookup"><span data-stu-id="10ae1-130">Demonstrates how to use a type that inherits from the <xref:System.ComponentModel.INotifyPropertyChanged> with a <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
 [<span data-ttu-id="10ae1-131">操作說明：使用 BindingSource 反射 Windows Forms 控制項中的資料來源更新</span><span class="sxs-lookup"><span data-stu-id="10ae1-131">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 <span data-ttu-id="10ae1-132">示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件來回應資料來源中的變更。</span><span class="sxs-lookup"><span data-stu-id="10ae1-132">Demonstrates how to respond to changes in the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="10ae1-133">操作說明：使用 BindingSource 元件跨表單共用繫結資料</span><span class="sxs-lookup"><span data-stu-id="10ae1-133">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 <span data-ttu-id="10ae1-134">示範如何使用 <xref:System.Windows.Forms.BindingSource> 將多個表單繫結至相同的資料來源。</span><span class="sxs-lookup"><span data-stu-id="10ae1-134">Shows how to use the <xref:System.Windows.Forms.BindingSource> to bind multiple forms to the same data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="10ae1-135">參考資料</span><span class="sxs-lookup"><span data-stu-id="10ae1-135">Reference</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="10ae1-136">提供 <xref:System.Windows.Forms.BindingSource> 元件的參考文件。</span><span class="sxs-lookup"><span data-stu-id="10ae1-136">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 <span data-ttu-id="10ae1-137">提供 <xref:System.Windows.Forms.BindingNavigator> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="10ae1-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="10ae1-138">相關章節</span><span class="sxs-lookup"><span data-stu-id="10ae1-138">Related Sections</span></span>  
 [<span data-ttu-id="10ae1-139">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="10ae1-139">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 <span data-ttu-id="10ae1-140">包含描述 Windows Form 資料繫結架構的主題連結。</span><span class="sxs-lookup"><span data-stu-id="10ae1-140">Contains links to topics describing the Windows Forms data binding architecture.</span></span>  
  
 <span data-ttu-id="10ae1-141">另請參閱[在 Visual Studio 中將控制項繫結至資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="10ae1-141">Also see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>
