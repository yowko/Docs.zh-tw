---
title: 如何：使用應用程式資源
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: 4305c49c4322d164e2481c1508dda7c038c14694
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-application-resources"></a>如何：使用應用程式資源
這個範例示範如何使用應用程式資源。  
  
## <a name="example"></a>範例  
 下列範例顯示應用程式定義檔案。 應用程式定義檔定義的資源區段 (值<xref:System.Windows.Application.Resources%2A>屬性)。 如果資源是定義為應用程式層級，則應用程式當中的其他所有頁面均可存取這些資源。 在此情況下，這類資源是宣告的樣式。 包含控制項範本的完整樣式可能會很長，因為這個範例省略了 [控制項] 範本中定義<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>屬性 setter 的樣式。  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 下列範例所示[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]參考應用程式層級定義的資源。 上一個範例網頁。 資源使用參考[StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)指定要求之資源的唯一的資源索引鍵。 目前的頁面找不到任何含有 "GelButton" 索引鍵的資源，因此，所要求資源的資源查閱範圍會繼續延伸到目前頁面以外和已定義的應用程式層級資源當中。  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>另請參閱  
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [應用程式管理概觀](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
