---
title: ".NET Core 執行階段識別項 (RID) 目錄"
description: ".NET Core 執行階段識別項 (RID) 目錄"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 08/22/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b2032f5d-771f-48d9-917c-587d9509035c
translationtype: Human Translation
ms.sourcegitcommit: 811b9539019b7cc2817b5742760ae52fbc2f95dd
ms.openlocfilehash: fc59a9f3333f01caf9622dd500a5de6e2ae5132b
ms.lasthandoff: 03/02/2017

---

# <a name="net-core-runtime-identifier-rid-catalog"></a>.NET Core 執行階段識別項 (RID) 目錄

## <a name="what-are-rids"></a>什麼是 RID？
RID 是*執行階段識別項*的縮寫。 RID 可用來識別執行應用程式或資產 (亦即組件) 的目標作業系統。 它們看起來類似："ubuntu.14.04-x64"、"win7-x64"、"osx.10.11-x64"。 針對具有原生相依性的套件，RID 也可指定能在哪些平台上還原套件。 

請務必注意，RID 是不透明的字串。 這表示它們必須完全相符，使用這些項目的作業才能正常運作。 舉例來說，讓我們來看看[基礎作業系統](https://elementary.io/)的案例，這個作業系統是 Ubuntu 14.04 的直接複製品。 雖然 .NET Core 和 CLI 可在該版本的 Ubuntu 上運作，但如果您不經任何修改就嘗試在基礎作業系統中加以使用，任何套件的還原作業將會失敗。 這是因為我們目前沒有任何 RID 指定將基礎作業系統做為平台。 

代表具體作業系統的 RID 通常遵循 `[os].[version]-[arch]` 這個模式，其中：
- `ubuntu` 是作業系統 Moniker，例如 `[os]`。
- `[version]` 是作業系統版本，其中以點 (`.`) 來分隔版本號碼，例如 `15.10`，其精確度足以合理允許資產將目標設為該版本所代表的作業系統平台 API。
  - 此項目**不應為**行銷版本，因為行銷版本通常代表多個作業系統個別版本，且搭配不同平台 API 介面區。
- `[arch]` 是處理器架構，例如 `x86`、`x64`、`arm`、`arm64` 等。

`Microsoft.NETCore.Platforms` 套件的 `runtime.json` 檔案中有定義 RID 圖形，您可以在 [CoreFX 存放庫](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json)中看到這個檔案。 使用此檔案時，您會發現部分 RID 當中有 `"#import"` 陳述式。 這些陳述式是相容性陳述式。 這表示如果某個 RID 包含匯入的 RID，它就可能是該 RID 還原套件的目標。 聽起來有點令人困惑，讓我們來看看範例。 舉 macOS 來說：

```json
"osx.10.11-x64": {
    "#import": [ "osx.10.11", "osx.10.10-x64" ]
}
```
上述 RID 指定 `osx.10.11-x64` 匯入 `osx.10.10-x64`。 這表示，如果套件指定在 `osx.10.11-x64` 上需具備 `osx.10.10-x64`，則在還原套件時 NuGet 可順利還原這些套件。

稍大的 RID 圖形範例：  

- `win10-arm`
  - `win10`
  - `win81-arm`
    - `win81`
    - `win8-arm`
      - `win8`
        - `win7`
          - `win`
            - `any`

所有的 RID 最終將對應至根 `any` RID。

雖然 RID 似乎很容易使用，但在使用時也要謹記一些特殊的注意事項︰

* 它們是**不透明字串**，且應該視為黑箱處理。
    * 您不應以程式設計方式建構 RID。
* 您必須使用已針對平台定義且這份文件中有說明的 RID。
* RID 具有針對性，因此請不要從實際的 RID 值來進行假設；請參閱這份文件，判斷特定平台所需的 RID。

## <a name="using-rids"></a>使用 RID
若要使用 RID，必須先了解有哪些 RID。 新的 RID 會定期新增至平台。 如需最新的版本，請查看 CoreFX 存放庫上的 [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) 檔案。

> [!NOTE]
> 我們正努力以互動性更高的形式提供這些資訊。 等這項工作完成時，此頁面即會更新為指向該工具及/或其使用方式的文件。 

## <a name="windows-rids"></a>Windows RID

* Windows 7/Windows Server 2008 R2
    * `win7-x64`
    * `win7-x86`
* Windows 8/Windows Server 2012
    * `win8-x64`
    * `win8-x86`
    * `win8-arm`
* Windows 8.1/Windows Server 2012 R2
    * `win81-x64`
    * `win81-x86`
    * `win81-arm`
* Windows 10/Windows Server 2016
    * `win10-x64`
    * `win10-x86`
    * `win10-arm`
    * `win10-arm64`

## <a name="linux-rids"></a>Linux RID

* Red Hat Enterprise Linux
    * `rhel.7-x64`
* Ubuntu
    * `ubuntu.14.04-x64`
    * `ubuntu.14.10-x64`
    * `ubuntu.15.04-x64`
    * `ubuntu.15.10-x64`
    * `ubuntu.16.04-x64`
    * `ubuntu.16.10-x64`
* CentOS
    * `centos.7-x64`
* Debian
    * `debian.8-x64`
* Fedora
    * `fedora.23-x64`
    * `fedora.24-x64`
* OpenSUSE
    * `opensuse.13.2-x64`
    * `opensuse.42.1-x64`
* Oracle Linux
    * `ol.7-x64`
    * `ol.7.0-x64`
    * `ol.7.1-x64`
    * `ol.7.2-x64`
* 目前支援的 Ubuntu 衍生項目 
    * `linuxmint.17-x64`
    * `linuxmint.17.1-x64`
    * `linuxmint.17.2-x64`
    * `linuxmint.17.3-x64`
    * `linuxmint.18-x64`

## <a name="os-x-rids"></a>OS X RID

* `osx.10.10-x64`
* `osx.10.11-x64`
* `osx.10.12-x64`

