---
title: 緩和：圖示物件中的 PNG 畫面格
description: 瞭解如何在 .NET Framework 4.6 和更新版本中所包含的新行為不需要時，設定圖示物件中的 PNG 框架行為。
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: a8bb4fca19a09f16c89ce8c5da08ebcae9a037ec
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276577"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>緩和：圖示物件中的 PNG 畫面格

從 .NET Framework 4.6 開始， <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 方法可將具有 PNG 畫面格的圖示成功轉換成 <xref:System.Drawing.Bitmap> 物件。  
  
 在以 .NET Framework 4.5.2 (含) 之前版本為目標的應用程式中，如果 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 物件具有 PNG 畫面格， <xref:System.ArgumentOutOfRangeException> 方法會擲回 <xref:System.Drawing.Icon> 例外狀況。  
  
## <a name="impact"></a>影響  

 這項變更會影響重新撰寫之以 .NET Framework 4.6 為目標的應用程式，以及針對 <xref:System.ArgumentOutOfRangeException> 物件具有 PNG 畫面格時所擲回的 <xref:System.Drawing.Icon> 實作特殊處理的應用程式。 以 .NET Framework 4.6 執行時，轉換會成功，且不再擲回 <xref:System.ArgumentOutOfRangeException> ，因此不會再叫用例外狀況處理常式。  
  
### <a name="mitigation"></a>降低  

 如果不想要這種行為，您可以將下列專案加入至 app.config 檔的區段，以保留先前的行為 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) ：  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 如果 app.config 檔已經包含 `AppContextSwitchOverrides` 項目，則應該如下所示將新值與 `value` 屬性合併：  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a>另請參閱

- [應用程式相容性](application-compatibility.md)
