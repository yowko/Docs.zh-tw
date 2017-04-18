---
title: "從 .NET Framework 1.1 移轉 | Microsoft Docs"
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
  - ".NET Framework 1.1, 移轉至 .NET Framework 4.5"
  - ".NET Framework 4.5, 從 1.1 移轉"
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 從 .NET Framework 1.1 移轉
[!INCLUDE[win7](../../../includes/win7-md.md)] 和更新版本的 Windows 作業系統不支援 [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)]。 因此，以 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 為目標的應用程式一定要在 [!INCLUDE[win7](../../../includes/win7-md.md)] 或更新版本的作業系統上修改才能執行。 本主題討論在 [!INCLUDE[win7](../../../includes/win7-md.md)] 和更新版本的 Windows 作業系統底下執行以 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 為目標的應用程式時所需的步驟。 如需 [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)] 和 [!INCLUDE[win8](../../../includes/win8-md.md)] 的詳細資訊，請參閱[在 Windows 8 及更新版本上執行 .NET Framework 1.1 應用程式](../../../docs/framework/install/run-net-framework-1-1-apps.md)。  
  
## 重定目標或重新編譯  
 有兩種方式可取得之前使用 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 所編譯的應用程式，使其在 [!INCLUDE[win7](../../../includes/win7-md.md)] 和更新版本的 Windows 作業系統上執行：  
  
-   您可以重新設定應用程式的目標，使其在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 底下執行。 重新設定目標需要您將 [\<supportedRuntime\>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 項目加入至應用程式的組態檔，好讓它可以在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 之下執行。 這類組態檔的形式如下：  
  
    ```  
    <configuration> <startup> <supportedRuntime version="v4.0"/> </startup> </configuration>  
  
    ```  
  
-   您可以使用以 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 為目標的編譯器來重新編譯應用程式。 如果您原本使用 Visual Studio 2003 來開發及編譯您的方案，您可以在 [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] 中開啟此方案，並且使用 \[**專案相容性**\] 對話方塊來將此方案和專案檔從 Visual Studio 2003 使用的格式轉換成 [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] 使用的 Microsoft Build Engine \(MSBuild\) 格式。  
  
 不論您偏好重新編譯應用程式還是重新設定應用程式的目標，您都必須決定您的應用程式是否會受到較新 .NET Framework 版本中引入的任何變更所影響。 這些變更有兩種：  
  
-   在 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 與較新版 .NET Framework 之間發生的重大變更。  
  
-   在 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 與較新版 .NET Framework 之間，標示為已被取代或已過時的型別與型別成員。  
  
 當您重新設定應用程式的目標或重新編譯時，您應該針對 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 之後發行的每一個 .NET Framework 版本來檢閱重大變更及過時的型別和成員。  
  
## 重大變更  
 當發生重大變更時，重新設定目標及重新編譯的應用程式可能會有替代解決辦法可用 \(視特定變更而定\)。 在某些情況下，您可以將子項目加入至應用程式組態檔的 [\<runtime\>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 項目，以還原之前的行為。 例如，下列組態檔會還原 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 中使用的字串排序和比較行為，而且可以搭配重新設定目標或重新編譯的應用程式使用。  
  
```  
<configuration> <runtime> <CompatSortNLSVersion enabled="4096"/> </runtime> </configuration>  
  
```  
  
 但是在某些情況下，您可能必須修改原始程式碼及重新編譯應用程式。  
  
 若要評估可能的重大變更對您的應用程式的影響，您必須檢閱以下變更清單：  
  
-   [.NET Framework 2.0 中的重大變更](http://go.microsoft.com/fwlink/?LinkId=125263)記錄可能會影響以 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] 為目標之應用程式的 [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] 變更。  
  
-   [.NET Framework 3.5 SP1 中的變更](http://go.microsoft.com/fwlink/?LinkID=186989)記錄在 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] 之間的變更。  
  
-   [.NET Framework 4 移轉問題](http://msdn.microsoft.com/library/ee941656\(v=vs.100\).aspx)記錄在 [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] 和 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 之間的變更。  
  
## 過時的型別和成員  
 對於重新設定目標的應用程式和重新編譯的應用程式而言，已被取代的型別和成員的影響有些不同。 使用過時的型別和成員將不會影響重新設定目標的應用程式，除非已經從其組件中實際移除過時的型別或成員。 重新編譯使用過時型別或成員的應用程式通常會產生編譯器警告，而不是編譯器錯誤。 但是在某些情況下，它會產生編譯器錯誤，而且使用過時型別或成員的程式碼無法成功編譯。 在此情況下，您必須重新撰寫呼叫過時型別或成員的原始程式碼，然後重新編譯應用程式。 如需過時型別和成員的詳細資訊，請參閱 [類別庫中的過時功能](../../../docs/framework/whats-new/whats-obsolete.md)。  
  
 若要評估自從 [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] 發行之後已被取代之型別和成員的影響，請參閱 [類別庫中的過時功能](../../../docs/framework/whats-new/whats-obsolete.md)。 針對 [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)]、[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 檢閱過時的型別和成員清單。