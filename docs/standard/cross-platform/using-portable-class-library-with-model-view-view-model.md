---
title: "搭配 Model-View-View 模型使用可攜式類別庫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e39a8df5c8aee05414e778f15a29bbeda8dba930
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-portable-class-library-with-model-view-view-model"></a>搭配 Model-View-View 模型使用可攜式類別庫
您可以使用.NET Framework[可攜式類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)實作模型檢視 View Model (MVVM) 模式，並且跨多平台共用組件。  
  
 MVVM 是將使用者介面與基礎商務邏輯隔離的應用程式模式。 您可以在 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] 的[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]專案中實作模型和檢視模型類別，然後建立針對不同平台自訂的檢視。 這個方法讓您只需撰寫資料模型和商務邏輯一次，就可以從 .NET Framework、Silverlight、Windows Phone 和 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式使用該程式碼，如下圖所示。  
  
 ![搭配 MVVM 圖表可攜式](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")  
  
 本主題不提供 MVVM 模式的一般資訊。 它只會提供有關如何使用資訊[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]實作 MVVM。 如需 MVVM 的詳細資訊，請參閱[MVVM 快速入門](http://go.microsoft.com/fwlink/?LinkId=234934)。  
  
## <a name="classes-that-support-mvvm"></a>類別，可支援 MVVM  
 如果您的[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]專案是以 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]、[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]、Silverlight 或 Windows Phone 7.5 為目標，就可以使用下列類別實作 MVVM 模式：  
  
-   <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> 類別  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> 類別  
  
-   <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> 類別  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> 類別  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> 類別  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> 類別  
  
-   <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> 類別  
  
-   <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> 類別  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> 類別  
  
-   <xref:System.Windows.Input.ICommand?displayProperty=nameWithType> 類別  
  
-   中的所有類別<xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType>命名空間  
  
## <a name="implementing-mvvm"></a>實作 MVVM  
 若要實作 MVVM，您通常會建立模型和檢視模型中的[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]專案，因為[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]專案無法參考非可攜式專案。 模型和檢視模型可以是相同專案中，或在不同的專案中。 如果您使用不同的專案，請從檢視模型專案新增參考模型專案。  
  
 編譯模型後，當您檢視模型專案時，會參考包含此檢視的應用程式中的這些組件。 檢視只會與檢視模型互動時，如果您只需要參考組件包含檢視模型。  
  
### <a name="model"></a>模型  
 下列範例示範的簡化的模型類別，可能位於[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]專案。  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 下列範例顯示簡單的方式填入、 擷取及更新中的資料[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]專案。 在實際的應用程式，將會從來源，例如 Windows Communication Foundation (WCF) 服務擷取資料。  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### <a name="view-model"></a>檢視模型  
 實作 MVVM 模式時，經常會加入檢視模型的基底類別。 下列範例顯示基底類別。  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 實作<xref:System.Windows.Input.ICommand>介面經常搭配 MVVM 模式。 下列範例會示範 <xref:System.Windows.Input.ICommand> 介面的實作。  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 下列範例示範簡化的檢視模型。  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>檢視  
 從[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]應用程式，[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式、 Silverlight 架構應用程式或 Windows Phone 7.5 的應用程式，您可以參考包含模型和檢視的模型專案的組件。  然後，您會建立互動的檢視以檢視模型。 下列範例示範簡化的 Windows Presentation Foundation (WPF) 應用程式，以擷取並更新檢視模型中的資料。 您可以在 Windows Phone Silverlight 建立類似的檢視或[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式。  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>另請參閱  
 [可攜式類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
