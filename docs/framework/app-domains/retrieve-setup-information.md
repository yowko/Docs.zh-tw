---
title: "從應用程式定義域擷取安裝資訊 | Microsoft Docs"
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
  - "AppDomainSetup 物件"
  - "應用程式定義域, 擷取安裝資訊"
  - "擷取安裝資訊"
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 從應用程式定義域擷取安裝資訊
應用程式定義域的每個執行個體都是由屬性和 <xref:System.AppDomainSetup> 資訊所組成。  您可以使用 <xref:System.AppDomain?displayProperty=fullName> 類別從應用程式定義域擷取安裝資訊。  這個類別提供數個成員，可擷取應用程式定義域相關組態資訊。  
  
 您也可以查詢應用程式定義域的 **AppDomainSetup** 物件，來取得建立應用程式定義域時傳遞到應用程式定義域的安裝資訊。  
  
 下列範例建立新的應用程式定義域，然後列印數個值到主控台。  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 下列範例設定並擷取應用程式定義域的安裝資訊。  請注意，`AppDomain.SetupInformation.ApplicationBase` 會取得組態資訊。  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## 請參閱  
 [Hosting Overview](http://msdn.microsoft.com/zh-tw/ea527626-99e3-4995-81c4-c8f3e60eb6d5)   
 [Programming with Application Domains](http://msdn.microsoft.com/zh-tw/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [使用應用程式定義域](../../../docs/framework/app-domains/use.md)