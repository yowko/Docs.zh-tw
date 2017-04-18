---
title: "使用 .NET Native 編譯應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET 和機器碼"
  - ".NET Native"
  - "C# 和原生編譯"
  - "使用 .NET Native 編譯"
  - "原生編譯"
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
caps.latest.revision: 27
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 27
---
# 使用 .NET Native 編譯應用程式
[!INCLUDE[net_native](../../../includes/net-native-md.md)] 是用於建置及部署 Windows 應用程式的先行編譯技術，包含於 [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)] 中。 此工具可將以 Managed 程式碼 \(C\# 或 Visual Basic\) 撰寫且目標為 .NET Framework 和 Windows 10 的應用程式發行版本自動編譯為機器碼。  
  
 一般而言，以 .NET Framework 為目標的應用程式會編譯成中繼語言 \(IL\)。 在執行階段，just\-in\-time \(JIT\) 編譯器會將 IL 轉譯成機器碼。 相對地，[!INCLUDE[net_native](../../../includes/net-native-md.md)] 則會將 Windows 應用程式直接編譯成機器碼。 對開發人員而言，這表示：  
  
-   您的應用程式將會提供較佳的機器碼效能。  
  
-   您可以繼續以 C\# 或 Visual Basic 進行程式設計。  
  
-   您可以繼續利用 .NET Framework 所提供的資源，包括其類別庫、自動記憶體管理和記憶體回收，以及例外狀況處理。  
  
 對應用程式的使用者而言，[!INCLUDE[net_native](../../../includes/net-native-md.md)] 可提供下列優點：  
  
-   快速的執行時間  
  
-   一貫快速的啟動時間  
  
-   部署和更新成本低  
  
-   最佳化的應用程式記憶體使用量  
  
 但是 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 牽涉到多項機器碼編譯。 它會將轉換 .NET Framework 應用程式建置和執行的方式。 特別之處在於：  
  
-   在預先編譯期間，.NET Framework 的必要部分會以靜態方式連結到您的應用程式。 這樣可以讓應用程式以 .NET Framework 的 app\-local 程式庫來執行，並且讓編譯器執行全域分析，以提供優異的效能。 如此一來，即使 .NET Framework 更新之後，應用程式還是一貫地會以更快的速度啟動。  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)] 執行階段已針對靜態預先編譯進行最佳化，因此能夠提供更優異的效能。 同時，它還保留了開發人員會覺得生產力極佳的核心反映功能。  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)] 使用與 C\+\+ 編譯器相同的後端，其已針對靜態預先編譯案例進行最佳化。  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 能夠將 C\+\+ 的效能優點帶給 Managed 程式碼開發人員，因為其實它是使用與 C\+\+ 相同或類似的工具，此下表所示。  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|C\+\+|  
|-|----------------------------------------------------------------|-----------|  
|程式庫|.NET Framework \+ Windows 執行階段|Win32 \+ Windows 執行階段|  
|編譯器|UTC 最佳化編譯器|UTC 最佳化編譯器|  
|已部署|可立即執行的二進位檔案|可立即執行的二進位檔案 \(ASM\)|  
|執行階段|MRT.dll \(最小 CLR 執行階段\)|CRT.dll \(C 執行階段\)|  
  
 針對適用於 Windows 10 的 Windows 應用程式，您要將應用程式封裝 \(.appx 檔\) 中的 .NET 機器碼編譯二進位檔上傳至 Windows 市集。  
  
## 在本節中  
 如需有關使用 .NET 機器碼編譯來開發應用程式的詳細資訊，請參閱下列主題：  
  
-   [開始使用 .NET 機器碼編譯：開發人員經驗逐步解說](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   [.NET 原生和編譯：](../../../docs/framework/net-native/net-native-and-compilation.md).NET 原生如何將您的專案編譯成原生程式碼。  
  
-   [反映和 .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [依賴反映的 API](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [反映 API 參考](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [執行階段指示詞 \(rd.xml\) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [序列化和中繼資料](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [將您的 Windows 市集應用程式移轉至 .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [.NET Native 一般疑難排解](../../../docs/framework/net-native/net-native-general-troubleshooting.md)  
  
## 請參閱  
 [.NET Native 常見問題集](http://msdn.microsoft.com/vstudio/dn642499.aspx)