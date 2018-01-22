---
title: "如何：使用應用程式範圍的資源字典"
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
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04dbcfb0fa16ceb4d6778ef611e926894d7840e9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>如何：使用應用程式範圍的資源字典
此範例示範如何定義和使用應用程式範圍自訂資源字典。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Application>公開共用資源的應用程式範圍存放區： <xref:System.Windows.Application.Resources%2A>。 根據預設，<xref:System.Windows.Application.Resources%2A>屬性會初始化的執行個體<xref:System.Windows.ResourceDictionary>型別。 當您取得和設定應用程式領域屬性使用時，會使用此執行個體<xref:System.Windows.Application.Resources%2A>。 如需詳細資訊，請參閱[How to： 取得和設定應用程式範圍資源](http://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095)。
  
 如果您有多個您設定使用的資源<xref:System.Windows.Application.Resources%2A>，您可以改用自訂資源字典來儲存這些資源和設定<xref:System.Windows.Application.Resources%2A>與其改為。 下圖顯示您將自訂的資源字典使用 XAML 的宣告。
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 交換使用的整個資源字典<xref:System.Windows.Application.Resources%2A>可讓您支援應用程式範圍的佈景主題，其中每個主題會封裝單一資源字典。 下列範例會示範如何設定 <xref:System.Windows.ResourceDictionary>。  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 下列範例示範如何取得應用程式範圍的資源，從所公開的資源字典<xref:System.Windows.Application.Resources%2A>在 XAML 中。  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 下列會顯示也可以如何使用程式碼來取得資源。  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 有兩個使用時的考量<xref:System.Windows.Application.Resources%2A>。 首先，字典*金鑰*不是物件，因此您必須使用完全相同物件執行個體時設定和取得屬性值。 (請注意，使用字串時，索引鍵會區分大小寫)。其次，字典*值*是物件，所以您必須取得的屬性值時，就將值轉換成所需的類型。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.ResourceDictionary>  
 <xref:System.Windows.Application.Resources%2A>  
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [合併的資源字典](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
