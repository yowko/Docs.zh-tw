---
title: 如何：使用應用程式資源
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: e4114466fa8016f8e31100d7a37038b0abfdccca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460264"
---
# <a name="how-to-use-application-resources"></a>如何：使用應用程式資源
這個範例示範如何使用應用程式資源。  
  
## <a name="example"></a>範例  
 下列範例顯示應用程式定義檔案。 應用程式定義檔會定義資源區段（<xref:System.Windows.Application.Resources%2A> 屬性的值）。 如果資源是定義為應用程式層級，則應用程式當中的其他所有頁面均可存取這些資源。 在此情況下，這類資源是宣告的樣式。 因為包含控制項範本的完整樣式可能會很冗長，所以這個範例會省略在樣式的 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 屬性 setter 中定義的控制項範本。  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 下列範例顯示的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面會參考上一個範例所定義的應用層級資源。 藉由使用[StaticResource 標記延伸](staticresource-markup-extension.md)來參考資源，以指定所要求資源的唯一資源金鑰。 目前的頁面找不到任何含有 "GelButton" 索引鍵的資源，因此，所要求資源的資源查閱範圍會繼續延伸到目前頁面以外和已定義的應用程式層級資源當中。  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>請參閱

- [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [應用程式管理概觀](../app-development/application-management-overview.md)
- [「如何」主題](resources-how-to-topics.md)
