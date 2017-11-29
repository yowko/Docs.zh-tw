---
title: "如何：使用 XAML 排序和分組資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c219def87e258a2c9fc1bf4f4867287e6156c59a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>如何：使用 XAML 排序和分組資料
這個範例示範如何建立資料集合中的檢視[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。 檢視可讓分組、 排序、 篩選的功能和目前項目的概念。  
  
## <a name="example"></a>範例  
 在下列範例中，靜態資源名為*放置*做為集合定義*位置*中每個物件，*位置*物件組成的縣 （市） 名稱和狀態。 前置詞*src*對應至命名空間所在的資料來源*數位*定義。 前置詞*scm*對應至`"clr-namespace:System.ComponentModel;assembly=WindowsBase"`和*dat*對應至`"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`。  
  
 下列範例會建立一個檢視是依城市名稱排序，並依狀態分組的資料集合。  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 檢視可繫結來源，如下列範例所示：  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 對於 XML 資料中定義的繫結<xref:System.Windows.Data.XmlDataProvider>資源 XML 名前加上 @ 符號。  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Data.CollectionViewSource>  
 [取得資料集合的預設檢視](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [操作說明主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
