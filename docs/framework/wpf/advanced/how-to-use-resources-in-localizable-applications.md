---
title: "如何：在可當地語系化的應用程式中使用資源 | Microsoft Docs"
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
  - "應用程式, 可當地語系化"
  - "可當地語系化的應用程式"
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：在可當地語系化的應用程式中使用資源
當地語系化的意義是要讓 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 適應不同的文化特性。  若要完成這項工作，必須翻譯標題 \(Title\)、標題 \(Caption\)、清單方塊項目等文字。  為了簡化翻譯過程，會將要翻譯的項目收集到資源檔中。  如需如何建立當地語系化之資源檔的詳細資訊，請參閱[將應用程式當地語系化](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)。  若要讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式變成可供當地語系化，開發人員必須將所有可當地語系化的資源建置至一個資源組件中。  這個資源組件會被譯為不同的語言，而程式碼後置 \(Code\-Behind\) 會使用資源管理 [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] 進行載入。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式需要的其中一個檔案是專案檔 \(.proj\)。  所有您在應用程式中使用的資源都應該要包含在專案檔中。  下列程式碼範例會顯示這點。  
  
## 範例  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 若要在應用程式中使用資源，請執行個體化 <xref:System.Resources.ResourceManager>，然後載入想要使用的資源。  以下示範如何進行這項操作。  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]