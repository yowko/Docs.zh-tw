---
title: .NET Framework 中的版本相容性
description: 瞭解 .NET Framework 版本之間的相容性，包括回溯相容性和並存執行。
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
ms.openlocfilehash: 2be9c4e12d6a613e7f1062ec7492b0b99203f39d
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400692"
---
# <a name="version-compatibility"></a>版本相容性

回溯相容性表示針對特定平台版本開發的應用程式將會在該平台的較新版本上執行。 .NET Framework 嘗試最大化回溯相容性：針對某一個版本的 .NET Framework 所撰寫的原始程式碼應該在較新版本的 .NET Framework 上編譯，而在某個 .NET Framework 版本上執行的二進位檔在較新版本的 .NET Framework 上應會有相同的行為。

## <a name="version-compatibility-for-apps"></a><a name="Apps"></a> 應用程式的版本相容性

根據預設，應用程式會在其所建立的 .NET Framework 版本上執行。 如果該版本不存在，且應用程式組態檔不會定義支援的版本，則可能會發生 .NET Framework 初始化錯誤。 在此例中，嘗試執行應用程式的作業將會失敗。

若要定義應用程式執行所在的特定版本，請將一或多個專案新增 [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) 至您的應用程式佈建檔。 每一個 `<supportedRuntime>` 項目都會列出支援的執行階段版本，最先指定的是最優先的版本，而最後指定的則是優先順序最低的版本。

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

如需詳細資訊，請參閱[如何：設定應用程式以支援 .NET Framework 4 或 4.x](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)。

## <a name="version-compatibility-for-components"></a>元件的版本相容性

應用程式可以控制其執行的 .NET Framework 版本，元件則不能。 元件和類別庫會載入至特定應用程式的內容中，這就是為什麼它們會自動執行應用程式所執行的 .NET Framework 版本。

由於這項限制，所以相容性保證對於元件特別重要。 從 .NET Framework 4 開始，您可以指定元件在多個版本中維持相容所需的程度，方法是將 <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> 屬性套用至該元件。 工具可以使用這個屬性來偵測將來的元件版本中，是否有可能違反相容性保證的狀況。

## <a name="backward-compatibility"></a>回溯相容性

.NET Framework 4.5 和更新版本可以與使用舊版 .NET Framework 所建置的應用程式回溯相容。 換句話說，使用舊版所建置的應用程式和元件不需經過修改，就可在 .NET Framework 4.5 和更新版本上運作。 不過，應用程式預設會在作為其開發目標的通用語言執行平台版本上執行，因此您可能需要提供組態檔，才能讓您的應用程式在 .NET Framework 4.5 或更新版本上執行。 如需詳細資訊，請參閱本文前面的[應用程式的版本相容性](#Apps)一節。

在實際操作中，.NET Framework 中似乎前後不一致的變更以及程式設計技術的變更可能會破壞此相容性。 例如，.NET Framework 4.5 中的效能改良可能會暴露在舊版不會發生的競爭情況。 同樣地，使用 .NET Framework 組件的硬式編碼路徑、搭配特定版本的 .NET Framework 執行相等比較以及使用反映來取得私用欄位的值，都不是具有回溯相容性的作法。 此外，每一個 .NET Framework 版本都包含可能會影響某些應用程式與元件之相容性的 Bug 修正和安全性相關的變更。

如果您的應用程式或元件在 .NET Framework 4.5 (包括其點版本，.NET Framework 4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 或 4.8) 上無法如預期運作，請使用下列檢查清單：

- 如果您的應用程式開發在從 .NET Framework 4.0 開始的任何 .NET Framework 版本上執行，請參閱 [應用程式相容性](application-compatibility.md) ，以產生您的目標 .NET Framework 版本與您的應用程式執行所在版本之間的變更清單。

- 如果您有 .NET Framework 3.5 應用程式，另請參閱 [.NET Framework 4 移轉問題](net-framework-4-migration-issues.md)。

- 如果您有 .NET Framework 2.0 應用程式，另請參閱 [.NET Framework 3.5 SP1 中的變更](/previous-versions/dotnet/articles/dd310284(v=msdn.10))。

- 如果您有 .NET Framework 1.1 應用程式，另請參閱 [.NET Framework 2.0 中的變更](/previous-versions/aa570326(v=msdn.10))。

- 如果您正在重新編譯現有原始程式碼以便在 .NET Framework 4.5 或其點版本執行，或如果您正在開發的新版本應用程式或元件針對 .NET Framework 4.5，或針對來自其現有原始程式碼基底的點版本，請檢查 [.NET Framework 類別庫中已淘汰的功能](../whats-new/whats-obsolete.md)中已淘汰類型和成員，並套用所述的因應措施。 (之前編譯的程式碼將會針對已標示為過時的型別和成員繼續執行)。

- 如果您判斷 .NET Framework 4.5 中的變更已中斷應用程式，請檢查執行時間[設定架構](../configure-apps/file-schema/runtime/index.md)（尤其是[ \<AppContextSwitchOverrides> 元素](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)），以判斷您是否可以在應用程式的設定檔案中使用執行時間設定，以還原先前的行為。

- 如果您遇到未記載的問題，請在 [.NET 開發人員社群網站](https://aka.ms/feedback/report?space=61)或 [Microsoft/dotnet GitHub 存放庫](https://github.com/microsoft/dotnet/issues)中開啟問題。

## <a name="side-by-side-execution"></a>並存執行

如果您找不到適合您問題的因應措施，請記住，.NET Framework 4.5 (或其中一個點發行版) 與1.1、2.0 和3.5 版本並存執行，而且是取代第4版的就地更新。 針對以1.1、2.0 和3.5 版為目標的應用程式，您可以在目的電腦上安裝適當版本的 .NET Framework，以在其最佳環境中執行應用程式。 如需並存執行的詳細資訊，請參閱[並存執行](../deployment/side-by-side-execution.md)。

## <a name="see-also"></a>請參閱

- [新功能](../whats-new/index.md)
- [類別庫中的過時功能](../whats-new/whats-obsolete.md)
- [應用程式相容性](application-compatibility.md)
- [.NET Framework 官方支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [.NET Framework 4 個遷移問題](net-framework-4-migration-issues.md)
