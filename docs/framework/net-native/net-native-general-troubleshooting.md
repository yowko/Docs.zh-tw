---
title: .NET Native 一般疑難排解
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea5f61b0e250c4f51a966bc60959f7559d8e2fe2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049392"
---
# <a name="net-native-general-troubleshooting"></a>.NET Native 一般疑難排解

本主題說明如何針對使用 .NET Native 開發應用程式時可能遇到的潛在問題進行疑難排解。

- **問題：** 您的組建輸出視窗未正確更新。

  **分析**在組建完成之前，不會更新 [組建輸出] 視窗。 建置時間可能長達數分鐘，因此您可能晚點才會看到更新。

- **問題：** 您應用程式的 ARM 零售組建時間已增加。

  **分析**當您將應用程式部署至 ARM 裝置時，會叫用 .NET Native 的基礎結構。 這個編譯會執行大量最佳化，同時確保該非靜態語意 (例如反映) 仍然能夠正常運作。 此外，應用程式使用的 .NET Framework 部分已靜態連結，以取得最佳效能，因此也必須編譯成機器碼。 這就是編譯需要更多時間的原因。

  不過，對於標準開發電腦上的大多數應用程式而言，編譯時間仍然在標準編譯的一分鐘內。  一般而言，光是在標準開發電腦上產生 .NET Framework 的原生映像就需要數分鐘。  即使執行所有最佳化來改善產生的程式碼 (包括使用 .NET Framework)，應用程式建置時間通常還是需要一到兩分鐘。

  我們將調查多執行緒編譯和其他最佳化，持續提升編譯效能。

- **問題：** 您不知道您的應用程式是使用 .NET Native 編譯。

  **分析**如果叫用 .NET Native 編譯器，您會發現組建時間較長，而且 [工作管理員] 會顯示各種 .NET Native 元件進程，例如 ILC.OUT .exe 和 nutc_driver。

  使用 .NET Native 成功建立專案之後，\\ \\您會*在 obj* \ 設定架構*專案名稱*ilc\out. 中找到輸出。您可以在 bin\\*arch*\\*config*\AppX 下找到最終的原生套件內容。 如果已部署應用程式，則最終的原生套件內容位於 \bin\\*arch*\\*config*\AppX 下。

- **問題：** 您 .NET Native 編譯的應用程式會擲回執行時間例外狀況（通常是[MissingMetadataException](missingmetadataexception-class-net-native.md)或[MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)例外狀況），而不會在沒有 .NET Native 的情況下進行編譯。

  **分析**會擲回例外狀況，因為 .NET Native 並未提供可透過反映取得的中繼資料或執行程式碼。 (如需詳細資訊，請參閱 [.NET Native 和編譯](net-native-and-compilation.md))。若要排除例外狀況，您必須在[執行階段指示詞 (rd.xml) 檔案](runtime-directives-rd-xml-configuration-file-reference.md)中新增一個項目，如此一來，.NET Native 工具鏈便可以在執行階段提供中繼資料或實作程式碼。 您可以使用兩個疑難排解工具，這些工具會產生要加入執行階段指示詞檔案的必要項目：

  - 針對類型的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/type.html) 。

  - 針對方法的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/method.html) 。

  如需詳細資訊，請參閱[反映和 .NET Native](reflection-and-net-native.md)。

## <a name="see-also"></a>另請參閱

- [將您的 Windows 市集應用程式移轉至 .NET Native](migrating-your-windows-store-app-to-net-native.md)
