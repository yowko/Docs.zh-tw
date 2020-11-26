---
title: 風險降低：WPF 版面配置
description: 瞭解如何減輕 WPF 控制項配置變更所產生的問題，例如，將物件的位置移動一個圖元。
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: caed758f6e86a1e2bee255c2f29ca3160b327e17
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244076"
---
# <a name="mitigation-wpf-layout"></a>風險降低：WPF 版面配置

WPF 控制項的版面配置可能略有不同。  
  
## <a name="impact"></a>影響  

 此變更的結果：  
  
- 項目寬度或高度的增減最多不超過一個像素。  
  
- 物件的位置的位最多不超過一個像素。  
  
- 置中項目的垂直或水平位移最多不超過一個像素。  
  
 預設只有以 .NET Framework 4.6 為目標的應用程式才會啟用此新版面配置。  
  
## <a name="mitigation"></a>降低  

 由於此修改會停用高 DPI 之 WPF 控制項右側或底端的裁剪功能，因此，應用程式若是以舊版 .NET Framework 為目標，但要在 .NET Framework 4.6 上執行，可將下行加入 app.config 檔案中的 `<runtime>` 區段來選擇使用此新行為：  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 應用程式若是以 .NET Framework 4.6 為目標，但想使用先前的配置演算法來呈現 WPF 控制項，可將下行加入 app.config 檔案中的 `<runtime>` 區段，以執行此作業：  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>另請參閱

- [應用程式相容性](application-compatibility.md)
