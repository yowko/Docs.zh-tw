---
title: ".NET Framework 的版本相容性 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework 4.5, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
caps.latest.revision: 35
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 09f682d9c3a1cf5d42bba878676d84b9328a1a81
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="version-compatibility-in-the-net-framework"></a>.NET Framework 的版本相容性
回溯相容性表示針對特定平台版本開發的應用程式將會在該平台的較新版本上執行。 .NET Framework 嘗試最大化回溯相容性：針對某一個 .NET Framework 版本撰寫的原始程式碼應該在較新版本的 .NET Framework 上編譯，而且在某一個 .NET Framework 版本上執行之二進位檔的行為應該與較新版本的 .NET Framework 相同。  
  
<a name="Apps"></a>   
## <a name="version-compatibility-for-apps"></a>應用程式的版本相容性  
 根據預設，應用程式會在其建置所針對的 .NET Framework 版本上執行。 如果該版本不存在，而且應用程式組態檔並未定義支援的版本，則可能會發生 .NET Framework 初始化錯誤。 在此例中，嘗試執行應用程式的作業將會失敗。  
  
 若要定義應用程式執行所在的特定版本，請將一個或多個 [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 項目新增至應用程式的組態檔。 每一個 `<supportedRuntime>` 項目都會列出支援的執行階段版本，最先指定的是最優先的版本，而最後指定的則是優先順序最低的版本。  
  
```xml  
  
<configuration>  
   <startup>  
      <supportedRuntime version="v2.0.50727" />  
      <supportedRuntime version="v4.0" />  
   </startup>  
</configuration>  
  
```  
  
 如需詳細資訊，請參閱[如何：設定應用程式以支援 .NET Framework 4 或 4.x](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)。  
  
## <a name="version-compatibility-for-components"></a>元件的版本相容性  
 應用程式可以控制其執行所在的 .NET Framework 版本，但是元件則無法控制。 元件和類別庫會在特定應用程式的內容中載入，因此會自動在應用程式執行所在的 .NET Framework 版本上執行。  
  
 由於這項限制，所以相容性保證對於元件特別重要。 從 .NET Framework 4 開始，您可以指定元件在多個版本中維持相容所需的程度，方法是將 <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=fullName> 屬性套用至該元件。 工具可以使用這個屬性來偵測將來的元件版本中，是否有可能違反相容性保證的狀況。  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a>回溯相容性和 .NET Framework 4.5  
 .NET Framework 4.5 及其點版本 (4.5.1、4.5.2、4.6、4.6.1、4.6.2 和 4.7) 可與使用舊版 .NET Framework 建置的應用程式回溯相容。 換句話說，使用舊版建置的應用程式和元件不需經過修改，就可在 .NET Framework 4.5 上運作。 不過，應用程式預設會在做為其開發目標的 Common Language Runtime 版本上執行，因此您可能需要提供組態檔，才能讓您的應用程式在 .NET Framework 4.5 上執行。 如需詳細資訊，請參閱本文前面的[應用程式的版本相容性](#Apps)一節。  
  
 在實際操作中，.NET Framework 中似乎前後不一致的變更以及程式設計技術的變更可能會破壞此相容性。 例如，.NET Framework 4.5 中的效能改良可能會暴露在舊版不會發生的競爭情況。 同樣地，使用 .NET Framework 組件的硬式編碼路徑、搭配特定版本的 .NET Framework 執行相等比較以及使用反映來取得私用欄位的值，都不是具有回溯相容性的作法。 此外，每一個 .NET Framework 版本都包含可能會影響某些應用程式與元件之相容性的 Bug 修正和安全性相關的變更。  
  
 如果您的應用程式或元件無法依預期的方式在 .NET Framework 4.5 (包括其點版本 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]和 4.5.2)、4.6、4.6.1、4.6.2 或 4.7 上運作，請使用下列檢查清單：  
  
-   檢查下列主題，找出任何可能會影響應用程式的變更，並套用所述的替代解決辦法：  
  
    -   [.NET Framework 4 移轉問題](http://go.microsoft.com/fwlink/p/?LinkId=248212)  
  
    -   [4.5 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)  
  
    -   [4.5.1 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)  
  
    -   [4.5.2 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)  
  
    -   [4.6 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6.md)  
  
    -   [4.6.1 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)  
  
    -   [4.6.2 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)  

    - [4.7 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
       
-   如果您有 .NET Framework 1.1 應用程式，請同時檢閱下列主題：  
  
    -   [.NET Framework 2.0 的變更](http://go.microsoft.com/fwlink/?LinkID=125263)  
  
    -   [.NET Framework 3.5 SP1 的變更](http://go.microsoft.com/fwlink/?LinkId=186989)  
  
-   如果您正在重新編譯現有的原始程式碼以便在 .NET Framework 4.5 或其點版本上執行，或者您正從現有的原始程式碼基底開發以 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為目標的新版應用程式或元件，請查看[類別庫中的過時功能](../../../docs/framework/whats-new/whats-obsolete.md)中的過時類型和成員，並套用所述的因應措施 (之前編譯的程式碼將會針對已標示為過時的型別和成員繼續執行)。  
  
-   如果您判斷 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中的某項變更已經破壞您的應用程式，請查看[執行階段設定結構描述](../../../docs/framework/configure-apps/file-schema/runtime/index.md)來判斷您是否可以在應用程式組態檔中使用執行階段設定，以還原舊版行為。  
  
-   如果您遇到未記載的問題，請記錄 [Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=154815) 錯誤 (bug)，然後連絡 [netfxcf@microsoft.com](mailto:netfxcf@microsoft.com) 並提供錯誤 (bug) 編號。  
  
## <a name="compatibility-and-side-by-side-execution"></a>相容性和並存執行  
 如果您找不到問題的適當因應措施，請記得 .NET Framework 4.5 (或其中一個點版本) 會與版本 1.1、2.0 和 3.5 並存執行，而且是取代第 4 版的就地更新。 若是以 1.1、2.0 和 3.5 版為目標的應用程式，您可以在目標電腦上安裝適當的 .NET Framework 版本，以便在最佳環境中執行應用程式。 如需並存執行的詳細資訊，請參閱[並存執行](../../../docs/framework/deployment/side-by-side-execution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [新功能](../../../docs/framework/whats-new/index.md)   
 [類別庫中的過時功能](../../../docs/framework/whats-new/whats-obsolete.md)   
 [應用程式相容性](../../../docs/framework/migration-guide/application-compatibility.md)   
 [Microsoft .NET Framework 支援週期原則](http://go.microsoft.com/fwlink/p/?LinkId=248212)   
 [.NET Framework 4 移轉問題](http://go.microsoft.com/fwlink/p/?LinkId=248212)
