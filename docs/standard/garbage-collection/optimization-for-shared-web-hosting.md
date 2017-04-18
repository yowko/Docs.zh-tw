---
title: "Optimization for Shared Web Hosting | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "garbage collection, Web hosting"
  - "garbage collection, optimizing"
  - "garbage collection, shared Web hosting"
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Optimization for Shared Web Hosting
如果您是裝載多個小網站的共用伺服器管理員，您可以在 .NET Framework 目錄中，將下列 `gcTrimCommitOnLowMemory` 設定新增至 Aspnet.config 檔案中的 `runtime` 節點，以達到最佳效能，並提高網站容量：  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  這個設定只建議使用於共用 Web 主機的情況。  
  
 因為記憶體回收行程會保留記憶體以便日後配置，所以認可的空間會比實際所需的更大。  您可以減少這個空間，以配合有時候系統記憶體重度負載的情況。  減少認可的空間，可以提高效能並擴充容量以裝載更多網站。  
  
 啟用 `gcTrimCommitOnLowMemory` 設定時，記憶體回收行程會評估系統記憶體負載，並於負載達到 90% 時進入調整模式。  調整模式會一直持續到負載降至 85% 為止。  
  
 如果條件允許，記憶體回收行程可以決定 `gcTrimCommitOnLowMemory` 設定不協助目前的應用程式，並且忽略此應用程式。  
  
## 範例  
 下列 XML 片段顯示如何啟用 `gcTrimCommitOnLowMemory` 設定。  省略符號表示 `runtime` 節點中的其他設定。  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## 請參閱  
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)