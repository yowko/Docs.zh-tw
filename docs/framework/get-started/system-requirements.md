---
title: ".NET Framework 系統需求 | Microsoft Docs"
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
  - "軟體需求"
  - ".NET Framework, 系統需求"
  - "系統需求"
  - "支援的作業系統"
  - "硬體需求"
ms.assetid: 298275e2-da1d-4618-9f74-6a3567832350
caps.latest.revision: 95
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 91
---
# .NET Framework 系統需求
本主題中的表格提供 .NET Framework 4.5 與其單點發行版本 \(4.5.1 和 4.5.2\) 以及 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 與其單點發行版本 \(4.6.1 和 4.6.2\) 的硬體、作業系統和軟體需求。 您用以開發 .NET Framework 應用程式的開發環境，則會有另一組不同的需求。  
  
 如需下載資訊和連結，請參閱 [安裝指南](../../../docs/framework/install/guide-for-developers.md)。  
  
 如需 .NET Framework 版本支援週期的相關資訊，請參閱 [Microsoft 支援週期](https://support.microsoft.com/en-us/lifecycle/search?sort=PN&alpha=Microsoft%20.NET%20Framework&Filter=FilterNO)。  
  
## 硬體需求  
  
|||  
|-|-|  
|**處理器**|1 GHz|  
|**RAM**|512 MB|  
|**磁碟空間 \(最小\)**||  
|32 位元|4.5 GB|  
|64 位元|4.5 GB|  
  
## 安裝需求  
  
-   必須有系統管理員權限才能安裝 .NET Framework。 如果您在要安裝 .NET Framework 的電腦上沒有系統管理員權限，請連絡您的網路系統管理員。  
  
## 支援的用戶端作業系統  
  
|作業系統|支援的版本|與作業系統一起預先安裝|可個別安裝|  
|----------|-----------|-----------------|-----------|  
|Windows 10 年度更新|32 位元和 64 位元|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]||  
|Windows 10 11 月更新|32 位元和 64 位元|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|  
|Windows 10|32 位元和 64 位元|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|  
|[!INCLUDE[win81](../../../includes/win81-md.md)]|32 位元、64 位元和 ARM|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]|[!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|  
|[!INCLUDE[win8](../../../includes/win8-md.md)]|32 位元、64 位元和 ARM|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|  
|Windows 7 SP1|32 位元和 64 位元|\-\-|.NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|  
|Windows Vista SP2|32 位元和 64 位元|\-\-|.NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|  
|Windows XP|32 位元和 64 位元|\-\-|.NET Framework 4|  
  
 **注意:**  
  
-   在 Windows 7 系統中，.NET Framework 需要 Windows 7 SP1。 若您使用 Windows 7 而尚未安裝 Service Pack 1，就必須先加以安裝，才能安裝 .NET Framework。  
  
-   Windows 預先安裝環境 \(Windows PE\) 支援 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]。 並非所有的功能在 Windows PE 上都支援。  
  
-   .NET Framework 4 也支援 IA64 平台。  
  
-   對於所有平台，建議您升級至 [Windows Update 網站](http://go.microsoft.com/fwlink/?LinkId=168461)上提供的最新 Windows Service Pack 和安裝重要更新，確保有最佳相容性與安全性。  
  
-   在 64 位元作業系統上，.NET Framework 同時支援 WOW64 \(在 64 位元電腦上進行 32 位元處理\) 和原生 64 位元處理。  
  
## 支援的伺服器作業系統  
  
|作業系統|支援的版本|與作業系統一起預先安裝|可個別安裝|  
|----------|-----------|-----------------|-----------|  
|[!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]|64 位元|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]|[!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|  
|[!INCLUDE[winserver8](../../../includes/winserver8-md.md)] \(64 位元版本\)|64 位元|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|  
|Windows Server 2008 R2 SP1|64 位元|\-\-|.NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|  
|Windows Server 2008 SP2|32 位元和 64 位元|\-\-|.NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|  
  
 **注意:**  
  
-   [!INCLUDE[winserver8](../../../includes/winserver8-md.md)] 包含 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]，因此，您不需要另外安裝。 同樣地，[!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] 包含 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]。  
  
-   .NET Framework 在 Windows Server R2 SP1 \(含\) 以後版本的 Server Core 角色中受支援，但在適用於 Itanium 型系統的 Windows Server 2008 R2 中則不受支援。  
  
-   Windows Server 2008 SP2，Server Core 角色不支援 .NET Framework。  
  
-   對於所有平台，建議您升級至 [Windows Update 網站](http://go.microsoft.com/fwlink/?LinkId=168461)上提供的最新 Windows Service Pack 和重要更新，確保有最佳相容性與安全性。 某些作業系統上可能需要安裝最新的 Windows Service Pack。  
  
-   在 64 位元作業系統上，.NET Framework 同時支援 WOW64 \(在 64 位元電腦上進行 32 位元處理\) 和原生 64 位元處理。  
  
## 請參閱  
 [安裝指南](../../../docs/framework/install/guide-for-developers.md)   
 [快速入門](../../../docs/framework/get-started/index.md)   
 [疑難排解](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)