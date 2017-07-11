---
title: ".NET Framework 中的應用程式相容性 | Microsoft Docs"
ms.custom: 
ms.date: 05/19/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
- app-compat
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
caps.latest.revision: 19
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d0d39f1d6d15dc2757387ea83d3a0f868f6ec17
ms.openlocfilehash: 9169b8ec118ed0d9ab3f05eec47317cf68551754
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017

---

<a id="application-compatibility-in-the-net-framework" class="xliff"></a>
# .NET Framework 中的應用程式相容性

<a id="introduction" class="xliff"></a>
## 簡介
相容性是每個 .NET 版本都極為重視的目標。 相容性可確保每個版本都能累加，讓舊版仍能運作。 另一方面，舊版功能的變更 (為改善效能、處理安全性問題，或修正 Bug) 會造成現有程式碼或現有應用程式中在更新版本下執行的相容性問題。 .NET Framework 可辨識重定目標變更及執行階段變更。 重定目標變更會影響以 .NET Framework 特定版本為目標，但在更新版本上執行的應用程式。 執行階段變更會影響在特定版本上執行的所有應用程式。

每個應用程式都有特定版本的 .NET Framework 目標，可以下列方式指定：

* 在 Visual Studio 中定義目標架構。
* 在專案檔中指定目標架構。
* 將 <xref:System.Runtime.Versioning.TargetFrameworkAttribute> 套用至原始程式碼。

在比目標版本更新的版本上執行時，.NET Framework 會使用古怪的行為，模擬較舊的目標版本。 換句話說，應用程式會在較新的 Framework 版本上執行，但表現出的行為如同在較舊的版本上執行。 .NET Framework 版本間的許多相容性問題是透過這種古怪的模型而降低。

<a id="runtime-changes" class="xliff"></a>
## 執行階段變更

執行階段問題是在電腦上進行新的執行階段，而相同的二進位檔案也在執行時，會看到不同的行為。 如果二進位檔已針對 .NET Framework 4.0 編譯，它就可以在 4.5 或更新版本中以 .NET Framework 4.0 相容性模式執行。 許多影響 4.5 的變更不會影響針對 4.0 所編譯的二進位檔。 這是 AppDomain 特有的功能，視項目組件的設定而定。

<a id="retargeting-changes" class="xliff"></a>
## 重定目標變更

重定目標問題，是當以 4.0 為目標的組件現在設定為以 4.5 為目標時發生的問題。 現在，組件選擇加入新功能並成為可能的舊功能相容性問題。 這同樣受項目組件支配，所以主控台應用程式會使用組件，或網站會參考組件。

<a id="net-compatibility-diagnostics" class="xliff"></a>
## .NET 相容性診斷

.NET 相容性診斷是由 Roslyn 提供的分析器，可協助您識別各版 .NET Framework 之間的應用程式相容性問題。 此清單包含所有可用的分析器，但只有一部分會套用至任何特定的移轉。 分析器會判斷適用於規劃之移轉的問題，並且只會呈現這些問題。

每個問題包含下列資訊：

-   舊版中已變更的內容描述。

-   變更如何影響客戶，以及是否有任何因應措施可保留版本間的相容性。

-   變更的重要性評估。 應用程式相容性問題可分類如下：

    |   |   |
    |---|---|
    |主要|影響大量應用程式或需要大幅修改程式碼的重大變更。|
    |次要|影響少量應用程式或需要稍微修改程式碼的變更。|
    |邊緣案例|在非常特定 (罕見) 的情況下影響應用程式的變更。|
    |透明|對應用程式的開發人員或使用者影響的不明顯變更。|

-   第一次出現此變更的 Framework 版本。 也指出某些變更會引入到特定版本，然後在更新版本中還原。

-   變更類型：

    |   |   |
    |---|---|
    |正在重定目標|此變更會影響為了以新版 .NET Framework 為目標而重新編譯的應用程式。|
    |執行階段|此變更會影響以舊版 .NET Framework 為目標但在新版上執行的現有應用程式。|

-   受影響的 API (如果有的話)。

-   可用診斷的識別碼

<a id="usage" class="xliff"></a>
## 使用方式
若要開始，請選取以下的相容性變更類型：

* [重定目標變更](./retargeting/index.md)
* [執行階段變更](./runtime/index.md)


<a id="see-also" class="xliff"></a>
## 另請參閱

* [版本和相依性](../../../docs/framework/migration-guide/versions-and-dependencies.md)
* [新功能](../../../docs/framework/whats-new/index.md)
* [類別庫中已淘汰的功能](../../../docs/framework/whats-new/whats-obsolete.md)

