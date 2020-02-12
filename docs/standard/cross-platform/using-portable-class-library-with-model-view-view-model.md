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
ms.openlocfilehash: f5312177b9f437d9b5474d38fca80db6fc45245b
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123671"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="41aba-102">搭配 Model-View-View 模型使用可攜式類別庫</span><span class="sxs-lookup"><span data-stu-id="41aba-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="41aba-103">您可以使用 .NET Framework 的[可移植類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)來執行模型視圖視圖模型（MVVM）模式，並跨多個平臺共用元件。</span><span class="sxs-lookup"><span data-stu-id="41aba-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="41aba-104">MVVM 是將使用者介面與基礎商務邏輯隔離的應用程式模式。</span><span class="sxs-lookup"><span data-stu-id="41aba-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="41aba-105">您可以在 Visual Studio 2012 的可移植類別庫專案中，執行模型和視圖模型類別，然後建立針對不同平臺自訂的視圖。</span><span class="sxs-lookup"><span data-stu-id="41aba-105">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="41aba-106">這種方法可讓您只撰寫資料模型和商務邏輯一次，並使用 .NET Framework、Silverlight、Windows Phone 和 Windows 8.x Store 應用程式中的程式碼，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="41aba-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and Windows 8.x Store apps, as shown in the following illustration.</span></span>

 ![顯示在各平臺上具有 MVVM 共用元件的可移植類別庫。](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="41aba-108">本主題不提供 MVVM 模式的一般資訊。</span><span class="sxs-lookup"><span data-stu-id="41aba-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="41aba-109">它只提供如何使用可移植類別庫來執行 MVVM 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="41aba-109">It only provides information about how to use Portable Class Library to implement MVVM.</span></span> <span data-ttu-id="41aba-110">如需 MVVM 的詳細資訊，請參閱[使用適用于 WPF 的 Prism 程式庫5.0 的 MVVM 快速入門](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40))。</span><span class="sxs-lookup"><span data-stu-id="41aba-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="41aba-111">支援 MVVM 的類別</span><span class="sxs-lookup"><span data-stu-id="41aba-111">Classes That Support MVVM</span></span>
 <span data-ttu-id="41aba-112">當您以 .NET Framework 4.5、適用于 Windows 8.x 的 .NET 儲存應用程式、Silverlight 或 Windows Phone 7.5 作為可移植類別庫專案的目標時，可以使用下列類別來執行 MVVM 模式：</span><span class="sxs-lookup"><span data-stu-id="41aba-112">When you target the .NET Framework 4.5, .NET for Windows 8.x Store apps, Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="41aba-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="41aba-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="41aba-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="41aba-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="41aba-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="41aba-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="41aba-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="41aba-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="41aba-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="41aba-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="41aba-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="41aba-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="41aba-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="41aba-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="41aba-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="41aba-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="41aba-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="41aba-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="41aba-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="41aba-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="41aba-123"><xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> 命名空間中的所有類別</span><span class="sxs-lookup"><span data-stu-id="41aba-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="41aba-124">執行 MVVM</span><span class="sxs-lookup"><span data-stu-id="41aba-124">Implementing MVVM</span></span>
 <span data-ttu-id="41aba-125">若要執行 MVVM，您通常會在可移植的類別庫專案中建立模型和視圖模型，因為可移植的類別庫專案無法參考不可移植的專案。</span><span class="sxs-lookup"><span data-stu-id="41aba-125">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span></span> <span data-ttu-id="41aba-126">模型和視圖模型可以位於相同的專案或個別專案中。</span><span class="sxs-lookup"><span data-stu-id="41aba-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="41aba-127">如果您使用不同的專案，請從視圖模型專案中，將參考加入至模型專案。</span><span class="sxs-lookup"><span data-stu-id="41aba-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="41aba-128">在您編譯模型和視圖模型專案之後，您會參考應用程式中包含此視圖的元件。</span><span class="sxs-lookup"><span data-stu-id="41aba-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="41aba-129">如果此視圖只與視圖模型互動，您只需要參考包含視圖模型的元件。</span><span class="sxs-lookup"><span data-stu-id="41aba-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="41aba-130">模型</span><span class="sxs-lookup"><span data-stu-id="41aba-130">Model</span></span>
 <span data-ttu-id="41aba-131">下列範例顯示可能位於可移植類別庫專案中的簡化模型類別。</span><span class="sxs-lookup"><span data-stu-id="41aba-131">The following example shows a simplified model class that could reside in a Portable Class Library project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="41aba-132">下列範例顯示簡單的方式來填入、抓取和更新可移植類別庫專案中的資料。</span><span class="sxs-lookup"><span data-stu-id="41aba-132">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span></span> <span data-ttu-id="41aba-133">在實際的應用程式中，您會從 Windows Communication Foundation （WCF）服務之類的來源抓取資料。</span><span class="sxs-lookup"><span data-stu-id="41aba-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="41aba-134">視圖模型</span><span class="sxs-lookup"><span data-stu-id="41aba-134">View Model</span></span>
 <span data-ttu-id="41aba-135">在執行 MVVM 模式時，經常會加入視圖模型的基類。</span><span class="sxs-lookup"><span data-stu-id="41aba-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="41aba-136">下列範例顯示基類。</span><span class="sxs-lookup"><span data-stu-id="41aba-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="41aba-137"><xref:System.Windows.Input.ICommand> 介面的執行通常與 MVVM 模式搭配使用。</span><span class="sxs-lookup"><span data-stu-id="41aba-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="41aba-138">下列範例會示範 <xref:System.Windows.Input.ICommand> 介面的實作。</span><span class="sxs-lookup"><span data-stu-id="41aba-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="41aba-139">下列範例會顯示簡化的視圖模型。</span><span class="sxs-lookup"><span data-stu-id="41aba-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="41aba-140">檢視</span><span class="sxs-lookup"><span data-stu-id="41aba-140">View</span></span>  
 <span data-ttu-id="41aba-141">從 .NET Framework 4.5 應用程式、Windows 8.x 存放區應用程式、Silverlight 應用程式或 Windows Phone 7.5 應用程式，您可以參考包含模型和視圖模型專案的元件。</span><span class="sxs-lookup"><span data-stu-id="41aba-141">From a .NET Framework 4.5 app, Windows 8.x Store app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="41aba-142">接著，您可以建立與視圖模型互動的視圖。</span><span class="sxs-lookup"><span data-stu-id="41aba-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="41aba-143">下列範例顯示簡化的 Windows Presentation Foundation （WPF）應用程式，可從視圖模型抓取和更新資料。</span><span class="sxs-lookup"><span data-stu-id="41aba-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="41aba-144">您可以在 Silverlight、Windows Phone 或 Windows 8.x 存放區應用程式中建立類似的視圖。</span><span class="sxs-lookup"><span data-stu-id="41aba-144">You could create similar views in Silverlight, Windows Phone, or Windows 8.x Store apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="41aba-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41aba-145">See also</span></span>

- [<span data-ttu-id="41aba-146">可攜式類別庫</span><span class="sxs-lookup"><span data-stu-id="41aba-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
