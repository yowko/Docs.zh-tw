---
title: .NET Native 一般疑難排解
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca0f093e85a5ac983266ba34f78021d6af6018c0
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052025"
---
# <a name="net-native-general-troubleshooting"></a>.NET Native 一般疑難排解
本主題描述如何開發使用.NET Native 應用程式時，可能會遇到的潛在問題進行疑難排解。  
  
- **問題：** 您的建置輸出視窗未正確更新。  
  
     **解決方式：** 組建完成之前，不會更新建置輸出視窗。 建置時間可能長達數分鐘，因此您可能晚點才會看到更新。  
  
- **問題：** 增加您的應用程式正式版本建置階段 ARM。  
  
     **解決方式：** 當您將應用程式部署到 ARM 裝置時，會叫用.NET 原生的基礎結構。 這個編譯會執行大量最佳化，同時確保該非靜態語意 (例如反映) 仍然能夠正常運作。 此外，應用程式使用的 .NET Framework 部分已靜態連結，以取得最佳效能，因此也必須編譯成機器碼。 這就是編譯需要更多時間的原因。  
  
     不過，對於標準開發電腦上的大多數應用程式而言，編譯時間仍然在標準編譯的一分鐘內。  一般而言，光是在標準開發電腦上產生 .NET Framework 的原生映像就需要數分鐘。  即使執行所有最佳化來改善產生的程式碼 (包括使用 .NET Framework)，應用程式建置時間通常還是需要一到兩分鐘。  
  
     我們將調查多執行緒編譯和其他最佳化，持續提升編譯效能。  
  
- **問題：** 您不知道您的應用程式使用.NET Native 來編譯。  
  
     **解決方式：** 如果.NET Native 編譯器會叫用，您會發現時間更長的建置時間、 工作管理員 會顯示各種.NET 原生的元件處理序，例如 ILC.exe 和 nutc_driver.exe。  
  
     您已成功建置使用.NET 原生專案之後，您會發現在 obj 輸出\\*config*\ *arch*\\*projectname*。 ilc\out。您可以在 bin\\*arch*\\*config*\AppX 下找到最終的原生套件內容。 如果已部署應用程式，則最終的原生套件內容位於 \bin\\*arch*\\*config*\AppX 下。  
  
- **問題：**.NET Native 編譯應用程式會擲回執行階段例外狀況 (通常[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)或是[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)例外狀況)，它未擲回時不編譯.NET 原生。  
  
     **解決方式：** 因為.NET Native 未提供的中繼資料或實作程式碼可透過反映，則會擲回例外狀況。 (如需詳細資訊，請參閱 [.NET Native 和編譯](../../../docs/framework/net-native/net-native-and-compilation.md))。若要排除例外狀況，您必須在[執行階段指示詞 (rd.xml) 檔案](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)中新增一個項目，如此一來，.NET Native 工具鏈便可以在執行階段提供中繼資料或實作程式碼。 您可以使用兩個疑難排解工具，這些工具會產生要加入執行階段指示詞檔案的必要項目：  
  
    - 針對類型的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/type.html) 。  
  
    - 針對方法的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/method.html) 。  
  
     如需詳細資訊，請參閱[反映和 .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)。  
  
## <a name="see-also"></a>另請參閱

- [將您的 Windows 市集應用程式移轉至 .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
