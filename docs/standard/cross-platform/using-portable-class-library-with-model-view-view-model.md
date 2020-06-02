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
ms.openlocfilehash: ff34b295ba443088115d470d8ade0c986ac1d856
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288845"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a>搭配 Model-View-View 模型使用可攜式類別庫
您可以使用 .NET Framework 的[可移植類別庫](cross-platform-development-with-the-portable-class-library.md)來執行模型視圖視圖模型（MVVM）模式，並跨多個平臺共用元件。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM 是將使用者介面與基礎商務邏輯隔離的應用程式模式。 您可以在 Visual Studio 2012 的可移植類別庫專案中，執行模型和視圖模型類別，然後建立針對不同平臺自訂的視圖。 這種方法可讓您只撰寫資料模型和商務邏輯一次，並使用 .NET Framework、Silverlight、Windows Phone 和 Windows 8.x Store 應用程式中的程式碼，如下圖所示。

 ![顯示在各平臺上具有 MVVM 共用元件的可移植類別庫。](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 本主題不提供 MVVM 模式的一般資訊。 它只提供如何使用可移植類別庫來執行 MVVM 的相關資訊。 如需 MVVM 的詳細資訊，請參閱[使用適用于 WPF 的 Prism 程式庫5.0 的 MVVM 快速入門](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40))。

## <a name="classes-that-support-mvvm"></a>支援 MVVM 的類別
 當您以 .NET Framework 4.5、適用于 Windows 8.x 的 .NET 儲存應用程式、Silverlight 或 Windows Phone 7.5 作為可移植類別庫專案的目標時，可以使用下列類別來執行 MVVM 模式：

- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> 類別

- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> 類別

- <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> 類別

- <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> 類別

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> 類別

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> 類別

- <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> 類別

- <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> 類別

- <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> 類別

- <xref:System.Windows.Input.ICommand?displayProperty=nameWithType> 類別

- 命名空間中的所有類別 <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType>

## <a name="implementing-mvvm"></a>執行 MVVM
 若要執行 MVVM，您通常會在可移植的類別庫專案中建立模型和視圖模型，因為可移植的類別庫專案無法參考不可移植的專案。 模型和視圖模型可以位於相同的專案或個別專案中。 如果您使用不同的專案，請從視圖模型專案中，將參考加入至模型專案。

 在您編譯模型和視圖模型專案之後，您會參考應用程式中包含此視圖的元件。 如果此視圖只與視圖模型互動，您只需要參考包含視圖模型的元件。

### <a name="model"></a>型號
 下列範例顯示可能位於可移植類別庫專案中的簡化模型類別。

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 下列範例顯示簡單的方式來填入、抓取和更新可移植類別庫專案中的資料。 在實際的應用程式中，您會從 Windows Communication Foundation （WCF）服務之類的來源抓取資料。

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a>視圖模型
 在執行 MVVM 模式時，經常會加入視圖模型的基類。 下列範例顯示基類。

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 介面的執行 <xref:System.Windows.Input.ICommand> 通常與 MVVM 模式搭配使用。 下列範例會示範 <xref:System.Windows.Input.ICommand> 介面的實作。

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 下列範例會顯示簡化的視圖模型。

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>檢視  
 從 .NET Framework 4.5 應用程式、Windows 8.x 存放區應用程式、Silverlight 應用程式或 Windows Phone 7.5 應用程式，您可以參考包含模型和視圖模型專案的元件。  接著，您可以建立與視圖模型互動的視圖。 下列範例顯示簡化的 Windows Presentation Foundation （WPF）應用程式，可從視圖模型抓取和更新資料。 您可以在 Silverlight、Windows Phone 或 Windows 8.x 存放區應用程式中建立類似的視圖。  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>另請參閱

- [可攜式類別庫](cross-platform-development-with-the-portable-class-library.md)
