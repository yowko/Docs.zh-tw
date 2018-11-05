---
title: 開始建立高品質的 .NET 程式庫
description: 開始建置 .NET 程式庫。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 6377e3fe606bf7603b418decdd0e3f9d2de6a510
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201239"
---
# <a name="get-started"></a>開始使用

## <a name="cross-platform-targetingcross-platform-targetingmd"></a>[跨平台目標](./cross-platform-targeting.md)

如何使用 .NET Standard 與多目標設定來建立跨平台程式庫。 .NET 可在許多地方執行，而 .NET 程式庫所支援的平台與開發人員應該越多越好。

## <a name="strong-namingstrong-namingmd"></a>[強式命名](./strong-naming.md)

了解強式命名與其優缺點。 為 .NET 程式庫提供強式命名可讓大部分的開發人員使用它，這也是建議的最佳做法。

## <a name="nuget-and-open-source-librariesnugetmd"></a>[NuGet 與開放原始碼程式庫](./nuget.md)

針對開放原始碼 .NET 程式庫建立 NuGet 套件的最佳方式，包括適用於在 NuGet.org 上公開發佈之所有套件的建議中繼資料。

### <a name="dependenciesdependenciesmd"></a>[相依性](./dependencies.md)

NuGet 可讓您在建置 .NET 程式庫時輕鬆使用現有的套件。 了解 NuGet 相依性的常見摩擦原因，以及避免它們的方法。

### <a name="sourcelinksourcelinkmd"></a>[SourceLink](./sourcelink.md)

SourceLink 是可讓您 .NET 程式庫的使用者在偵錯期間逐步執行其原始程式碼的絕佳工具。 此文章會提供 SourceLink 的概觀，以及您應該使用它的原因。

### <a name="publishingpublish-nuget-packagemd"></a>[發佈](./publish-nuget-package.md)

雖然 NuGet.org 是最廣為人知且最常被使用的存放庫，還有許多其他可以發佈 NuGet 套件的地方。 了解各種可供使用的 NuGet 套件存放庫，以及發佈 .NET 存放庫的安全性最佳做法。

## <a name="versioningversioningmd"></a>[版本控制](./versioning.md)

良好的 .NET 程式庫會隨著時間演進，並會在後續版本中新增功能、修正錯誤 (Bug) 並改善效能。 了解各種版本號碼，以及如何與開發人員溝通中斷性變更。

### <a name="breaking-changesbreaking-changesmd"></a>[重大變更](./breaking-changes.md)

.NET 程式庫必須在針對現有使用者提供穩定性，以及針對未來取得創新之間取得平衡。 了解各種類型的中斷性變更，以及在維持回溯相容性的同時新增功能的策略。

>[!div class="step-by-step"]
[上一頁](./index.md)
[下一頁](./cross-platform-targeting.md)
