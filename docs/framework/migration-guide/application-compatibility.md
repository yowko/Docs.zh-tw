---
title: 執行時間和重定變更-.NET Framework
description: 瞭解 .NET Framework 中的應用程式相容性，以及當遷移至另一個版本時，執行時間和重定變更的影響。
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: 26f36dd34c6c5ecae8fc5ab373ff60d9e56f8245
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475485"
---
# <a name="application-compatibility-in-the-net-framework"></a>.NET Framework 中的應用程式相容性

相容性是每個 .NET 版本的重要目標。 相容性可確保每個版本都是附加的，因此舊版會繼續工作。 另一方面，對先前的功能所做的變更（例如，為了改善效能、解決安全性問題或修正錯誤）可能會導致現有程式碼中的相容性問題，或在更新版本下執行的現有應用程式。

每個應用程式都是以特定版本的 .NET Framework 為目標，如下所示：

- 在 Visual Studio 中定義目標架構。
- 在專案檔中指定目標架構。
- 將 <xref:System.Runtime.Versioning.TargetFrameworkAttribute> 套用至原始程式碼。

從 .NET Framework 的某個版本遷移至另一個版本時，需要考慮兩種類型的變更：

- [執行階段變更](#runtime-changes)
- [重定目標變更](#retargeting-changes)

## <a name="runtime-changes"></a>執行階段變更

執行時間問題是在電腦上放置新的執行時間，以及應用程式的行為變更時所發生的問題。 當在比目標較新的版本上執行時，.NET Framework 會使用*quirked*行為來模擬較舊的目標版本。 應用程式會在較新的版本上執行，但會如同在較舊的版本上執行一樣。 .NET Framework 版本間的許多相容性問題是透過這種古怪的模型而降低。 例如，如果二進位檔是針對 .NET Framework 4.0 編譯，但在具有 .NET Framework 4.5 或更新版本的電腦上執行，則會在 .NET Framework 4.0 相容性模式下執行。 這表示，較新版本中的許多變更不會影響二進位檔。

應用程式目標的 .NET Framework 版本是由程式碼執行所在之應用程式域的專案元件目標版本所決定。 載入該應用程式域中的所有其他元件都會以該版本為目標。 例如，如果是可執行檔，則可執行檔目標的版本是該應用程式域中的所有元件在其下執行的相容性模式。

若要查看適用于您環境的執行時間變更清單，請選取您目前設為目標的 .NET Framework 版本，然後選擇您想要遷移到的版本：

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a>重定目標變更

重定變更是元件重新編譯成以較新版本為目標時所發生的變更。 以較新的版本為目標，表示元件會加入宣告新功能，以及舊功能的潛在相容性問題。

若要查看適用于您環境的重定變更清單，請選取您目前設為目標的 .NET Framework 版本，然後選擇您想要遷移到的版本：

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a>影響分類

在描述執行時間和重定變更的主題中（例如，[重定從4.7.2 遷移到4.8 的變更](retargeting/4.7.2-4.8.md)），個別專案會依其預期的影響分類，如下所示：

**巨大**\
影響大量應用程式或需要大幅修改程式碼的重大變更。

**刻度**\
影響少量應用程式或需要稍微修改程式碼的變更。

**邊緣案例**\
在非常特定 (罕見) 的情況下影響應用程式的變更。

**變成**\
此變更對應用程式的開發人員或使用者的影響不明顯。 發生此變更的應用程式應該不需要修改。

## <a name="see-also"></a>另請參閱

- [版本和相依性](versions-and-dependencies.md)
- [新功能](../whats-new/index.md)
- [過時功能](../whats-new/whats-obsolete.md)
