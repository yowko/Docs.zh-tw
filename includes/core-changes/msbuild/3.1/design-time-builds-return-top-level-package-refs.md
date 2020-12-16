---
ms.openlocfilehash: 53840ddd59ae3463bae2930fd0151ab2cd2d65cb
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593317"
---
### <a name="design-time-builds-only-return-top-level-package-references"></a>設計階段組建只會傳回最上層的封裝參考

從 .NET Core SDK 3.1.400 開始，目標只會傳回最上層的封裝參考 `RunResolvePackageDependencies` 。

#### <a name="version-introduced"></a>引進的版本

.NET Core SDK 3.1.400

#### <a name="change-description"></a>變更描述

在舊版的 .NET Core SDK 中， `RunResolvePackageDependencies` 目標會建立下列 MSBuild 專案，其中包含 NuGet 資產檔案中的資訊：

- `PackageDefinitions`
- `PackageDependencies`
- `TargetDefinitions`
- `FileDefinitions`
- `FileDependencies`

Visual Studio 會使用這項資料來填入方案總管中的相依性節點。 不過，它可以是大量資料，除非展開相依性節點，否則不需要資料。

從 .NET Core SDK 版本3.1.400 開始，預設不會產生大部分的專案。 只會傳回型別的專案 `Package` 。 如果 Visual Studio 需要專案來填入相依性節點，它會直接從資產檔案讀取資訊。

#### <a name="reason-for-change"></a>變更的原因

這項變更是為了改善 Visual Studio 內的解決方案載入效能而引進的。 先前會載入所有的封裝參考，其中牽涉到載入大部分使用者永遠不會看到的許多參考。

#### <a name="recommended-action"></a>建議的動作

如果您的 MSBuild 邏輯相依于這些建立的專案，請 `EmitLegacyAssetsFileItems` 在您的專案檔中將屬性設為 `true` 。 這項設定會啟用先前的行為，其中會建立所有專案。

#### <a name="category"></a>類別

MSBuild

#### <a name="affected-apis"></a>受影響的 API

N/A
