---
title: "如何：使用 DEVPATH 找出組件 | Microsoft Docs"
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
  - ".NET Framework 應用程式組態, 組件"
  - "app.config 檔案, 組件位置"
  - "應用程式組態檔, 指定組件的位置"
  - "組件 [.NET Framework], 位置"
  - "DEVPATH"
  - "尋找組件"
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# 如何：使用 DEVPATH 找出組件
開發人員可能會想要確定他們正在建置的共用組件是否能夠與多個應用程式一起正常運作。  不需在開發循環一再將組件置於全域組件快取，開發人員可代之以建立 DEVPATH 環境變數來指向組件的組建輸出目錄。  
  
 例如，假設您正在建置 \(Build\) 稱為 MySharedAssembly 的共用組件，而輸出目錄為 C:\\MySharedAssembly\\Debug。  您可以將 C:\\MySharedAssembly\\Debug 放在 DEVPATH 變數中。  接著您必須在電腦組態檔中指定 [\<developmentMode\>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) 項目。  這個項目會告訴 Common Language Runtime 要使用 DEVPATH 來找出組件。  
  
 共用組件必須要能被執行階段發現。若要指定私用目錄以解析組件參考，請在組態檔中使用 [\<codeBase\> 項目](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)或 [\<probing\> 項目](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)，如[指定組件的位置](../../../docs/framework/configure-apps/specify-assembly-location.md)中所述。您也可以將組件放在應用程式目錄的某個子目錄中。  如需詳細資訊，請參閱[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
> [!NOTE]
>  這是進階功能，是專為開發用途而設計。  
  
 下列範例顯示如何使執行階段在 DEVPATH 環境變數所指定的目錄中搜尋組件。  
  
## 範例  
  
```  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 這個設定值預設為 false。  
  
> [!NOTE]
>  這個設定只可以在程式開發階段使用。  Runtime 不會檢查在 DEVPATH 中所找到的強式名稱組件版本。  它只使用它所找到的第一個版本。  
  
## 請參閱  
 [Configuring .NET Framework Apps](http://msdn.microsoft.com/zh-tw/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)