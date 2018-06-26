---
title: dotnet store 命令
description: "'dotnet store' 命令會在執行階段套件存放區中儲存指定的組件。"
author: bleroy
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 54654522207157f7d49bb86223b7986acccf51ee
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696321"
---
# <a name="dotnet-store"></a>dotnet store

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>名稱

`dotnet store` - 會在[執行階段套件存放區](../deploying/runtime-store.md)中儲存指定的組件。

## <a name="synopsis"></a>概要

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a>描述

`dotnet store` 會在[執行階段套件存放區](../deploying/runtime-store.md)中儲存指定的組件。 根據預設，會針對目標執行階段和架構最佳化組件。 如需詳細資訊，請參閱[執行階段套件存放區](../deploying/runtime-store.md)主題。

## <a name="required-options"></a>必要選項

`-f|--framework <FRAMEWORK>`

指定[目標 Framework](../../standard/frameworks.md)。

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

「套件存放區資訊清單檔」是 XML 檔，包含要儲存的套件清單。 資訊清單檔的格式相容於 SDK 樣式專案格式。 因此，參考所需套件的專案檔可以搭配 `-m|--manifest` 選項，將組件儲存在執行階段套件存放區中。 若要指定多個資訊清單檔，請為每個檔案重複選項和路徑。 例如：`--manifest packages1.csproj --manifest packages2.csproj`。

`-r|--runtime <RUNTIME_IDENTIFIER>`

目標的[執行階段識別碼](../rid-catalog.md)。

## <a name="optional-options"></a>選擇性的選項

`--framework-version <FRAMEWORK_VERSION>`

指定 .NET Core SDK 版本。 此選項可讓您在 `-f|--framework` 選項指定的 Framework 之外，選取特定的 Framework 版本。

`-h|--help`

顯示說明資訊。

`-o|--output <OUTPUT_DIRECTORY>`

指定執行階段套件存放區的路徑。 如未指定，則預設為使用者設定檔 .NET Core 安裝目錄的 *store* 子目錄。

`--skip-optimization`

略過最佳化階段。

`--skip-symbols`

略過符號產生。 目前，只能在 Windows 和 Linux 產生符號。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

命令使用的工作目錄。 如未指定，則使用目前目錄的 *obj* 子目錄。

## <a name="examples"></a>範例

儲存 .NET Core 2.0.0 的 *packages.csproj* 專案中指定的套件：

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

儲存 *packages.csproj* 中指定的套件，不需要最佳化：

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a>另請參閱

[執行階段套件存放區](../deploying/runtime-store.md)