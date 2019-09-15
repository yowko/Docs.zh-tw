---
title: 資訊清單
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 053726b200b73956099ff9274cc8f63f21d8fc64
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973170"
---
# <a name="assembly-manifest"></a>資訊清單
每個組件 (不論是靜態或是動態) 都含有描述組件中項目彼此如何關聯的資料集合。 組件資訊清單就包含這個組件的中繼資料。 組件資訊清單含有指定組件的版本需求和安全性識別所需的所有中繼資料，以及定義組件範圍和解析資源與類別參考所需的所有中繼資料。 組件資訊清單可以儲存在 PE 檔（ *.exe*或 *.dll*）中，並以 MICROSOFT 中繼語言（MSIL）程式碼或只包含組件資訊清單資訊的獨立 PE 檔案。  
  
 下圖所示為儲存資訊清單的不同方式。  
  
 ![在單一檔案組件和多檔案組件組態中顯示資訊清單的圖表。](./media/manifest/assembly-types-diagram.gif)  
  
 對於具有一個關聯檔案的組件，資訊清單是合併在 PE 檔中以構成單一檔案組件。 您可以建立多檔案組件，它可具有獨立的資訊清單檔案，或者將資訊清單合併在該組件中的某一個 PE 檔中。  
  
 每個組件的資訊清單都會執行下列功能：  
  
- 列舉構成組件的檔案  
  
- 控制組件之型別和資源的參考如何對應到含有它們的宣告和實作的檔案  
  
- 列舉組件所依賴的其他組件  
  
- 在組件使用者與組件的實作詳細資料之間提供一層間接取值 (Indirection)  
  
- 轉譯組件的自我描述  
  
## <a name="assembly-manifest-contents"></a>組件資訊清單內容  
 下表所示為組件資訊清單中包含的資訊。 前四個專案：元件名稱、版本號碼、文化特性和強式名稱資訊組成元件的身分識別。  
  
|內容|說明|  
|-----------------|-----------------|  
|組件名稱|指定組件名稱的文字字串。|  
|版本號碼|主要和次要版本號碼，以及修訂和組建編號。 Common Language Runtime 會使用這些編號來強制執行版本原則。|  
|culture|有關組件所支援文化特性或語言的資訊。 這項資訊應該只用來將組件指定為包含文化特性或語言相關資訊的附屬組件 (具有文化特性資訊的組件會自動假設為附屬組件)。|  
|強式名稱資訊|如果已經為組件指定強式名稱，則為發行者 (Publisher) 的公開金鑰 (Public Key)。|  
|組件中所有檔案的清單|組件中所含每一檔案的雜湊和檔名。 請注意，構成組件的所有檔案必須與含有組件資訊清單的檔案在同一個目錄中。|  
|型別參考資訊|Runtime 用來將型別參考對應到含有其宣告和實作之檔案的資訊。 這是使用於從組件匯出之型別。|  
|所參考組件的資訊|組件以靜態方式參考之其他組件的清單。 每一參考包括相依組件的名稱、組件中繼資料 (版本、文化特性、作業系統等)，以及公開金鑰 (如果組件具有強式名稱)。|  
  
 您可以在程式碼中使用組件屬性在組件資訊清單中加入或變更某些資訊。 您可以變更版本資訊和資訊屬性，包括商標、著作權、產品、公司和資訊版本。 如需元件屬性的完整清單，請參閱[設定元件屬性](set-attributes.md)。  
  
## <a name="see-also"></a>另請參閱

- [元件內容](contents.md)
- [元件版本控制](versioning.md)
- [建立附屬元件](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [強式名稱的組件](strong-named.md)
