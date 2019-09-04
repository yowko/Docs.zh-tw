---
title: 附屬元件載入演算法-.NET Core
description: 描述 .NET Core 中附屬元件載入演算法的詳細資料
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70234624"
---
# <a name="satellite-assembly-loading-algorithm"></a>附屬元件載入演算法

附屬元件是用來儲存針對語言和文化特性自訂的當地語系化資源。

附屬元件會使用與一般 managed 元件不同的載入演算法。

## <a name="when-are-satellite-assemblies-loaded"></a>何時會載入附屬元件？

載入當地語系化資源時, 會載入附屬元件。

用來載入當地語系化資源的基本 API 是<xref:System.Resources.ResourceManager?displayProperty=fullName>類別。 最後, <xref:System.Resources.ResourceManager>類別會針對每<xref:System.Reflection.Assembly.GetSatelliteAssembly%2A>個<xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>呼叫方法。

較高層級的 Api 可能會抽象化低層級 API。

## <a name="algorithm"></a>演算法

.NET Core 資源後援處理序包含下列步驟：

1. `active` 判斷<xref:System.Runtime.Loader.AssemblyLoadContext>實例。 在所有情況下, `active`實例都是執行元件的<xref:System.Runtime.Loader.AssemblyLoadContext>。

2. `active`實例會嘗試載入所要求文化特性的附屬元件 (依優先順序排列):
    - 正在檢查其快取。
    - 檢查目前執行中元件的目錄中是否有符合要求<xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>的子目錄 ( `es-MX`例如)。

        > [!NOTE]
        > 在3.0 之前, 不會在 .NET Core 中實作為這項功能。
        >
        > [!NOTE]
        > 在 Linux 和 macOS 上, 子目錄會區分大小寫, 而且必須是:
        > - 完全相符的大小寫。
        > - 以小寫。

    - `active` 如果<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>是實例, 則執行預設的[附屬 (資源) 元件探查](default-probing.md#satellite-resource-assembly-probing)邏輯。

    - <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>呼叫函式。

    - <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType>引發事件。

    - <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>引發事件。

3. 如果載入附屬元件:
   - 便會引發 <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> 事件。
   - 元件會在其中搜尋所要求的資源。 如果執行時間在元件中找到資源, 則會使用它。 如果找不到資源，會繼續搜尋。

    > [!NOTE]
    > 為了在附屬組件內尋找資源，執行階段會搜尋目前 <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> 的 <xref:System.Resources.ResourceManager> 所要求的資源檔。 在資源檔中, 它會搜尋所要求的資源名稱。 如果找不到任一個，就會將資源視為找不到。

4. 執行時間接著會透過許多可能的層級來搜尋父文化特性元件, 每次重複步驟 2 & 3。

    每個文化<xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType>特性都只有一個父系, 這是由屬性所定義。

    當文化特性的<xref:System.Globalization.CultureInfo.Parent%2A>屬性為時, 會<xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>停止搜尋父文化特性。

    在<xref:System.Globalization.CultureInfo.InvariantCulture>中, 我們不會回到步驟 2 & 3, 而是繼續執行步驟5。

5. 如果仍找不到資源, 則會使用預設 (fallback) 文化特性的資源。

   通常，主要應用程式組件中會包含預設文化特性的資源。 不過, 您可以<xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType>為屬性指定。 此值表示資源的最終回退位置是附屬元件, 而不是主要元件。

    > [!NOTE]
    > 預設的文化特性是最終的回溯。 因此, 我們建議您一律在預設資源檔中包含一組完整的資源。 這樣有助於防止擲回例外狀況。 藉由全面設定, 您可以提供所有資源的回復, 並確保使用者一律至少有一個資源, 即使它不是特定文化特性。

6. 一點
   - 如果執行時間找不到預設 (fallback) 文化特性的資源檔, <xref:System.Resources.MissingManifestResourceException>則會擲回或<xref:System.Resources.MissingSatelliteAssemblyException>例外狀況。
   - 如果找到資源檔, 但要求的資源不存在, 則要求`null`會傳回。
