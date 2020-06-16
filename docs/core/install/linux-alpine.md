---
title: 在 Alpine 上安裝 .NET Core-.NET Core
description: 示範在 Alpine 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: bbaf4ee9020dcd33c894b5376bf04ad65db8d378
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "84771500"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a>在 Alpine 上安裝 .NET Core SDK 或 .NET Core 執行時間

本文說明如何在 Alpine 上安裝 .NET Core。 當 Alpine 版本不支援時，該版本就不再支援 .NET Core。 不過，這些指示可以協助您取得在這些版本上執行的 .NET Core，即使它不受支援也一樣。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

沒有安裝程式可供 Alpine。 您必須使用[安裝腳本](#scripted-install)或遵循[手動安裝](#manual-install)指示。

## <a name="supported-distributions"></a>支援的發行版本

下表列出目前支援的 .NET Core 版本，以及支援的 Alpine 版本。 在[.Net Core 版本達到支援終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)，或[Alpine 版本達到生命週期結束](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)之前，這些版本仍受到支援。

- ✔️表示仍然支援 Alpine 或 .NET Core 的版本。
- A ❌ 表示該 Alpine 版本不支援 Alpine 或 .Net Core 的版本。
- 當 Alpine 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。

| Alpine                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview |
|--------------------------|---------------|---------------|----------------|
| ✔️3.12  | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️3.11  | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️3.10  | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️3。9   | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ❌3.8   | ✔️2。1        | ❌3.1        | ❌5.0 預覽 |

已不再支援下列 .NET Core 版本。 這些下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

## <a name="dependencies"></a>相依性

Alpine Linux 上的 .NET Core 需要安裝下列相依性：

- icu-程式庫
- krb5-libs
- libintl
- libssl1.0.0 1.1 （Alpine v 3.9 或更新版本）
- libssl1.0.0 1.0 （Alpine 3.8）
- libstdc++
- lttng-ust
- numactl （選擇性）
- zlib

## <a name="scripted-install"></a>腳本式安裝

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動安裝

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>後續步驟

- [教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式](../tutorials/with-visual-studio-code.md)
