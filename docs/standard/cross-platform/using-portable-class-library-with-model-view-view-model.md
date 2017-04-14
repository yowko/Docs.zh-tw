---
title: "搭配 Model-View-View 模型使用可攜式類別庫 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "可攜式類別庫 [.NET Framework]，與 MVVM"
  - "MVVM 與可攜式類別庫"
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# 搭配 Model-View-View 模型使用可攜式類別庫
您可以使用 .NET Framework 的 [可攜式類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) 實作多重平台間的檢視模型檢視模型 \(MVVM\) 模式和共用組件。  
  
 MVVM 是隔離自基礎商務邏輯之使用者介面的應用程式樣式。  您可以在[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]實作 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] 專案模型和檢視模型類別，然後建立針對不同平台的自訂檢視。  如下圖所示，這個方法使您只能寫入一次資料模型和商務邏輯，並使用 .NET Framework， Silverlight 和 Windows Phone、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式的程式碼。  
  
 ![可攜式類別庫搭配 MVVM 圖表](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")  
  
 本主題不提供有關 MVVM 模式的一般資訊。  它只提供有關如何使用 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] 實作 MVVM的資訊。  如需 MVVM 的詳細資訊，請參閱 MSDN 文件庫的[MVVM Quickstart](http://go.microsoft.com/fwlink/?LinkId=234934)。  
  
## 類別支援 MVVM  
 當您為了 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] 專案而針對 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 、Silverlight或Windows Phone 7.5 時，下列類別可用於實作這個 MVVM 樣式：  
  
-   <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=fullName> 類別  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=fullName> 類別  
  
-   <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=fullName> 類別  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=fullName> 類別  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=fullName> 類別  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=fullName> 類別  
  
-   <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=fullName> 類別  
  
-   <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=fullName> 類別  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=fullName> 類別  
  
-   <xref:System.Windows.Input.ICommand?displayProperty=fullName> 類別  
  
-   在 <xref:System.ComponentModel.DataAnnotations?displayProperty=fullName> 命名空間中的所有類別  
  
## 實作MVVM  
 因為 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] 專案無法參考不可移植的專案，所以若要實作 MVVM，您通常可以在 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] 專案中建立模型和檢視模型。  模型和檢視模型可以在同一個專案或在不同的專案中。  如果您使用不同的專案，請在檢視模型專案中加入這個模型專案的參考。  
  
 在編譯模型和檢視模型專案之後，您可以在包含這個檢視的應用程式中參考這些組件。  如果檢視只與檢視模型互動，您只需要參考檢視模型中的組件。  
  
### Model  
 下列範例顯示可以位於 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] 專案的簡化的模型類別。  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 下列範例以簡單的方式來填入，擷取，並更新 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] 專案中的資料。  在實際的應用程式，您會從一個來源擷取資料 \(例如 Windows Communication Foundation \(WCF\) 服務。  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### 模型檢視  
 在實作MVVM 模式時，檢視模型的基底類別通常會被加入。  下列範例顯示基底類別。  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 <xref:System.Windows.Input.ICommand> 介面的實作最常搭配 MVVM 模式。  下列範例會示範 <xref:System.Windows.Input.ICommand> 介面的實作。  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 下列範例顯示一個簡易檢視模型。  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### 檢視  
 從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 應用程式， [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式， Silverlight 架構應用程式，或是 Windows Phone 7.5 應用程式中，您可以參考包含模型和檢視模型專案中的組件。然後建立與檢視模型互動的檢視。  下列範例會示範從檢視模型更新資料的簡化的 Windows Presentation Foundation \(WPF\) 應用程式。  您可以在 Silverlight 和 Windows Phone、或 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式建立類似的檢視。  
  
 [!code-xml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## 請參閱  
 [可攜式類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)