---
title: "緩和：圖示物件中的 PNG 畫面格 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# 緩和：圖示物件中的 PNG 畫面格
從 .NET Framework 4.6 開始，<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> 方法可將具有 PNG 畫面格的圖示成功轉換成 <xref:System.Drawing.Bitmap> 物件。  
  
 在以 .NET Framework 4.5.2 \(含\) 之前版本為目標的應用程式中，如果 <xref:System.Drawing.Icon> 物件具有 PNG 畫面格，<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> 方法會擲回 <xref:System.ArgumentOutOfRangeException> 例外狀況。  
  
## 影響  
 這項變更會影響重新撰寫之以 .NET Framework 4.6 為目標的應用程式，以及針對 <xref:System.Drawing.Icon> 物件具有 PNG 畫面格時所擲回的 <xref:System.ArgumentOutOfRangeException> 實作特殊處理的應用程式。 以 .NET Framework 4.6 執行時，轉換會成功，且不再擲回 <xref:System.ArgumentOutOfRangeException>，因此不會再叫用例外狀況處理常式。  
  
### 緩和  
 如果不需要這項行為，您可以將下列項目加入 app.config 檔的 [\<runtime\>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，以保留舊版行為：  
  
```  
<AppContextSwitchOverrides value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
  
```  
  
 如果 app.config 檔已經包含 `AppContextSwitchOverrides` 項目，則應該如下所示將新值與 `value` 屬性合併：  
  
```  
<AppContextSwitchOverrides value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
  
```  
  
## 請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)