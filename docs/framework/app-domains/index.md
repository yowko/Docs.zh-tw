---
title: "使用應用程式定義域和組件設計程式 | Microsoft Docs"
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
  - "應用程式定義域, 程式設計"
  - "組件 [.NET Framework], 程式設計"
  - "程式設計應用程式定義域"
  - "程式設計組件"
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 使用應用程式定義域和組件設計程式
Microsoft Internet Explorer、ASP.NET 和 Windows Shell 等主應用程式 \(Host\) 會將 Common Language Runtime 載入處理序 \(Process\)、在該處理序中建立[應用程式定義域](../../../docs/framework/app-domains/application-domains.md)，然後在執行 .NET Framework 應用程式時載入並執行該應用程式定義域中的使用者程式碼。  在多數情況下，您無須擔心需要建立應用程式定義域和將組件載入應用程式定義域中，因為執行階段主應用程式會執行這些工作。  
  
 但如果您要建立可裝載 Common Language Runtime 的應用程式、建立工具或程式碼來卸載程式、或建立執行時可卸載或重新裝載的外掛式元件，那麼您可以建立自己的應用程式定義域。  即使您不需要建立執行階段主應用程式，本章節亦將提供如何使用載入這些應用程式定義域中的應用程式定義域和組件的重要資訊。  
  
## 在本節中  
 [應用程式定義域和組件 HOW TO 主題](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 提供在有關應用程式定義域和組件的程式設計之概念性文件中找到之所有 HOW TO 主題之連結。  
  
 [使用應用程式定義域](../../../docs/framework/app-domains/use.md)  
 提供建立、組態和使用應用程式定義域範例。  
  
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 說明如何建立、簽名和設定組件上的屬性。  
  
## 相關章節  
 [發出動態方法和組件](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 說明如何建立動態組件。  
  
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 提供組件的概觀。  
  
 [應用程式定義域](../../../docs/framework/app-domains/application-domains.md)  
 提供應用程式定義域的概觀。  
  
 [反映概觀](../../../docs/framework/reflection-and-codedom/reflection.md)  
 說明如何使用 **Reflection** 類別取得組件的資訊。