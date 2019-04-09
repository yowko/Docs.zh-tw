---
title: HOW TO：使用應用程式資源
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: 70dff8089c4da70fdc61247a0c604cf7ee85d02b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088194"
---
# <a name="how-to-use-application-resources"></a>HOW TO：使用應用程式資源
這個範例示範如何使用應用程式資源。  
  
## <a name="example"></a>範例  
 下列範例顯示應用程式定義檔案。 應用程式定義檔定義的資源區段 (值<xref:System.Windows.Application.Resources%2A>屬性)。 如果資源是定義為應用程式層級，則應用程式當中的其他所有頁面均可存取這些資源。 在此情況下，這類資源是宣告的樣式。 包含控制項範本的完整樣式可能會很冗長，因為這個範例省略了 [控制項] 範本中定義<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>樣式的屬性 setter。  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 下列範例所示[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面，會參考前一個範例定義的應用程式層級資源。 參考資源，您使用[StaticResource 標記延伸](staticresource-markup-extension.md)，指定所要求資源的唯一資源金鑰。 目前的頁面找不到任何含有 "GelButton" 索引鍵的資源，因此，所要求資源的資源查閱範圍會繼續延伸到目前頁面以外和已定義的應用程式層級資源當中。  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>另請參閱

- [XAML 資源](xaml-resources.md)
- [應用程式管理概觀](../app-development/application-management-overview.md)
- [HOW TO 主題](resources-how-to-topics.md)
