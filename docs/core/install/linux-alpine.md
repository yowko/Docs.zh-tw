---
title: 在 Alpine 上安裝 .NET-.NET
description: 示範在 Alpine 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 29901cc24ddd4bbe8200a36765ddd29f501394c0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506814"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a>在 Alpine 上安裝 .NET SDK 或 .NET 執行時間

本文說明如何在 Alpine 上安裝 .NET。 當 Alpine 版本不受支援時，就不再支援該版本的 .NET。 不過，這些指示可協助您讓 .NET 在這些版本上執行，即使它不受支援也是一樣。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

沒有適用于 Alpine 的安裝程式。 您必須使用 [安裝腳本](#scripted-install) ，或遵循 [手動安裝](#manual-install) 指示。

## <a name="supported-distributions"></a>支援的發行版本

下表列出目前支援的 .NET 版本，以及其支援的 Alpine 版本。 除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Alpine 的版本 [達到生命週期結束](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)，否則仍支援這些版本。

- ✔️表示仍支援 Alpine 或 .NET 版本。
- ❌指出該 Alpine 版本不支援 Alpine 或 .net 版本。
- 當版本的 Alpine 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。

| Alpine  | .NET Core 2.1 | .NET Core 3.1 | .NET 5。0 |
|-------- |---------------|---------------|----------------|
| ✔️3.12 | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ✔️3.11 | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ✔️3.10 | ✔️2。1        | ✔️3。1        | ❌ 5.0 |
| ❌ 3.9  | ✔️2。1        | ✔️3。1        | ❌ 5.0 |
| ❌ 3.8  | ✔️2。1        | ✔️3。1        | ❌ 5.0 |

不再支援下列 .NET 版本。 這些內容的下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

## <a name="dependencies"></a>相依性

Alpine Linux 上的 .NET 需要安裝下列相依性：

- icu-程式庫
- krb5-libs
- libgcc
- libintl
- libssl1.0.0 1.1 (Alpine 3.9 或更高版本) 
- libssl1.0.0 1.0 (Alpine 3.8 或更低) 
- libstdc++
- zlib

## <a name="scripted-install"></a>腳本式安裝

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動安裝

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>後續步驟

- [教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code](../tutorials/with-visual-studio-code.md)
