---
title: "風險降低：WPF 應用程式中的文化特性和發送器作業 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 455c1452-8ce0-45ae-a092-21fb8edf1cac
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1aee32c5c50c4ff4309f93bff270e6c3b3c8f7cc
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-culture-and-dispatcher-operations-in-wpf-apps"></a>風險降低：WPF 應用程式中的文化特性和發送器作業
在以 .NET Framework 4.6 和 .NET Framework 4.6.1 為目標的應用程式中，於 <xref:System.Windows.Threading.Dispatcher> 之內所做的<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 屬性變更，會在發送器作業結束時遺失。 同樣地，在發送器作業之外所做的 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 變更，可能不會在執行該作業時反映出來。  
  
 這是 <xref:System.Threading.ExecutionContext> 有所變更，因而導致 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 儲存在執行內容。 WPF 發送器作業會儲存用來開始作業的執行內容，並在作業完成時還原先前的內容。 由於 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 現在已是該內容的一部分，它們在發送器作業內的變更不會反映到作業之外。  
  
## <a name="impact"></a>影響  
 實際上，這就表示對 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 屬性所做的變更，可能不會在 WPF UI 回呼和 WPF 應用程式中的其他程式碼之間流通。  
  
## <a name="mitigation"></a>緩和  
 受此變更影響的應用程式可透過下列任一種方式應變：  
  
-   將所需的 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 儲存在某個欄位，並檢查所有 <xref:System.Windows.Threading.Dispatcher> 作業主體 (包括 UI 事件回呼處理常式) 中是否都已設定正確的 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>。  
  
-   <xref:System.Threading.ExecutionContext> 的變更只會影響以 .NET Framework 4.6 或 .NET Framework 4.6.1 為目標的 WPF 應用程式，因此，只要以 .NET Framework 4.5.2 為目標或以 4.6.2 和之後的 .NET Framework 版本為目標，即可避開這項變更。  
  
## <a name="see-also"></a>另請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
