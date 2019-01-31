---
title: 風險降低：圖示物件中的 PNG 畫面格
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d67b2fac0c1d55bfa5594e90998d9613de4ad271
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659783"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>風險降低：圖示物件中的 PNG 畫面格
從 .NET Framework 4.6 開始， <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 方法可將具有 PNG 畫面格的圖示成功轉換成 <xref:System.Drawing.Bitmap> 物件。  
  
 在以 .NET Framework 4.5.2 (含) 之前版本為目標的應用程式中，如果 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 物件具有 PNG 畫面格， <xref:System.ArgumentOutOfRangeException> 方法會擲回 <xref:System.Drawing.Icon> 例外狀況。  
  
## <a name="impact"></a>影響  
 這項變更會影響重新撰寫之以 .NET Framework 4.6 為目標的應用程式，以及針對 <xref:System.ArgumentOutOfRangeException> 物件具有 PNG 畫面格時所擲回的 <xref:System.Drawing.Icon> 實作特殊處理的應用程式。 以 .NET Framework 4.6 執行時，轉換會成功，且不再擲回 <xref:System.ArgumentOutOfRangeException> ，因此不會再叫用例外狀況處理常式。  
  
### <a name="mitigation"></a>緩和  
 如果不需要這項行為，您可以將下列元素加入至 app.config 檔案的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，以保留舊版行為：  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 如果 app.config 檔案已經包含 `AppContextSwitchOverrides` 元素，則應以下列程式碼將新值與 `value` 屬性合併：  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>另請參閱
- [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
