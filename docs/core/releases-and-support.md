---
title: .NET 版本、修補程式和支援
description: 深入瞭解 .NET 5 (的版本、修補程式及支援，包括 .NET Core) 和更新版本。
ms.date: 10/07/2020
ms.topic: overview
ms.author: tdykstra
author: tdykstra
ms.openlocfilehash: 896b88cbf1f7f31d2d26d69ec7d219da6b27ceff
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982290"
---
# <a name="releases-and-support-for-net-core-and-net-5"></a>.NET Core 和 .NET 5 的版本和支援

Microsoft 針對 .NET 5.0 (和 .NET Core) 和更新版本推出了 (修補程式) 的主要版本、次要版本和服務更新。 本文說明發行類型、服務更新、SDK 功能區選、支援期間和支援選項。

## <a name="release-types"></a>版本類型

每個版本的類型相關資訊會以 *主要. 次要 patch* 格式的版本號碼編碼。

例如：

* .NET Core 3.0 和 NET 5.0 是主要版本。
* .NET Core 3.1 是 .NET Core 3.0 主要版本之後的第一個次要版本。
* .NET Core 3.1.7 是 .NET Core 3.1 的第七個修補程式。

### <a name="major-releases"></a>主要版本

主要版本包括新功能、新的公用 API 介面區和 bug 修正。 範例包括 .NET Core 3.0 和 .NET 5.0。  由於變更的本質，這些版本預期會有重大變更。 主要版本會與先前的主要版本並存安裝。

### <a name="minor-releases"></a>次要版本

次要版本也包含新功能、公用 API 介面區和 bug 修正，而且可能也有重大變更。 範例包括 .NET Core 2.1 和 .NET Core 3.1。 這兩個主要版本之間的差異在於變更的大小變小。 從 .NET Core 3.0 升級到3.1 的應用程式有較小的跳躍，可繼續進行。 次要版本會與先前的次要版本並存安裝。

### <a name="servicing-updates"></a>服務更新

服務更新 (修補程式) 幾乎每個月都會送出，而這些更新同時包含安全性和非安全性錯誤修正。 例如，.NET Core 3.1.8 是 .NET Core 3.1 的第八個更新。 當這些更新包含安全性修正時，就會在「星期二修補」上發行，這一律是當月的第二個星期二。 服務更新應維持相容性。 從 .NET Core 3.1 開始，服務更新會升級以移除先前的更新。 例如，3.1 的最新服務更新會在安裝成功後移除先前的3.1 更新。

### <a name="feature-bands-sdk-only"></a>僅)  (SDK 功能區

.NET SDK 的版本控制與 .NET 執行時間的運作方式稍有不同。 為了與新的 Visual Studio 版本保持一致，.NET SDK 更新有時會包含新功能或新版本的元件（例如 MSBuild 和 NuGet）。 這些新功能或元件可能與舊版 SDK 更新中針對相同主要或次要版本所提供的版本不相容。

為了區分這類更新，.NET SDK 會使用功能帶的概念。 例如，第一個 .NET Core 3.1 SDK 是3.1.100。 此版本對應于 3.1.1 xx  *功能區*。 功能群組是在版本號碼第三個區段中的數百個群組中定義。 例如，3.1.101 和3.1.201 是兩個不同的功能區中的版本，而3.1.101 和3.1.199 位於相同的功能區中。 安裝 .NET Core SDK 3.1.101 時，會從電腦移除 .NET Core SDK 3.1.100 （如果有的話）。 當 .NET Core SDK 3.1.200 安裝在同一部電腦上時，不會移除 .NET Core SDK 3.1.101。

### <a name="runtime-roll-forward-and-compatibility"></a>執行時間向前復原和相容性

主要和次要更新會與先前的版本並存安裝。 針對特定主要版本所建立的應用程式 *。次要* 版本會繼續使用該目標執行時間，即使已安裝較新的版本也一樣。 除非您加入宣告此行為，否則應用程式不會自動向前復原為使用較新的 *主要版本。* 以 .NET Core 3.0 為目標所建立的應用程式不會在 .NET Core 3.1 上自動開始執行。 建議您先重建應用程式，並針對較新的主要或次要執行階段版本進行測試，再部署至生產環境。 如需詳細資訊，請參閱與 [Framework 相依的應用程式](versions/selection.md#framework-dependent-apps-roll-forward) 向前復原和獨立式 [部署執行時間向前](deploying/runtime-patch-selection.md)復原。

服務更新的處理方式與主要和次要版本不同。 根據預設，針對 .NET Core 3.1 所建立的應用程式會在3.1.0 執行時間上執行。 當安裝服務更新時，它會自動向前復原以使用較新的3.1.1 執行時間。 這是預設行為，因為我們希望安全性修正程式在安裝時立即使用，而不需要執行任何其他動作。 您可以退出宣告此預設向前復原行為。

## <a name="net-core-and-net-5-version-lifecycles"></a>.NET Core 和 .NET 5 版本生命週期

.NET Core、.NET 5 和更新版本採用 [新式生命週期](/lifecycle/policies/modern) ，而不是已用於 .NET Framework 版本的 [固定生命週期](/lifecycle/policies/fixed) 。 具有固定生命週期的產品提供長期的支援，例如5年的主流支援，以及另五年的延伸支援。 主流支援包括安全性和非安全性的修正程式，而延伸支援只提供安全性修正。 採用新式生命週期的產品有更多類似服務的支援模型，並提供較短的支援週期和更頻繁的版本。

### <a name="release-tracks"></a>版本追蹤

有兩個版本支援追蹤：

* *目前* 的版本

  在下一個主要或次要版本發行之後的3個月內，才支援這些版本。

  範例：

  * .NET Core 3.0 隨附于2019年9月，並在12月2019的 .NET Core 3.1 之後推出。
  * .NET Core 3.0 支援已于年3月2020日結束後的3個月3.1 後結束。

* *長期支援* (LTS) 版本

  這些版本的支援最少3年，或在下一個 LTS 發行之後的1年之後，如果該日期之後才會發行。

  範例：

  * .NET Core 2.1 于5月2018日發行，並被視為8月2018的 LTS 版本。
  * .NET Core 3.1 是下一個 LTS 版本，在2019年12月發行。
  * 因為2021年8月 (3 年 2021 2.1) 3.1 的) 晚于2020年12月的 (一年。

釋放 LTS 和 Current 之間的替代版本，因此可能會比較新版本支援較舊版本。 例如，.NET Core 2.1 是 LTS 版本，可支援至2021年8月。 3.0 版已于稍後寄出超過一年，但在12月2019日之前已不再支援。

服務更新會每月寄送，同時包含安全性和非安全性 (可靠性、相容性和穩定性) 修正。 在下一個服務更新發行之前，支援服務更新。 服務更新有執行時間向前復原行為。 這表示應用程式預設會在最新安裝的執行時間服務更新上執行。

## <a name="how-to-choose-a-release"></a>如何選擇發行

如果您正在建立服務，並預期繼續定期進行更新，則目前的版本（例如 .NET 5.0）可能是您最新的選項，可讓您隨時掌握 .NET 提供的最新功能。

如果您要建立將散發給取用者的用戶端應用程式，穩定性可能會比存取最新功能更重要。 您的應用程式可能必須在一段時間內受到支援，取用者才能升級到下一版的應用程式。 在此情況下，LTS 版本（例如 .NET Core 3.1）可能是正確的選項。

### <a name="servicing-updates"></a>服務更新

在下一個服務更新發行之前，支援 .NET 服務更新。 每月的發行步調。

您必須定期安裝服務更新，以確保您的應用程式處於安全且受支援的狀態。 例如，如果 .NET Core 3.1 的最新服務更新是3.1.8，而我們已寄出3.1.9，則3.1.8 不再是最新的。 然後會 3.1.9 3.1 支援的服務等級。

如需每個主要和次要版本的最新服務更新的詳細資訊，請參閱 [.net 下載頁面](https://dotnet.microsoft.com/download/dotnet-core)。

## <a name="end-of-support"></a>結束支援

結束支援是指 Microsoft 不再提供產品版本的修正、更新或技術協助所需的日期。 在此日期之前，請確定您已移至使用支援的版本。 不受支援的版本不會再收到可保護您的應用程式和資料的安全性更新。

## <a name="supported-operating-systems"></a>支援的作業系統

.NET 5 (和 .NET Core) 和更新版本可在各種作業系統上執行。 每個作業系統都有其贊助商組織所定義的生命週期 (例如 Microsoft、Red Hat 或 Apple) 。 新增和移除作業系統版本的支援時，我們會將這些生命週期排程列入考慮。

當作業系統版本不支援時，我們會停止測試該版本，並提供該版本的支援。 使用者必須繼續使用支援的作業系統版本，才能取得支援。

如需詳細資訊，請參閱 [.NET 作業系統生命週期原則](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)。

## <a name="get-support"></a>取得支援

您可以選擇 Microsoft 協助支援和社區支援。

### <a name="microsoft-support"></a>Microsoft 支援服務

如需協助支援，請 [聯絡 Microsoft 支援服務專業人員](https://support.microsoft.com/supportforbusiness/productselection/?sapid=4fd4947b-15ea-ce01-080f-97f2ca3c76e8)。

您必須在支援的服務層級 (最新的可用服務更新) 才有資格支援。 如果系統執行的是3.1，且3.1.8 服務更新已發行，則必須先將3.1.8 安裝為第一個步驟。

### <a name="community-support"></a>社群支援

如需支援的社區，請參閱 [ [社區] 頁面](https://dotnet.microsoft.com/platform/community)。

## <a name="see-also"></a>另請參閱

如需詳細資訊，包括每個 .NET Core 版本和 .NET 5 版本支援的日期範圍，請參閱 [支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。
