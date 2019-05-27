---
title: .NET Framework 的版本相容性
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8db23f8e670406faff01644e751a948096f5fc7c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592888"
---
# <a name="version-compatibility-in-the-net-framework"></a>.NET Framework 的版本相容性

回溯相容性表示針對特定平台版本開發的應用程式將會在該平台的較新版本上執行。 .NET Framework 嘗試最大化回溯相容性：針對某一個 .NET Framework 版本撰寫的原始程式碼應該在較新版本的 .NET Framework 上編譯，且在某一個 .NET Framework 版本上執行的二進位檔行為應該與較新版本 .NET Framework 相同。

## <a name="Apps"></a> 應用程式的版本相容性

根據預設，應用程式會在其建置所針對的 .NET Framework 版本上執行。 如果該版本不存在，且應用程式組態檔不會定義支援的版本，則可能會發生 .NET Framework 初始化錯誤。 在此例中，嘗試執行應用程式的作業將會失敗。

若要定義應用程式執行所在的特定版本，請將一個或多個 [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) 項目新增至應用程式的組態檔。 每一個 `<supportedRuntime>` 項目都會列出支援的執行階段版本，最先指定的是最優先的版本，而最後指定的則是優先順序最低的版本。

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

如需詳細資訊，請參閱[如何：設定應用程式以支援 .NET Framework 4 或 4.x](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)。

## <a name="version-compatibility-for-components"></a>元件的版本相容性

應用程式可以控制其執行的 .NET Framework 版本，元件則不能。 元件和類別庫會載入至特定應用程式的內容中，這就是為什麼它們會自動執行應用程式所執行的 .NET Framework 版本。

由於這項限制，所以相容性保證對於元件特別重要。 從 .NET Framework 4 開始，您可以指定元件在多個版本中維持相容所需的程度，方法是將 <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> 屬性套用至該元件。 工具可以使用這個屬性來偵測將來的元件版本中，是否有可能違反相容性保證的狀況。

## <a name="backward-compatibility-and-the-net-framework"></a>回溯相容性和 .NET Framework

.NET Framework 4.5 和更新版本可以與使用舊版 .NET Framework 所建置的應用程式回溯相容。 換句話說，使用舊版所建置的應用程式和元件不需經過修改，就可在 .NET Framework 4.5 和更新版本上運作。 不過，應用程式預設會在作為其開發目標的通用語言執行平台版本上執行，因此您可能需要提供組態檔，才能讓您的應用程式在 .NET Framework 4.5 或更新版本上執行。 如需詳細資訊，請參閱本文前面的[應用程式的版本相容性](#Apps)一節。

在實際操作中，.NET Framework 中似乎前後不一致的變更以及程式設計技術的變更可能會破壞此相容性。 例如，.NET Framework 4.5 中的效能改良可能會暴露在舊版不會發生的競爭情況。 同樣地，使用 .NET Framework 組件的硬式編碼路徑、搭配特定版本的 .NET Framework 執行相等比較以及使用反映來取得私用欄位的值，都不是具有回溯相容性的作法。 此外，每一個 .NET Framework 版本都包含可能會影響某些應用程式與元件之相容性的 Bug 修正和安全性相關的變更。

如果您的應用程式或元件在 .NET Framework 4.5 (包括其點版本，.NET Framework 4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 或 4.8) 上無法如預期運作，請使用下列檢查清單：

- 如果您應用程式的開發目的是在開頭為 .NET Framework 4.0 之任何版本的 .NET Framework 上執行，請參閱 [.NET Framework 中的應用程式相容性](application-compatibility.md)，以產生目標 .NET Framework 版本與您應用程式所執行版本之間的變更清單。

- 如果您有 .NET Framework 3.5 應用程式，另請參閱 [.NET Framework 4 移轉問題](../migration-guide/net-framework-4-migration-issues.md)。

- 如果您有 .NET Framework 2.0 應用程式，另請參閱 [.NET Framework 3.5 SP1 中的變更](https://go.microsoft.com/fwlink/?LinkId=186989)。

- 如果您有 .NET Framework 1.1 應用程式，另請參閱 [.NET Framework 2.0 中的變更](https://go.microsoft.com/fwlink/?LinkID=125263)。

- 如果您正在重新編譯現有原始程式碼以便在 .NET Framework 4.5 或其點版本執行，或如果您正在開發的新版本應用程式或元件針對 .NET Framework 4.5，或針對來自其現有原始程式碼基底的點版本，請檢查 [.NET Framework 類別庫中已淘汰的功能](../whats-new/whats-obsolete.md)中已淘汰類型和成員，並套用所述的因應措施。 (之前編譯的程式碼將會針對已標示為過時的型別和成員繼續執行)。

- 如果您認為 .NET Framework 4.5 中的變更已破壞您的應用程式，請檢查[執行階段設定結構描述](../configure-apps/file-schema/runtime/index.md)，特別是 [\<Appcontextswitchoverrides > 項目](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，以判斷您是否可以在您的應用程式組態檔中使用執行階段設定來還原先前行為。

- 如果您遇到未記載的問題，請在 [.NET 開發人員社群網站](https://developercommunity.visualstudio.com/spaces/61/index.html)或 [Microsoft/dotnet GitHub 存放庫](https://github.com/microsoft/dotnet/issues)中開啟問題。

## <a name="compatibility-and-side-by-side-execution"></a>相容性和並存執行

如果您找不到適當的因應措施來解決問題，請記得 .NET Framework 4.5 (或其點版本其中之一) 與版本 1.1、2.0 和 3.5 並存執行，且是取代第 4 版的就地更新。 若是以 1.1、2.0 和 3.5 版為目標的應用程式，您可以在目標電腦上安裝適當的 .NET Framework 版本，以便在最佳環境中執行應用程式。 如需並存執行的詳細資訊，請參閱[並存執行](../deployment/side-by-side-execution.md)。

## <a name="see-also"></a>另請參閱

- [新功能](../whats-new/index.md)
- [類別庫中已淘汰的功能](../whats-new/whats-obsolete.md)
- [應用程式相容性](../migration-guide/application-compatibility.md)
- [Microsoft .NET Framework 支援週期原則](https://go.microsoft.com/fwlink/p/?LinkId=248212)
- [.NET Framework 4 移轉問題](../migration-guide/net-framework-4-migration-issues.md)
