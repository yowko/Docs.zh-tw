---
title: 執行時間程式庫總覽
description: 瞭解 [內容] 的 [執行時間程式庫] 區段中包含的內容。
author: tdykstra
ms.date: 11/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 64bbc13f8c3df3c0c9a02fee4560c9ee3fcc5d62
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507606"
---
# <a name="runtime-libraries-overview"></a>執行時間程式庫總覽

[.Net 運行](../core/introduction.md#sdk-and-runtimes)時間（安裝在電腦上以供與[framework 相依的應用程式](../core/introduction.md#deployment-models)使用）有一組廣泛的標準類別庫：

* 包含在執行時間中的核心集，也稱為 [基類程式庫 (BCL) ](glossary.md#bcl)。
* 包含在執行時間中的完整集合，也稱為 [運行](glossary.md#runtime) 時間程式庫或 [架構程式庫](glossary.md#framework)。
* NuGet 套件中提供的執行時間程式庫延伸模組。

這些程式庫提供許多一般和應用程式特定類型、演算法和公用程式功能的執行方式。

## <a name="base-class-libraries"></a>基類庫

BCL 提供基礎類型和公用程式功能，而且是所有其他 .NET 類別庫的基底。 例如 <xref:System.String?displayProperty=nameWithType> ，類別可提供用來處理字串的 api。

## <a name="runtime-libraries"></a>執行階段程式庫

也稱為架構程式庫，執行時間程式庫建基於 BCL，以提供公用程式 Api 來進行一般工作。 例如，序列化連結 [庫](serialization/index.md)。

## <a name="extensions-to-the-runtime-libraries"></a>執行時間程式庫的延伸模組

部分執行時間程式庫會在 NuGet 套件中提供，而不是內建至針對與 framework 相依的應用程式所安裝的執行時間。 例如， [.Net 記錄 API](../core/extensions/logging.md)。

## <a name="see-also"></a>另請參閱

* [.NET 簡介](../core/introduction.md)
* [安裝 .NET SDK 或執行時間](../core/install/index.yml)
* [選取要使用的已安裝 .NET SDK 或執行階段版本](../core/versions/selection.md)
* [發佈與 framework 相依的應用程式](../core/deploying/index.md#publish-framework-dependent)
