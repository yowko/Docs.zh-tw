---
title: "在完全信任環境下執行內部網路應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
caps.latest.revision: 20
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 58eeda82c66ecda6ffd714e808b006634ccba804
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 在完全信任環境下執行內部網路應用程式
從 .NET Framework 3.5 版 Service Pack 1 \(SP1\) 開始，可以從網路共用上將應用程式及其程式庫組件視為完全信任的組件執行。  <xref:System.Security.SecurityZone> 區域辨識項會自動加入至從內部網路上之共用所載入的組件。  此辨識項可授與這些組件與電腦上的組件相同的授權集 \(通常為完全信任\)。  此功能不適用於 ClickOnce 應用程式或設計在主機上執行的應用程式。  
  
## 程式庫組件的規則  
 下列規則會套用到網路共用上的可執行檔載入的組件：  
  
-   程式庫組件必須位於可執行檔組件的同一個資料夾中。  位於子資料夾或在不同路徑上參考的組件則不會給予完全信任授權集。  
  
-   如果可執行檔延遲載入組件，它必須使用先前用來啟動可執行檔的相同路徑。  例如，如果共用 \\\\*network\-computer*\\*share* 對應至某個磁碟機代號，而可執行檔從該路徑執行，則可執行檔使用網路路徑載入的組件將不會給予完全信任。  若要延遲載入 <xref:System.Security.SecurityZone> 區域中的組件，可執行檔必須使用磁碟機代號路徑。  
  
## 還原先前的內部網路原則  
 在 .NET Framework 先前的版本中，會將 <xref:System.Security.SecurityZone> 區域辨識項授與共用組件。  您必須指定程式碼存取安全性原則，才能授與完全信任給共用上的組件。  
  
 這個行為現在則是內部網路組件的預設行為。  您可以設定套用到電腦上所有應用程式的登錄機碼，恢復原來提供 <xref:System.Security.SecurityZone> 辨識項的行為。  32 位元和 64 位元電腦的程序不同：  
  
-   在 32 位元電腦上，在系統登錄的 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework 機碼底下建立子機碼。  使用機碼名稱 LegacyMyComputerZone，並將 DWORD 值設為 1。  
  
-   在 64 位元電腦上，在系統登錄的 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework 機碼底下建立子機碼。  使用機碼名稱 LegacyMyComputerZone，並將 DWORD 值設為 1。  在 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework 機碼底下建立相同的子機碼。  
  
## <a name="see-also"></a>另請參閱  
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)

