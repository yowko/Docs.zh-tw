---
title: "設定密碼編譯類別 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - ".NET Framework 應用程式組態, 密碼編譯"
  - "組態檔 [.NET Framework], 密碼編譯"
  - "密碼編譯演算法"
  - "密碼編譯, 類別"
  - "預設密碼編譯"
  - "安全性 [.NET Framework], 加密"
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 設定密碼編譯類別
[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 允許電腦管理員設定 .NET Framework 和適當編寫之應用程式所使用的預設密碼編譯演算法和演算法實作 \(Implementation\)。例如，企業可將自己的密碼編譯演算法實作設定為預設實作，而不是 [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)] 中所隨附的實作。  雖然使用密碼編譯的 Managed 應用程式可以一直選擇明確地繫結至特定實作，但建議您讓它們使用密碼編譯組態系統來建立密碼編譯物件。  
  
## 在本節中  
 [將演算法名稱對應至密碼編譯類別](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 說明如何對應演算法名稱至密碼編譯類別。  
  
 [對應物件識別項至密碼編譯演算法](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 說明如何對應物件識別項至密碼編譯演算法。  
  
## 相關章節  
 [密碼編譯服務](../../../docs/standard/security/cryptographic-services.md)  
 提供 [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)] 所提供之密碼編譯服務的概觀。  
  
 [密碼編譯設定結構描述](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 說明對應易記演算法名稱至實作密碼編譯演算法之類別的項目。