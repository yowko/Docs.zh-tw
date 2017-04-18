---
title: "Web 和通訊端權限 | Microsoft Docs"
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
  - "網路"
  - "位置 [.NET Framework]，接受"
  - "通訊端，權限"
  - "網路，權限"
  - "網際網路，權限"
  - "網路資源"
  - "SocketPermission 類別，關於 SocketPermission 類別"
  - "位置 [.NET Framework]，連接"
  - "WebPermission 類別，關於 WebPermission 類別"
  - "權限 [.NET Framework]，通訊端"
  - "安全性 [.NET Framework]，網際網路"
  - "位置 [.NET Framework]，授與"
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Web 和通訊端權限
使用 <xref:System.Net> 命名空間 <xref:System.Net.WebPermission> 和 <xref:System.Net.SocketPermission> 類別為應用程式的網際網路安全性。  **WebPermission** 類別控制應用程式的權限要求 URI 的資料或服務 URI 至網際網路。  **SocketPermission** 類別控制應用程式的使用權限 <xref:System.Net.Sockets.Socket> 接受了某個本機通訊埠資料或使用遠端裝置連接使用傳輸通訊協定在另一個位址，視通訊端主機、連接埠編號和傳輸通訊協定。  
  
 哪些使用權限類別使用取決於您的應用程式類型。  使用 <xref:System.Net.WebRequest> 和其子代 \(Descendant\) 的應用程式應該使用 **WebPermission** 類別處理使用權限。  使用通訊端 \(Socket\) 存取層級的應用程式應該使用 **SocketPermission** 類別處理使用權限。  
  
 **WebPermission** 和 **SocketPermission** 定義兩個使用權限:接受並連接到。  接受授權應用程式版權回應來自另一方的連入連線。  連接授與應用程式版權啟始與另一方的連接。  
  
 如需執行個體 **SocketPermission** ，接受表示應用程式可以接受在本機傳輸位址的連入連線，連接表示應用程式可以連接至特定遠端 \(或區域\) 傳送位址。  
  
 如需執行個體 **WebPermission** ，接受表示應用程式可以匯出控制項的 **WebPermission** URI 至世界;連接表示應用程式可以存取該 URI \(它是否為遠端或本機\)。  
  
## 請參閱  
 [Security](../../../docs/standard/security/index.md)   
 [網路程式設計的安全性](../../../docs/framework/network-programming/security-in-network-programming.md)