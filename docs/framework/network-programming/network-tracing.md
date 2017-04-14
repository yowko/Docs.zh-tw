---
title: "以 .NET Framework 進行網路追蹤 | Microsoft Docs"
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
  - "擷取網路流量"
  - "偵錯 [.NET Framework], 網路追蹤"
  - "部署應用程式 [.NET Framework], 網路流量"
  - "網際網路, 網路追蹤"
  - "方法引動過程"
  - "方法, 網路追蹤"
  - "網路資源"
  - "網路追蹤"
  - "網路追蹤, 關於網路追蹤"
  - "網路, 網路追蹤"
  - "網路"
  - "輸出, 網路追蹤"
  - "追蹤啟用的偵錯功能"
  - "追蹤 [.NET Framework], 網路"
  - "流量追蹤"
ms.assetid: e993b7c3-087f-45d8-9c02-9dded936d804
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 以 .NET Framework 進行網路追蹤
針對方法叫用及 Managed 應用程式所產生的網路流量，.NET Framework 中的網路追蹤能提供對這些相關資訊的存取。  若要為開發中的應用程式進行偵錯，以及分析已部署的應用程式，此功能會非常有用。  您可以自訂網路追蹤所提供的輸出，在程式開發時期和實際執行環境中支援不同的使用案例。  
  
 若要啟用 .NET Framework 中的網路追蹤，您必須為追蹤輸出選取一個目的地，並在應用程式或電腦組態檔中加入網路追蹤組態設定。  如需組態檔以及如何使用它們的說明，請參閱[組態檔](../../../docs/framework/configure-apps/index.md)。  如需如何啟用網路追蹤的詳細資訊，請參閱[啟用網路追蹤](../../../docs/framework/network-programming/enabling-network-tracing.md)。  如需必須加入至組態檔中之設定的詳細資訊，請參閱[如何：設定網路追蹤](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)。  
  
 啟用追蹤之後，您就可以擷取 **System.Net** 類別所輸出的追蹤資訊。  可產生追蹤資訊的網路類別成員在它們的 .NET Framework 類別庫文件的＜備註＞一節中會包含下面附註：  
  
> [!NOTE]
>  在應用程式中啟用網路追蹤時，這個成員會輸出追蹤資訊。  如需詳細資訊，請參閱＜網路追蹤＞。  
  
## 請參閱  
 [啟用網路追蹤](../../../docs/framework/network-programming/enabling-network-tracing.md)   
 [HOW TO:設定網路追蹤](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)   
 [解譯網路追蹤](../../../docs/framework/network-programming/interpreting-network-tracing.md)   
 [Introduction to Instrumentation and Tracing](http://msdn.microsoft.com/zh-tw/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)