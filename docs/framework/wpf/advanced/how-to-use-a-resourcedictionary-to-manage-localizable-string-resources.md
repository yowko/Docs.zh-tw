---
title: "如何：使用 ResourceDictionary 管理可當地語系化的字串資源 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "當地語系化 [WPF], 封裝字串資源"
  - "封裝字串資源"
  - "ResourceDictionary [WPF]"
  - "資源 [WPF], 封裝字串資源"
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：使用 ResourceDictionary 管理可當地語系化的字串資源
本範例示範如何使用 <xref:System.Windows.ResourceDictionary>，來封裝 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 應用程式的可當地語系化字串資源。  
  
### 若要使用 ResourceDictionary 管理可當地語系化的字串資源  
  
1.  建立 <xref:System.Windows.ResourceDictionary>，其中包含您要當地語系化的字串。  下列程式碼示範一個範例。  
  
     [!code-xml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     這段程式碼會從 mscorlib.dll 中的 <xref:System> 命名空間定義型別為 <xref:System.String> 的字串資源 `localizedMessage`。  
  
2.  使用下列程式碼，將 <xref:System.Windows.ResourceDictionary> 加入到應用程式。  
  
     [!code-xml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  使用下列 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，從標記使用字串資源。  
  
     [!code-xml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  使用下列程式碼，從程式碼後置 \(Code\-Behind\) 使用字串資源。  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  將應用程式當地語系化。  如需詳細資訊，請參閱 [將應用程式當地語系化](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)。