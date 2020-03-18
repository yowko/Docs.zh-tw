---
title: 衛星程式集載入演算法 - .NET 核心
description: .NET Core 中衛星程式集載入演算法的詳細資訊說明
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "70234624"
---
# <a name="satellite-assembly-loading-algorithm"></a>衛星程式集載入演算法

附屬程式集用於存儲為語言和文化定制的當地語系化資源。

附屬程式集使用的載入演算法與常規託管程式集不同。

## <a name="when-are-satellite-assemblies-loaded"></a>何時載入附屬程式集？

載入當地語系化資源時載入附屬程式集。

載入當地語系化資源的基本 API 是類<xref:System.Resources.ResourceManager?displayProperty=fullName>。 最終，<xref:System.Resources.ResourceManager>類將為每個<xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType><xref:System.Reflection.Assembly.GetSatelliteAssembly%2A>調用 方法。

更高級別 API 可能會抽象低級 API。

## <a name="algorithm"></a>演算法

.NET Core 資源後援處理序包含下列步驟：

1. 確定`active`<xref:System.Runtime.Loader.AssemblyLoadContext>實例。 在所有情況下，`active`實例都是執行程式集的<xref:System.Runtime.Loader.AssemblyLoadContext>。

2. 實例`active`嘗試按優先順序順序載入請求的區域性的附屬程式集，其順序包括：
    - 檢查其緩存。
    - 檢查當前正在執行程式集的目錄，以執行與請求<xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>匹配的子目錄（例如`es-MX`）。

        > [!NOTE]
        > 此功能在 3.0 之前未在 .NET Core 中實現。
        >
        > [!NOTE]
        > 在 Linux 和 macOS 上，子目錄區分大小寫，必須：
        > - 完全符合的情況下。
        > - 處於小寫字母中。

    - 如果是`active`實例，<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>則通過運行[預設的衛星（資源）程式集探測](default-probing.md#satellite-resource-assembly-probing)邏輯。

    - 調用函數<xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>。

    - 引發事件<xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType>。

    - 引發事件<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>。

3. 如果載入了附屬程式集：
   - 便會引發 <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> 事件。
   - 將程式集搜索為請求的資源。 如果運行時在程式集中找到資源，則使用它。 如果找不到資源，會繼續搜尋。

    > [!NOTE]
    > 為了在附屬組件內尋找資源，執行階段會搜尋目前 <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> 的 <xref:System.Resources.ResourceManager> 所要求的資源檔。 在資源檔中，它搜索請求的資源名稱。 如果找不到任一個，就會將資源視為找不到。

4. 接下來運行時通過許多潛在級別搜索父區域性程式集，每次重複步驟 2 & 3。

    每個區域性只有一個父級，由<xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType>屬性定義。

    當區域性的屬性為<xref:System.Globalization.CultureInfo.Parent%2A><xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>時，對父區域性的搜索將停止。

    對於<xref:System.Globalization.CultureInfo.InvariantCulture>，我們不會返回到步驟 2 & 3，而是繼續步驟 5。

5. 如果仍未找到資源，則使用預設（回退）區域性的資源。

   通常，主要應用程式組件中會包含預設文化特性的資源。 但是，您可以為<xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType><xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType>屬性指定。 此值表示資源的最終回退位置是附屬程式集，而不是主程式集。

    > [!NOTE]
    > 預設區域性是最終的回退。 因此，我們建議您始終在預設資源檔中包含一組詳盡的資源。 這樣有助於防止擲回例外狀況。 通過擁有詳盡集，您可以為所有資源提供回退，並確保使用者始終存在至少一個資源，即使它不是特定于區域性的資源。

6. 最後
   - 如果運行時找不到預設（回退）區域性的資源檔，則引發 或<xref:System.Resources.MissingManifestResourceException><xref:System.Resources.MissingSatelliteAssemblyException>異常。
   - 如果找到資源檔但請求的資源不存在，則請求將返回`null`。
