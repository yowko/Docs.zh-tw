---
title: 運行時和重新置放更改 - .NET 框架
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73196693"
---
# <a name="application-compatibility-in-the-net-framework"></a>.NET 框架中的應用程式相容性

相容性是每個 .NET 版本的一個重要目標。 相容性可確保每個版本都是附加版本，因此以前的版本將繼續工作。 另一方面，對以前功能的更改（例如，為了提高性能、解決安全問題或修復 Bug）可能會導致現有代碼或在更高版本下運行的現有應用程式中出現相容性問題。

每個應用都針對 .NET 框架的特定版本：：

- 在 Visual Studio 中定義目標架構。
- 在專案檔中指定目標架構。
- 將 <xref:System.Runtime.Versioning.TargetFrameworkAttribute> 套用至原始程式碼。

從 .NET 框架的一個版本遷移到另一個版本時，需要考慮兩種類型的更改：

- [運行時更改](#runtime-changes)
- [重新置放更改](#retargeting-changes)

## <a name="runtime-changes"></a>執行階段變更

運行時問題是將新運行時放置在電腦上且應用行為發生更改時出現的問題。 在比目標版本更新的版本中運行時，.NET Framework 使用*古怪的*行為來類比較舊的目標版本。 應用在較新版本上運行，但運行時就像它在舊版本上運行一樣。 .NET Framework 版本間的許多相容性問題是透過這種古怪的模型而降低。 例如，如果為 .NET Framework 4.0 編譯了二進位檔案，但在具有 .NET Framework 4.5 或更高版本的電腦上運行，則該二進位檔案在 .NET Framework 4.0 相容模式下運行。 這意味著更高版本中的許多更改不會影響二進位檔案。

應用程式目標 .NET Framework 的版本由代碼運行的應用程式域的入口程式集的目標版本確定。 在該應用程式域中載入的所有其他程式集都針對該版本。 例如，對於可執行檔，可執行目標的版本是該應用程式域中的所有程式集都運行的相容性模式。

要查看適用于環境的運行時更改清單，請選擇當前定位的 .NET Framework 版本，然後選擇要遷移到的版本：

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a>重定目標變更

重新定向更改是在重新編譯程式集以定位較新版本時發生的更改。 定位較新版本意味著程式集選擇新功能以及舊功能的潛在相容性問題。

要查看適用于環境的重定向更改清單，請選擇當前定位的 .NET Framework 版本，然後選擇要遷移到的版本：

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a>影響分類

在描述運行時和重定向更改的主題中，例如，[從 4.7.2 遷移到 4.8 的重定向更改](retargeting/4.7.2-4.8.md)，各個項按其預期影響進行分類，如下所示：

**主要**\
影響大量應用程式或需要大幅修改程式碼的重大變更。

**小**\
影響少量應用程式或需要稍微修改程式碼的變更。

**邊緣案例**\
在非常特定 (罕見) 的情況下影響應用程式的變更。

**透明**\
此變更對應用程式的開發人員或使用者的影響不明顯。 發生此變更的應用程式應該不需要修改。

## <a name="see-also"></a>另請參閱

- [版本和相依性](versions-and-dependencies.md)
- [新功能](../whats-new/index.md)
- [過時的內容](../whats-new/whats-obsolete.md)
