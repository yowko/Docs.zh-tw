---
title: "如何： 判斷已安裝哪些.NET Framework 安全性更新和 hotfix"
description: "了解如何判斷電腦上已安裝哪些.NET Framework 安全性更新和 hotfix。"
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c35705470a8e1b553eca2ca0c68d3b8b9b3f6fa6
ms.sourcegitcommit: a3ba258f7a8cab5c6d19a3743dd95e904ecebc44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>如何： 判斷已安裝哪些.NET Framework 安全性更新和 hotfix

本文將說明如何找出哪些.NET Framework 安全性更新，並在電腦上已安裝 hotfix。

> [!NOTE]
> 本文中所顯示的所有技術都需要具有系統管理權限的帳戶。

## <a name="to-find-installed-updates-using-the-registry"></a>尋找已安裝的更新登錄

Windows 登錄中列出的已安裝的安全性更新和 hotfix 的電腦上安裝的.NET Framework 的每個版本。 您可以使用登錄編輯程式 (*regedit.exe*) 若要檢視這項資訊的程式。

1. 開啟 **regedit.exe** 程式。 在 Windows 8 和更新版本中，以滑鼠右鍵按一下**啟動** ![Windows 標誌](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")，然後選取**執行**。 在**開啟**方塊中，輸入**regedit**選取**確定**。

2. 在 [登錄編輯程式] 中，開啟下列子機碼：

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     已安裝的更新會列於子機碼下，這些子機碼可識別套用更新的 .NET Framework 版本。 每個更新都是透過知識庫 (KB) 號碼加以識別。

在登錄編輯程式中，.NET Framework 版本和每一版已安裝的更新會儲存在不同的子機碼中。 如需偵測已安裝的版本號碼相關的資訊，請參閱[How to： 判斷已安裝哪些.NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)。

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>若要尋找安裝的更新藉由查詢程式碼中登錄

下列範例以程式設計方式判斷.NET Framework 安全性更新和 hotfix 安裝在電腦上：

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

這個範例會產生類似下列的輸出：

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

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>若要尋找安裝的更新藉由查詢在 PowerShell 中登錄

下列範例會示範如何判斷.NET Framework 安全性更新和 hotfix 安裝在電腦上使用 PowerShell:

```powershell
 Get-ChildItem "HKLM:SOFTWARE\Wow6432Node\Microsoft\Updates\*" -Recurse | Where-Object {$_.name -like
 "*.NET Framework*"}
```

這個範例會產生類似下列的輸出：

```console
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Client Profile


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y


    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Extended


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y
```

## <a name="see-also"></a>請參閱

[如何： 判斷已安裝哪些.NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
[安裝.NET Framework 開發人員](../../../docs/framework/install/guide-for-developers.md)  
[版本和相依性](../../../docs/framework/migration-guide/versions-and-dependencies.md)
