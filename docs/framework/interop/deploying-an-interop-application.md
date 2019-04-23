---
title: 部署 Interop 應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], interop
- strong-named assemblies, interop applications
- unsigned assemblies
- private assemblies
- exposing COM components to .NET Framework
- interoperation with unmanaged code, deploying applications
- shared assemblies
- COM interop, deploying applications
- interoperation with unmanaged code, exposing COM components
- signed assemblies
- COM interop, exposing COM components
ms.assetid: ea8a403e-ae03-4faa-9d9b-02179ec72992
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9bacc8f67755319b416c14766204f6eb2be52de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192078"
---
# <a name="deploying-an-interop-application"></a>部署 Interop 應用程式
Interop 應用程式通常包含 .NET 用戶端組件、代表各種不同 COM 型別程式庫的一或多個 Interop 組件，以及一或多個已登錄的 COM 元件。 Visual Studio 和 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 提供工具以匯入型別程式庫，並將它轉換成 Interop 組件，如[匯入型別程式庫作為組件](importing-a-type-library-as-an-assembly.md)中所述。 有兩種方式可以部署 Interop 應用程式：  
  
-   使用內嵌的 Interop 類型：從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，您可以指示編譯器將 Interop 組件的類型資訊內嵌到可執行檔。 編譯器只會內嵌應用程式使用的類型資訊。 您不必與應用程式一起部署 Interop 組件。 這是建議使用的技巧。  
  
-   部署 Interop 組件：您可以建立 Interop 組件的標準參考。 在此情況下，Interop 組件必須與您的應用程式一起部署。 如果您運用這項技巧，但不使用私用的 COM 元件，請一律參考 COM 元件作者發佈的主要 Interop 組件 (PIA)，這是您想要併入 Managed 程式碼的 COM 元件。 如需產生和使用主要 Interop 組件的詳細資訊，請參閱[主要 Interop 組件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))。  
  
 如果您使用內嵌的 Interop 類型，部署就會簡單且直接。 您不需要特別做什麼。 這篇文章的其餘部分會說明部署 Interop 組件和您應用程式的狀況。  
  
## <a name="deploying-interop-assemblies"></a>部署 Interop 組件  
 組件可以有強式名稱。 強式名稱組件包含發行者的公開金鑰，這會提供唯一識別。 [型別程式庫匯入工具 (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) 所產生的組件可由發行者使用 **/keyfile** 選項簽署。 您可以將已簽署的組件安裝到全域組件快取。 未簽署的組件必須安裝在使用者電腦上，當成私用組件。  
  
### <a name="private-assemblies"></a>私用組件  
 若要安裝供私人使用的組件，應用程式可執行檔和包含已匯入 COM 類型的 Interop 組件，都必須以相同的目錄結構安裝。 下圖顯示供 Client1.exe 和 Client2.exe 私下使用的未簽署 Interop 組件，它們位在不同的應用程式目錄中。 本例中稱之為 LOANLib.dll 的 Interop 組件，安裝了兩次。  
  
 ![目錄結構和 Windows 登錄](./media/deploying-an-interop-application/com-private-deployment.gif "私用部署的目錄結構和登錄項目")  
  
 與應用程式建立關聯的所有 COM 元件都必須都安裝在 Windows 登錄中。 如果圖中的 Client1.exe 和 Client2.exe 安裝在不同的電腦上，您必須在兩部電腦上都登錄 COM 元件。  
  
### <a name="shared-assemblies"></a>共用組件  
 多個應用程式共用的組件應該安裝在稱為全域組件快取的集中式存放庫中。 .NET 用戶端可以存取相同的 Interop 組件複本，它是簽署並安裝在全域組件快取中。 如需產生和使用主要 Interop 組件的詳細資訊，請參閱[主要 Interop 組件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))。  
  
## <a name="see-also"></a>另請參閱

- [將 COM 元件公開給 .NET Framework](exposing-com-components.md)
- [匯入類型程式庫做為組件](importing-a-type-library-as-an-assembly.md)
- [在受控程式碼中使用 COM 型別](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [編譯 Interop 專案](compiling-an-interop-project.md)
