---
title: "如何：使用應用程式範圍的資源字典 | Microsoft Docs"
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
  - "應用程式範圍的資源字典"
  - "字典, 資源"
  - "資源字典, 應用程式範圍"
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用應用程式範圍的資源字典
這個範例顯示如何定義和使用應用程式範圍的自訂資源字典。  
  
## 範例  
 <xref:System.Windows.Application> 會針對共用資源公開應用程式範圍的存放區：<xref:System.Windows.Application.Resources%2A>。  根據預設，<xref:System.Windows.Application.Resources%2A> 屬性是以 <xref:System.Windows.ResourceDictionary> 型別的執行個體初始化。  當您使用 <xref:System.Windows.Application.Resources%2A> 取得及設定應用程式範圍的屬性時，會使用這個執行個體  \(如需詳細資訊，請參閱 [How to: Get and Set an Application\-Scope Resource](http://msdn.microsoft.com/zh-tw/39e0420c-c9fc-47dc-8956-fdd95b214095)\)。  
  
 如果要用 <xref:System.Windows.Application.Resources%2A> 設定的資源不止一個，您可以改為使用自訂資源字典來存放這些資源，然後將 <xref:System.Windows.Application.Resources%2A> 設為這個字典。  以下示範如何使用 XAML 宣告自訂資源字典。  
  
 [!code-xml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 使用 <xref:System.Windows.Application.Resources%2A> 交換整個資源字典，可以讓您支援應用程式範圍的佈景主題，因為所有佈景主題都封裝在單一資源字典中。  下列範例示範如何設定 <xref:System.Windows.ResourceDictionary>。  
  
 [!code-xml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 以下示範如何在 XAML 中從 <xref:System.Windows.Application.Resources%2A> 公開的資源字典取得應用程式範圍資源。  
  
 [!code-xml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 以下示範如何同樣在程式碼中取得資源。  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 使用 <xref:System.Windows.Application.Resources%2A> 時需要進行兩項考量。  首先，字典 *key* 是一個物件，因此您在設定和取得屬性值時，必須使用完全相同的物件執行個體  \(請注意，使用字串時，key 區分大小寫\)。 其次，字典 *value* 是一個物件，因此在取得屬性值時，必須將這個值轉換為所需的型別。  
  
## 請參閱  
 <xref:System.Windows.ResourceDictionary>   
 <xref:System.Windows.Application.Resources%2A>   
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [合併的資源字典](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)