---
title: ".NET Native 一般疑難排解"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e92e99b978d12c32cc46b9133621875f35af634
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="net-native-general-troubleshooting"></a>.NET Native 一般疑難排解
本主題說明如何對使用 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 開發應用程式時可能遇到的問題進行疑難排解。  
  
-   **問題：**您的建置輸出視窗未正確更新。  
  
     **解決方式：**建置輸出視窗必須等到建置完成才會更新。 建置時間可能長達數分鐘，因此您可能晚點才會看到更新。  
  
-   **問題：**ARM 的應用程式正式版本建置時間變長。  
  
     **解決方式：**當您將應用程式部署至 ARM 裝置時，會叫用 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 基礎結構。 這個編譯會執行大量最佳化，同時確保該非靜態語意 (例如反映) 仍然能夠正常運作。 此外，應用程式使用的 .NET Framework 部分已靜態連結，以取得最佳效能，因此也必須編譯成機器碼。 這就是編譯需要更多時間的原因。  
  
     不過，對於標準開發電腦上的大多數應用程式而言，編譯時間仍然在標準編譯的一分鐘內。  一般而言，光是在標準開發電腦上產生 .NET Framework 的原生映像就需要數分鐘。  即使執行所有最佳化來改善產生的程式碼 (包括使用 .NET Framework)，應用程式建置時間通常還是需要一到兩分鐘。  
  
     我們將調查多執行緒編譯和其他最佳化，持續提升編譯效能。  
  
-   **問題：**您不確定是否已使用 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 編譯應用程式。  
  
     **解決方式：**如果叫用 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 編譯器，您會發現建置時間更久，且工作管理員會顯示各種 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 元件處理序，例如 ILC.exe 和 nutc_driver.exe。  
  
     使用 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 成功建置專案之後，您將在 obj\\*config*\ *arch*\\<專案名稱>.ilc\out 下找到輸出。您可以在 bin\\*arch*\\*config*\AppX 下找到最終的原生套件內容。 如果已部署應用程式，則最終的原生套件內容位於 \bin\\*arch*\\*config*\AppX 下。  
  
-   **問題：**以 .NET Native 編譯的應用程式正在擲回執行階段例外狀況 (通常是 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 或 [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 例外狀況)，未使用 .NET Native 編譯時不會擲回該例外狀況。  
  
     **解決方式：**擲回例外狀況的原因是 .NET Native 未提供可透過反映提供的中繼資料或實作程式碼 (如需詳細資訊，請參閱 [.NET Native 和編譯](../../../docs/framework/net-native/net-native-and-compilation.md))。若要排除例外狀況，您必須在[執行階段指示詞 (rd.xml) 檔案](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)中新增一個項目，如此一來，.NET Native 工具鏈便可以在執行階段提供中繼資料或實作程式碼。 您可以使用兩個疑難排解工具，這些工具會產生要加入執行階段指示詞檔案的必要項目：  
  
    -   針對類型的 [MissingMetadataException 疑難排解工具](http://dotnet.github.io/native/troubleshooter/type.html) 。  
  
    -   針對方法的 [MissingMetadataException 疑難排解工具](http://dotnet.github.io/native/troubleshooter/method.html) 。  
  
     如需詳細資訊，請參閱[反映和 .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)。  
  
## <a name="see-also"></a>請參閱  
 [將您的 Windows 市集應用程式移轉至 .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
