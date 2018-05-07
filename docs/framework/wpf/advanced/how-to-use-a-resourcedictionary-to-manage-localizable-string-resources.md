---
title: 如何：使用 ResourceDictionary 管理可當地語系化的字串資源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
ms.openlocfilehash: 76ff3f688b5d3e7122254990076edb21fe6ae119
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>如何：使用 ResourceDictionary 管理可當地語系化的字串資源
這個範例示範如何使用<xref:System.Windows.ResourceDictionary>Windows Presentation Foundation (WPF) 應用程式的封裝可當地語系化字串資源。  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>若要使用 ResourceDictionary 管理可當地語系化的字串資源  
  
1.  建立<xref:System.Windows.ResourceDictionary>，其中包含您想要當地語系化的字串。 下列程式碼示範範例。  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     此程式碼定義之字串資源`localizedMessage`，型別<xref:System.String>，從<xref:System>mscorlib.dll 中的命名空間。  
  
2.  新增<xref:System.Windows.ResourceDictionary>您的應用程式中，使用下列程式碼。  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  使用字串資源標記中，從使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]像下面這樣。  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  使用類似下列程式碼，即可利用來自程式碼後置的字串資源。  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  將應用程式當地語系化。 如需詳細資訊，請參閱[當地語系化應用程式](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)。
