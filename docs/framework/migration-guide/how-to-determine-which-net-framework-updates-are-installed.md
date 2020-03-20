---
title: 請參閱已安裝的 .NET 框架安全更新和修補程式
description: 了解如何判斷電腦上所安裝的 .NET Framework 安全性更新與 Hotfix。
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
ms.openlocfilehash: 5c7bf48d5786530a9bcb69fb7cf605ac2c80a4eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181274"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>如何確定哪些 .NET 框架安全更新和修補程式已安裝

本文說明如何找出安裝在電腦上的 .NET Framework 安全性更新與 Hotfix。

> [!NOTE]
> 本文中展示的所有技術，皆需要使用具備系統管理權限的帳戶。

## <a name="use-registry-editor"></a>使用登錄編輯程式

已為電腦上安裝之各版 .NET Framework 所安裝之安全性更新與 Hotfix，都列於 Windows 登錄中。 您可使用登錄編輯程式 (*regedit.exe*) 程式，檢視此資訊。

1. 開啟 **regedit.exe** 程式。 在 Windows 8 和更高版本中，**按右鍵** ![Windows 金鑰徽標的開始螢幕截圖。，](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "視窗鍵盤logo")然後選擇"**運行**"。 在 [開啟]**** 方塊中，輸入 **regedit**，然後選取 [確定]****。

2. 在 [登錄編輯程式] 中，開啟下列子機碼：

     **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**

     已安裝的更新會列於子機碼下，這些子機碼可識別套用更新的 .NET Framework 版本。 每個更新都是透過知識庫 (KB) 號碼加以識別。

在登錄編輯程式中，.NET Framework 版本和每一版已安裝的更新會儲存在不同的子機碼中。 如需偵測已安裝之版本號碼的相關資訊，請參閱[如何：判斷安裝的 .NET Framework 版本](how-to-determine-which-versions-are-installed.md)。

## <a name="query-the-registry-using-code"></a>使用代碼查詢註冊表

下列範例以程式設計方式判斷電腦上安裝的 .NET Framework 安全性更新與 Hotfix：

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

該範例會產生類似如下的輸出：

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="use-powershell-to-query-the-registry"></a>使用 PowerShell 查詢註冊表

下列範例示範如何使用 PowerShell 判斷電腦上安裝的 .NET Framework 安全性更新與 Hotfix：

```powershell
$DotNetVersions = Get-ChildItem HKLM:\SOFTWARE\WOW6432Node\Microsoft\Updates | Where-Object {$_.name -like
 "*.NET Framework*"}

ForEach($Version in $DotNetVersions){

   $Updates = Get-ChildItem $Version.PSPath
    $Version.PSChildName
    ForEach ($Update in $Updates){
       $Update.PSChildName
       }
}
```

該範例會產生類似如下的輸出：

```console
Microsoft .NET Framework 4 Client Profile
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
Microsoft .NET Framework 4 Extended
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
```

## <a name="see-also"></a>另請參閱

- [如何：確定安裝了哪些 .NET 框架版本](how-to-determine-which-versions-are-installed.md)
- [安裝適用於開發人員的 .NET Framework](../install/guide-for-developers.md)
- [版本和相依性](versions-and-dependencies.md)
