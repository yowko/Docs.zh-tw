---
title: 在 Alpine 上安裝 .NET-.NET
description: 示範在 Alpine 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 6adaa905c400b45526ebbc3d8e2606522863eec3
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970846"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a>在 Alpine 上安裝 .NET SDK 或 .NET 執行時間

本文說明如何在 Alpine 上安裝 .NET。 當 Alpine 版本不受支援時，就不再支援該版本的 .NET。 不過，這些指示可協助您讓 .NET 在這些版本上執行，即使它不受支援也是一樣。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install"></a>安裝

安裝程式不適用於 Alpine Linux。 您必須以下列其中一種方式安裝 .NET：

- [貼齊套件](linux-snap.md)
- [使用 _install-dotnet.sh_ 編寫腳本的安裝](linux-scripted-manual.md#scripted-install)
- [手動二進位解壓縮](linux-scripted-manual.md#manual-install)

## <a name="supported-distributions"></a>支援的發行版本

下表列出目前支援的 .NET 版本，以及其支援的 Alpine 版本。 除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Alpine 的版本 [達到生命週期結束](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)，否則仍支援這些版本。

- ✔️表示仍支援 Alpine 或 .NET 版本。
- ❌指出該 Alpine 版本不支援 Alpine 或 .net 版本。
- 當版本的 Alpine 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。

| Alpine  | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
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

## <a name="next-steps"></a>後續步驟

- [如何啟用 .NET CLI 的 TAB 鍵自動完成](../tools/enable-tab-autocomplete.md)
- [教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code](../tutorials/with-visual-studio-code.md)
