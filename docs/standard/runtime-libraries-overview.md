---
title: 執行時間程式庫總覽
description: 瞭解 [內容] 的 [執行時間程式庫] 區段中包含的內容。
author: tdykstra
ms.date: 11/12/2020
ms.openlocfilehash: 5a8f888e1778553e2968277738cfef5134f11589
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687891"
---
# <a name="runtime-libraries-overview"></a>執行時間程式庫總覽

[.Net 運行](../core/introduction.md#sdk-and-runtimes)時間（安裝在電腦上以供與[framework 相依的應用程式](../core/introduction.md#deployment-models)使用）有一組廣泛的標準類別庫，也稱為[運行](glossary.md#runtime)時間程式庫、[架構程式庫](glossary.md#framework-libraries)，或[ (BCL) 的基類庫](glossary.md#bcl)。 此外，NuGet 套件中提供執行時間程式庫的擴充功能。

這些程式庫提供許多一般和應用程式特定類型、演算法和公用程式功能的執行方式。

## <a name="runtime-libraries"></a>執行階段程式庫

這些程式庫提供基礎類型和公用程式功能，而且是所有其他 .NET 類別庫的基底。 例如 <xref:System.String?displayProperty=nameWithType> ，類別可提供用來處理字串的 api。 另一個範例是 [序列化程式庫](serialization/index.md)。

## <a name="extensions-to-the-runtime-libraries"></a>執行時間程式庫的延伸模組

某些程式庫是在 NuGet 套件中提供，而不是包含在執行時間的 [共用架構](glossary.md#shared-framework)中。 例如：

* [Logging](../core/extensions/logging.md)
* [相依性插入](../core/extensions/dependency-injection.md)
* [設定](../core/extensions/configuration.md)

## <a name="see-also"></a>另請參閱

* [.NET 簡介](../core/introduction.md)
* [安裝 .NET SDK 或執行時間](../core/install/index.yml)
* [選取要使用的已安裝 .NET SDK 或執行階段版本](../core/versions/selection.md)
* [發佈與 framework 相依的應用程式](../core/deploying/index.md#publish-framework-dependent)
