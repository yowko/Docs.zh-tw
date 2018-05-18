---
title: .NET Core 支援
description: 了解適用於 .NET Core 的不同版本序列的支援 (LTS 和目前)
author: kendrahavens
ms.author: mairaw
ms.date: 01/30/2017
ms.openlocfilehash: b61aa48451cee60be4968c151b97746a3aef85c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-support"></a>.NET Core 支援

這是 .NET Core 支援的一般說明。

## <a name="lts-and-current-release-trains"></a>LTS 和目前的 Release Train

支援兩個 Release Train 是整個軟體界常用的概念，特別是像 .NET Core 這類開放原始碼專案。 .NET Core 支援下列版本序列︰[長期支援 (LTS) (英文)](https://en.wikipedia.org/wiki/Long-term_support) 和目前。 LTS 版本會受到維護，以在其週期內提供穩定性，可接收重要問題的修正和安全性問題修正。 目前版本中會有新的功能工作和其他 Bug 修正。 從支援的觀點來看，這些 Release Train 具有下列支援週期屬性。

LTS 版本
* 可於 LTS 版本全面上市後，提供為期三年的支援
* 或可於後續的 LTS 版本全面上市後，提供為期一年的支援

目前版本
* 和父代 LTS 版本一樣，同樣提供為期三年的支援
* 可於後續的目前版本全面上市後，提供為期三個月的支援
* 並可於後續的 LTS 版本全面上市後，提供為期一年的支援

## <a name="versioning"></a>版本控制
利用增加的主要版本號碼來標示新的 LTS 版本。 目前版本的主要版本號碼會和對應的 LTS Train 相同，並會利用增加的主要版本號碼來標示版本。 例如，1.0.3 為 LTS 版本，而 1.1.0 則為目前版本。 對任一 Train 更新 Bug 修正，會讓修補檔案版本遞增。 如需版本控制配置的詳細資訊，請參閱 [.NET Core 版本控制](index.md)。

## <a name="what-causes-updates-in-lts-and-current-trains"></a>在 LTS 和目前的 Train 中造成更新的原因為何？
若要了解哪些特定變更，例如 Bug 修正或加入 API，會導致更新版本號碼，請檢閱[版本控制說明文件](index.md)中的「決策樹」一節。 要決定將哪些變更從目前版本提取到 LTS 分支中，並沒有黃金規則。 一般而言，可修正預期行為的必要安全性問題更新與修補檔案，都會造成更新 LTS 分支。 雖然這不一定可行，但我們也想要支援 LTS 分支上最近的桌面開發人員作業系統。 想要掌握特定版本中支援哪些 API、修正及作業系統，最好瀏覽其在 GitHub 上的[版本資訊](https://github.com/dotnet/core/tree/master/release-notes)。

### <a name="further-reading"></a>進一步閱讀
* [.NET Core 支援週期資料表](https://www.microsoft.com/net/core/support)
* [目前支援的作業系統和版本](https://github.com/dotnet/core/blob/master/roadmap.md)
