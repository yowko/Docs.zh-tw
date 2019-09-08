---
title: 風險降低：路徑正規化
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5ea69d80a225adfc2f409e8303ee1c241398db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779341"
---
# <a name="mitigation-path-normalization"></a>風險降低：路徑正規化
從以 .NET Framework 4.6.2 為目標的應用程式開始，.NET Framework 中的路徑正規化已有所變更。  
  
## <a name="what-is-path-normalization"></a>路徑正規化是什麼？  
 路徑正規化牽涉到修改識別路徑或檔案的字串，使其符合目標作業系統上的有效路徑。 正規化通常牽涉到︰  
  
- 規範化元件和目錄分隔符號。  
  
- 將目前的目錄套用到相對路徑。  
  
- 評估路徑中的相對目錄 (`.`) 或上層目錄 (`..`)。  
  
- 修剪指定的字元。  
  
## <a name="the-changes"></a>變更  
 從以 .NET Framework 4.6.2 為目標的應用程式開始，路徑正規化在下列方面已有所變更：  
  
- 執行階段會延後至作業系統的 [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) 函式再進行路徑正規化。  
  
- 正規化不再涉及修剪目錄區段的結尾 (例如目錄名稱結尾的空格)。  
  
- 支援完全信任的裝置路徑語法，包括 `\\.\` 以及適用於 mscorlib.dll 中之檔案 I/O API 的 `\\?\`。  
  
- 執行階段不會驗證裝置語法路徑。  
  
- 支援使用裝置語法存取替代資料流。  
  
## <a name="impact"></a>影響  

對於以 .NET Framework 4.6.2 或更新版本為目標的應用程式，這些變更預設為開啟。 它們應該可以改善效能，同時允許方法存取先前無法存取的路徑。  
  
此變更不會影響以 .NET Framework 4.6.1 和舊版為目標但執行於 .NET Framework 4.6.2 或更新版本下的應用程式。  
  
## <a name="mitigation"></a>緩和  
 以 .NET Framework 4.6.2 或更新版本為目標的應用程式，可透過在應用程式組態檔的[\<執行階段>](../configure-apps/file-schema/runtime/runtime-element.md) 區段中新增下列內容來選擇退出此變更，並使用舊版行為：  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
以 .NET Framework 4.6.1 或更早版本為目標，但在 .NET Framework 4.6.2 或更新版本上執行的應用程式，可以藉由在應用程式組態檔的[\<執行階段>](../configure-apps/file-schema/runtime/runtime-element.md) 區段新增下行，就能啟用路徑正規化的變更：  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>另請參閱

- [重定目標變更](retargeting-changes-in-the-net-framework-4-6-2.md)
