---
title: 在完全信任環境下執行內部網路應用程式
description: 以完全信任的方式執行 .NET Framework 3.5 SP1 的內部網路應用程式。 應用程式及其程式庫元件可以從網路共用以完全信任元件的形式執行。
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
ms.openlocfilehash: 01d98a1ca7ce67088b4f04bedf7e3ef02e0ca7a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723710"
---
# <a name="running-intranet-applications-in-full-trust"></a>在完全信任環境下執行內部網路應用程式

從 .NET Framework 3.5 版 Service Pack 1 (SP1) 開始，應用程式及其程式庫組件可以當成來自網路共用的完全信任組件執行。 <xref:System.Security.SecurityZone.MyComputer> 區域辨識項會自動新增至從內部網路共用載入的組件。 這個辨識項會提供這些組件與電腦上組件相同的授權集 (通常為完全信任)。 此功能不適用於 ClickOnce 應用程式或專為主機設計執行的應用程式。

## <a name="rules-for-library-assemblies"></a>程式庫組件規則

下列規則適用於可執行檔在網路共用上載入的組件：

- 程式庫組件必須和可執行組件位於相同的資料夾。 完全信任的授權集不提供給位於子資料夾或於不同路徑參考的組件。

- 如果可執行檔延遲載入組件，即必須使用啟動可執行檔所用的相同路徑。 例如，如果共用 \\ \\ *網路-電腦* \\ *共用* 對應到磁碟機號，而可執行檔是從該路徑執行，則使用網路路徑所載入之可執行檔的元件將不會被授與完全信任。 若要在 <xref:System.Security.SecurityZone.MyComputer> 區域中延遲載入組件，可執行檔必須使用磁碟機代號路徑。

## <a name="restoring-the-former-intranet-policy"></a>還原先前的內部網路原則

在舊版的 .NET Framework 中，共用的組件被授與 <xref:System.Security.SecurityZone.Intranet> 區域辨識項。 您必須指定程式碼存取安全性原則，才能授與共用組件完全信任。

此新行為是內部網路組件的預設值。 您可以設定適用於電腦上所有應用程式的登錄機碼，回到提供 <xref:System.Security.SecurityZone.Intranet> 辨識項的先前行為。 此程序在 32 位元電腦和 64 位元電腦中是不同的：

- 在 32 位元電腦系統登錄的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 機碼下，建立子機碼。 使用 DWORD 值為 1 的機碼名稱 LegacyMyComputerZone。

- 在 64 位元電腦系統登錄的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 機碼下，建立子機碼。 使用 DWORD 值為 1 的機碼名稱 LegacyMyComputerZone。 在 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework 機碼下建立相同的子機碼。

## <a name="see-also"></a>另請參閱

- [使用組件設計程式](../../standard/assembly/index.md)
