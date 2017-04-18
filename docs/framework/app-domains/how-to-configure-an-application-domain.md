---
title: "如何：設定應用程式定義域 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式定義域, 設定"
  - "ApplicationBase 屬性"
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：設定應用程式定義域
您可以使用 <xref:System.AppDomainSetup> 類別提供 Common Language Runtime 新的應用程式定義域組態資訊。  建立自己的應用程式定義域時，最重要的屬性就是 <xref:System.AppDomainSetup.ApplicationBase%2A>。  其他 **AppDomainSetup** 屬性主要是由執行階段主應用程式用來組態特定的應用程式定義域。  
  
 **ApplicationBase** 屬性定義應用程式的根目錄。  當執行階段必須滿足型別要求時，它必須在 **ApplicationBase** 屬性指定的目錄中檢查含有該型別的組件。  
  
> [!NOTE]
>  新的應用程式定義域只會繼承建立者的 **ApplicationBase** 屬性。  
  
 下列範例建立 **AppDomainSetup** 類別的執行個體 \(Instance\)、使用該類別建立新的應用程式定義域、撰寫資訊到主控台，然後卸載應用程式定義域。  
  
## 範例  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## 請參閱  
 [Hosting Overview](http://msdn.microsoft.com/zh-tw/ea527626-99e3-4995-81c4-c8f3e60eb6d5)   
 [Programming with Application Domains](http://msdn.microsoft.com/zh-tw/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [使用應用程式定義域](../../../docs/framework/app-domains/use.md)