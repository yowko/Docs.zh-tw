---
title: 強式名稱的組件
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 72e9e698e510153073515aa891f1ed3b4d7b9886
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081433"
---
# <a name="strong-named-assemblies"></a>強式名稱的組件
強式命名組件會為組件建立唯一識別，並可防止發生組件衝突。  
  
## <a name="what-makes-a-strong-named-assembly"></a>構成強式名稱的組件之項目為何？  
 強式名稱的組件是透過私密金鑰所產生，該私密金鑰對應至隨組件或當做組件本身散發的公開金鑰。 該組件包含組件資訊清單，其中包含構成組件之所有檔案的名稱和雜湊。 具有相同強式名稱的組件應該是相同的。  
  
 您可以使用 Visual Studio 或命令列工具強式命名組件。 如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)或 [Sn.exe (強式名稱工具)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)。  
  
 建立強式名稱的組件時，會包含組件的簡單文字名稱、版本號碼、文化特性資訊 (選擇性)、數位簽章，以及對應至用於簽署之私密金鑰的公開金鑰。  
  
> [!WARNING]
>  請勿依賴強式名稱提供安全性。 強式名稱僅提供唯一識別。  
  
## <a name="why-strong-name-your-assemblies"></a>為什麼需要強式命名您的組件？  
 當您參考強式名稱的組件時，您會希望取得某些優點，例如版本控制和命名保護。 強式名稱的組件可安裝在全域組件快取中，在某些情況下您必須這麼做。  
  
 強式名稱的組件在下列情況下很實用：  
  
-   您想要啟用組件以供強式名稱的組件參考，或者您想要授與 `friend` 存取權，以從其他強式名稱的組件存取您的組件。  
  
-   應用程式需要存取相同組件的不同版本。 這表示您需要在不起衝突的情況下，在同一個應用程式網域中並存載入組件的不同版本。 例如，如果組件中存在具有相同簡單名稱的不同應用程式開發介面擴充模組，強式命名會為每個組件版本提供唯一識別。  
  
-   您不希望在使用組件時，對應用程式效能造成負面影響，因此想要使用領域中性的組件。 由於領域中性的組件必須安裝在全域組件快取中，因此需要對其強式命名。  
  
-   當您要藉由套用發行者原則來集中提供應用程式時，換句話說，組件必須安裝在全域組件快取中。  
  
 如果您是開放原始碼開發人員並需要強式名稱組件的識別優點，請考慮將與組件相關聯的私密金鑰簽入原始檔控制系統中。  
  
## <a name="see-also"></a>另請參閱

- [全域組件快取](../../../docs/framework/app-domains/gac.md)
- [如何：使用強式名稱簽署組件](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [Sn.exe (強式名稱工具)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
