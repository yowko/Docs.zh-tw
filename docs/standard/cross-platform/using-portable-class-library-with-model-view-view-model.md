---
title: 搭配 Model-View-View 模型使用可攜式類別庫
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b53be90764c6537fb27cb1b5ed781a68e69effa0
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504670"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="83b16-102">搭配 Model-View-View 模型使用可攜式類別庫</span><span class="sxs-lookup"><span data-stu-id="83b16-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="83b16-103">您可以使用.NET Framework[可攜式類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)實作模型檢視 View Model (MVVM) 模式，並跨多個平台共用的組件。</span><span class="sxs-lookup"><span data-stu-id="83b16-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="83b16-104">MVVM 是將使用者介面與基礎商務邏輯隔離的應用程式模式。</span><span class="sxs-lookup"><span data-stu-id="83b16-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="83b16-105">您可以在 Visual Studio 2012 中，可攜式類別庫專案中實作模型和檢視模型類別，然後再建立自訂的不同平台的檢視。</span><span class="sxs-lookup"><span data-stu-id="83b16-105">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="83b16-106">這個方法讓您只需撰寫資料模型和商務邏輯一次，就可以從 .NET Framework、Silverlight、Windows Phone 和 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式使用該程式碼，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="83b16-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps, as shown in the following illustration.</span></span>

 ![顯示跨平台的可攜式類別庫搭配 MVVM 共用組件。](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="83b16-108">本主題不提供 MVVM 模式的一般資訊。</span><span class="sxs-lookup"><span data-stu-id="83b16-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="83b16-109">此外，它只會提供有關如何實作 MVVM 使用可攜式類別庫的資訊。</span><span class="sxs-lookup"><span data-stu-id="83b16-109">It only provides information about how to use Portable Class Library to implement MVVM.</span></span> <span data-ttu-id="83b16-110">如需 MVVM 的詳細資訊，請參閱[MVVM 快速入門使用 Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40))。</span><span class="sxs-lookup"><span data-stu-id="83b16-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="83b16-111">支援 MVVM 類別</span><span class="sxs-lookup"><span data-stu-id="83b16-111">Classes That Support MVVM</span></span>
 <span data-ttu-id="83b16-112">.NET Framework 4.5 為目標時[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]，Silverlight 或 Windows Phone 7.5，可攜式類別庫專案，下列類別可供實作 MVVM 模式：</span><span class="sxs-lookup"><span data-stu-id="83b16-112">When you target the .NET Framework 4.5, [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="83b16-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="83b16-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="83b16-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="83b16-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="83b16-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="83b16-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="83b16-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="83b16-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="83b16-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="83b16-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="83b16-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="83b16-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="83b16-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="83b16-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="83b16-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="83b16-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="83b16-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="83b16-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="83b16-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="83b16-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="83b16-123">中的所有類別<xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType>命名空間</span><span class="sxs-lookup"><span data-stu-id="83b16-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="83b16-124">實作 MVVM</span><span class="sxs-lookup"><span data-stu-id="83b16-124">Implementing MVVM</span></span>
 <span data-ttu-id="83b16-125">若要實作 MVVM，通常會建立模型和檢視模型在可攜式類別庫專案中，因為非可攜式專案無法參考可攜式類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="83b16-125">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span></span> <span data-ttu-id="83b16-126">模型和檢視模型可以是相同專案中，或在不同的專案中。</span><span class="sxs-lookup"><span data-stu-id="83b16-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="83b16-127">如果您使用不同的專案，請從檢視模型專案中將參考新增到模型專案。</span><span class="sxs-lookup"><span data-stu-id="83b16-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="83b16-128">編譯模型後，當您檢視模型專案時，您會參考包含此檢視的應用程式中的這些組件。</span><span class="sxs-lookup"><span data-stu-id="83b16-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="83b16-129">如果檢視互動只具有檢視模型，您只需要參考該組件包含檢視模型。</span><span class="sxs-lookup"><span data-stu-id="83b16-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="83b16-130">型號</span><span class="sxs-lookup"><span data-stu-id="83b16-130">Model</span></span>
 <span data-ttu-id="83b16-131">下列範例顯示可能位於可攜式類別庫專案的簡化的模型類別。</span><span class="sxs-lookup"><span data-stu-id="83b16-131">The following example shows a simplified model class that could reside in a Portable Class Library project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="83b16-132">下列範例顯示簡單的方式來填入、 擷取及更新可攜式類別庫專案中的資料。</span><span class="sxs-lookup"><span data-stu-id="83b16-132">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span></span> <span data-ttu-id="83b16-133">在實際的應用程式中，您會從來源，例如 Windows Communication Foundation (WCF) 服務擷取資料。</span><span class="sxs-lookup"><span data-stu-id="83b16-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="83b16-134">檢視模型</span><span class="sxs-lookup"><span data-stu-id="83b16-134">View Model</span></span>
 <span data-ttu-id="83b16-135">實作 MVVM 模式時，經常會加入檢視模型的基底類別。</span><span class="sxs-lookup"><span data-stu-id="83b16-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="83b16-136">下列範例顯示基底類別。</span><span class="sxs-lookup"><span data-stu-id="83b16-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="83b16-137">實作<xref:System.Windows.Input.ICommand>介面經常搭配 MVVM 模式。</span><span class="sxs-lookup"><span data-stu-id="83b16-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="83b16-138">下列範例會示範 <xref:System.Windows.Input.ICommand> 介面的實作。</span><span class="sxs-lookup"><span data-stu-id="83b16-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="83b16-139">下列範例示範簡化的檢視模型。</span><span class="sxs-lookup"><span data-stu-id="83b16-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="83b16-140">檢視</span><span class="sxs-lookup"><span data-stu-id="83b16-140">View</span></span>  
 <span data-ttu-id="83b16-141">從.NET Framework 4.5 的應用程式，[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式、 Silverlight 架構應用程式或 Windows Phone 7.5 應用程式，您可以參考包含模型和檢視的模型專案的組件。</span><span class="sxs-lookup"><span data-stu-id="83b16-141">From a .NET Framework 4.5 app, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="83b16-142">然後，您會建立互動的檢視以檢視模型。</span><span class="sxs-lookup"><span data-stu-id="83b16-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="83b16-143">下列範例示範簡化的 Windows Presentation Foundation (WPF) 應用程式，以擷取並更新檢視模型中的資料。</span><span class="sxs-lookup"><span data-stu-id="83b16-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="83b16-144">您可以建立類似的檢視，silverlight 中的 Windows Phone 或[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="83b16-144">You could create similar views in Silverlight, Windows Phone, or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="83b16-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83b16-145">See also</span></span>

- [<span data-ttu-id="83b16-146">可攜式類別庫</span><span class="sxs-lookup"><span data-stu-id="83b16-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
