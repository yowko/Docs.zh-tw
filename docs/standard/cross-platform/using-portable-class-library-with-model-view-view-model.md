---
title: 搭配 Model-View-View 模型使用可攜式類別庫
ms.date: 03/30/2017
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
ms.openlocfilehash: aa8423c5c9453a9edb1058f0d5bdf4c494ece088
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574104"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="de223-102">搭配 Model-View-View 模型使用可攜式類別庫</span><span class="sxs-lookup"><span data-stu-id="de223-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="de223-103">您可以使用.NET Framework[可攜式類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)實作模型檢視 View Model (MVVM) 模式，並且跨多平台共用組件。</span><span class="sxs-lookup"><span data-stu-id="de223-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>  
  
 <span data-ttu-id="de223-104">MVVM 是將使用者介面與基礎商務邏輯隔離的應用程式模式。</span><span class="sxs-lookup"><span data-stu-id="de223-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="de223-105">您可以在 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] 的[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]專案中實作模型和檢視模型類別，然後建立針對不同平台自訂的檢視。</span><span class="sxs-lookup"><span data-stu-id="de223-105">You can implement the model and view model classes in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], and then create views that are customized for different platforms.</span></span> <span data-ttu-id="de223-106">這個方法讓您只需撰寫資料模型和商務邏輯一次，就可以從 .NET Framework、Silverlight、Windows Phone 和 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式使用該程式碼，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="de223-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="de223-107">![搭配 MVVM 圖表可攜式](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span><span class="sxs-lookup"><span data-stu-id="de223-107">![Portable with MVVM diagram](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span></span>  
  
 <span data-ttu-id="de223-108">本主題不提供 MVVM 模式的一般資訊。</span><span class="sxs-lookup"><span data-stu-id="de223-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="de223-109">它只會提供有關如何使用資訊[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]實作 MVVM。</span><span class="sxs-lookup"><span data-stu-id="de223-109">It only provides information about how to use [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] to implement MVVM.</span></span> <span data-ttu-id="de223-110">如需 MVVM 的詳細資訊，請參閱[MVVM 快速入門](https://msdn.microsoft.com/library/gg430869(v=PandP.40).aspx)。</span><span class="sxs-lookup"><span data-stu-id="de223-110">For more information about MVVM, see the [MVVM Quickstart](https://msdn.microsoft.com/library/gg430869(v=PandP.40).aspx).</span></span>  
  
## <a name="classes-that-support-mvvm"></a><span data-ttu-id="de223-111">類別，可支援 MVVM</span><span class="sxs-lookup"><span data-stu-id="de223-111">Classes That Support MVVM</span></span>  
 <span data-ttu-id="de223-112">如果您的[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]專案是以 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]、[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]、Silverlight 或 Windows Phone 7.5 為目標，就可以使用下列類別實作 MVVM 模式：</span><span class="sxs-lookup"><span data-stu-id="de223-112">When you target the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, the following classes are available for implementing the MVVM pattern:</span></span>  
  
-   <span data-ttu-id="de223-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="de223-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="de223-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="de223-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="de223-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="de223-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="de223-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="de223-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="de223-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="de223-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="de223-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="de223-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="de223-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="de223-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="de223-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="de223-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="de223-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="de223-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="de223-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="de223-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="de223-123">中的所有類別<xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType>命名空間</span><span class="sxs-lookup"><span data-stu-id="de223-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>  
  
## <a name="implementing-mvvm"></a><span data-ttu-id="de223-124">實作 MVVM</span><span class="sxs-lookup"><span data-stu-id="de223-124">Implementing MVVM</span></span>  
 <span data-ttu-id="de223-125">若要實作 MVVM，您通常會建立模型和檢視模型中的[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]專案，因為[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]專案無法參考非可攜式專案。</span><span class="sxs-lookup"><span data-stu-id="de223-125">To implement MVVM, you typically create both the model and the view model in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, because a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project cannot reference a non-portable project.</span></span> <span data-ttu-id="de223-126">模型和檢視模型可以是相同專案中，或在不同的專案中。</span><span class="sxs-lookup"><span data-stu-id="de223-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="de223-127">如果您使用不同的專案，請從檢視模型專案新增參考模型專案。</span><span class="sxs-lookup"><span data-stu-id="de223-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>  
  
 <span data-ttu-id="de223-128">編譯模型後，當您檢視模型專案時，會參考包含此檢視的應用程式中的這些組件。</span><span class="sxs-lookup"><span data-stu-id="de223-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="de223-129">檢視只會與檢視模型互動時，如果您只需要參考組件包含檢視模型。</span><span class="sxs-lookup"><span data-stu-id="de223-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>  
  
### <a name="model"></a><span data-ttu-id="de223-130">型號</span><span class="sxs-lookup"><span data-stu-id="de223-130">Model</span></span>  
 <span data-ttu-id="de223-131">下列範例示範的簡化的模型類別，可能位於[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="de223-131">The following example shows a simplified model class that could reside in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 <span data-ttu-id="de223-132">下列範例顯示簡單的方式填入、 擷取及更新中的資料[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="de223-132">The following example shows a simple way to populate, retrieve, and update the data in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span> <span data-ttu-id="de223-133">在實際的應用程式，將會從來源，例如 Windows Communication Foundation (WCF) 服務擷取資料。</span><span class="sxs-lookup"><span data-stu-id="de223-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### <a name="view-model"></a><span data-ttu-id="de223-134">檢視模型</span><span class="sxs-lookup"><span data-stu-id="de223-134">View Model</span></span>  
 <span data-ttu-id="de223-135">實作 MVVM 模式時，經常會加入檢視模型的基底類別。</span><span class="sxs-lookup"><span data-stu-id="de223-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="de223-136">下列範例顯示基底類別。</span><span class="sxs-lookup"><span data-stu-id="de223-136">The following example shows a base class.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 <span data-ttu-id="de223-137">實作<xref:System.Windows.Input.ICommand>介面經常搭配 MVVM 模式。</span><span class="sxs-lookup"><span data-stu-id="de223-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="de223-138">下列範例會示範 <xref:System.Windows.Input.ICommand> 介面的實作。</span><span class="sxs-lookup"><span data-stu-id="de223-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 <span data-ttu-id="de223-139">下列範例示範簡化的檢視模型。</span><span class="sxs-lookup"><span data-stu-id="de223-139">The following example shows a simplified view model.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="de223-140">檢視</span><span class="sxs-lookup"><span data-stu-id="de223-140">View</span></span>  
 <span data-ttu-id="de223-141">從[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]應用程式，[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式、 Silverlight 架構應用程式或 Windows Phone 7.5 的應用程式，您可以參考包含模型和檢視的模型專案的組件。</span><span class="sxs-lookup"><span data-stu-id="de223-141">From a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] app, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="de223-142">然後，您會建立互動的檢視以檢視模型。</span><span class="sxs-lookup"><span data-stu-id="de223-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="de223-143">下列範例示範簡化的 Windows Presentation Foundation (WPF) 應用程式，以擷取並更新檢視模型中的資料。</span><span class="sxs-lookup"><span data-stu-id="de223-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="de223-144">您可以在 Windows Phone Silverlight 建立類似的檢視或[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="de223-144">You could create similar views in Silverlight, Windows Phone, or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="de223-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de223-145">See Also</span></span>  
 [<span data-ttu-id="de223-146">可攜式類別庫</span><span class="sxs-lookup"><span data-stu-id="de223-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
