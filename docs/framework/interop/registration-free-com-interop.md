---
title: 免註冊的 COM Interop
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 939630726f399184c264f73ee01270f50981e83a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484801"
---
# <a name="registration-free-com-interop"></a>免註冊的 COM Interop
免註冊的 COM Interop 不需要使用 Windows 登錄來儲存組件資訊，即可啟動元件。 您不是在部署期間在電腦上登錄元件，而是在設計階段建立 Win32 樣式資訊清單檔案，其中包含繫結和啟動的相關資訊。 這些資訊清單檔案 (而不是登錄機碼) 會引導物件的啟動。  
  
 為您的組件使用免註冊啟動，而不是在部署期間將其註冊，有兩個優點：  
  
-   當電腦上安裝多個 DLL 版本時，您可以控制要啟動哪個版本。  
  
-   使用者可以使用 XCOPY 或 FTP，將您的應用程式複製到他們電腦上的適當目錄。 然後就可以從該目錄執行應用程式。  
  
 本節說明免註冊 COM Interop 所需的兩種資訊清單類型：應用程式和元件資訊清單。 這些資訊清單是 XML 檔案。 應用程式資訊清單是由應用程式開發人員建立，其中包含說明組件和組件相依性的中繼資料。 元件資訊清單是由元件開發人員建立，其中包含其他位在 Windows 登錄中的資訊。  
  
### <a name="requirements-for-registration-free-com-interop"></a>免註冊 COM Interop 的需求  
  
1.  對免註冊 COM Interop 的支援，會依據程式庫組件的類型而稍微不同；具體來說，就是組件為 Unmanaged (COM 並存) 或 Managed (.NET 架構)。 下表顯示各組件類型的作業系統和 .NET Framework 版本需求。  
  
    |組件類型|作業系統|.NET Framework 版本|  
    |-------------------|----------------------|----------------------------|  
    |COM 並存|Microsoft Windows XP|不需要。|  
    |.NET 架構|Windows XP 含 SP2|NET Framework 1.1 或更新版本。|  
  
     Windows Server 2003 系列也支援適用於 .NET 架構組件的免註冊 COM Interop。  
  
     若要使 .NET 架構的類別相容於來自 COM 的免註冊啟動，該類別必須要有預設建構函式，而且必須是公用的。  
  
### <a name="configuring-com-components-for-registration-free-activation"></a>設定適用於免註冊啟動的 COM 元件  
  
1.  若要讓 COM 元件參與免註冊啟動，必須將其部署為並存組件。 並存組件是 Unmanaged 組件。  如需詳細資訊，請參閱[使用並存組件](/windows/desktop/SbsCs/using-side-by-side-assemblies) \(英文\)。  
  
     若要使用 COM 並存組件，.NET 架構應用程式開發人員必須提供應用程式資訊清單，其中包含繫結和啟動資訊。 對 Unmanaged 並存組件的支援內建在 Windows XP 作業系統中。 當所要啟動的元件不在登錄中時，COM 執行階段 (作業系統可支援) 會掃描應用程式資訊清單，以取得啟動資訊。  
  
     針對安裝在 Windows XP 上的 COM 元件，免註冊啟動是選擇性的。 如需將並存組件加入至應用程式的詳細指示，請參閱[使用並存組件](/windows/desktop/SbsCs/using-side-by-side-assemblies) \(英文\)。  
  
    > [!NOTE]
    >  並存執行是 .NET Framework 的功能，可讓多版執行階段，以及使用某版執行階段的多版應用程式和元件，同時在同一部電腦上執行。 並存執行和並存組件是提供並行功能的不同機制。  
  
## <a name="see-also"></a>請參閱  
 [如何：設定免註冊啟用的 .NET Framework 架構 COM 元件](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
