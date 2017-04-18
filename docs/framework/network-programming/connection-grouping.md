---
title: "連接群組 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "網際網路，連接"
  - "連接 [.NET Framework]，群組"
  - "WebRequest 類別，連接群組"
  - "網路資源，連接"
  - "連接共用"
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# 連接群組
群組在單一應用程式中的連接將特定需求與已定義的連接集區。  您可以連接到後端伺服器代表使用者的中介層應用程式需求並支援使用委派，例如 Kerberos，或是由中介層應用程式提供自己的驗證，在以下範例中的驗證通訊協定。  例如，假設使用者， Joe，瀏覽顯示它們的薪資資訊的內部網路網站。  在驗證之後， Joe 中介層應用程式伺服器使用 Joe 的認證連接到後端伺服器擷取它們的薪資資訊。  接著，程式珊造訪網站並要求她的薪資資訊。  使用 Joe 的認證，因為中介層應用程式已經建立連線，後端伺服器回應與 Joe 的資訊。  不過，因此，如果應用程式將每一個要求傳送至後端伺服器會從使用者名稱建立連接的群組，然後針對每位使用者屬於不同的連接集區，而且無法與其他使用者共用不小心驗證資訊。  
  
 若要將需要針對特定連接群組，您必須將名稱指派給您的 <xref:System.Net.WebRequest><xref:System.Net.WebRequest.ConnectionGroupName%2A> 屬性在發出要求之前。  
  
## 請參閱  
 [管理連接](../../../docs/framework/network-programming/managing-connections.md)   
 [如何：將使用者資訊指派給群組連接](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)