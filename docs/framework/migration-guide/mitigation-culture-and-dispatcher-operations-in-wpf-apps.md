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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1aee32c5c50c4ff4309f93bff270e6c3b3c8f7cc
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="mitigation-culture-and-dispatcher-operations-in-wpf-apps"></a>風險降低：WPF 應用程式中的文化特性和發送器作業
在以 .NET Framework 4.6 和 .NET Framework 4.6.1 為目標的應用程式中，在 <xref:System.Windows.Threading.Dispatcher> 中對 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 屬性進行的變更，會於發送器作業結束時遺失。 同樣地，在發送器作業之外對 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 所做的變更，可能不會在執行該作業時反映出來。  
  
 這是因為在 <xref:System.Threading.ExecutionContext> 中導致 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 的變更要儲存在執行內容中。 WPF 發送器作業會儲存用來開始作業的執行內容，並在作業完成時還原先前的內容。 因為 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 現在是該內容的一部分，所以在發送器作業內對其進行的變更不會保留到作業外。  
  
## <a name="impact"></a>影響  
 實務上，這表示對於 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 屬性的變更，可能不會在 WPF UI 回呼和 WPF 應用程式中其他程式碼之間流動。  
  
## <a name="mitigation"></a>緩和  
 受此變更影響的應用程式可透過下列任一種方式應變：  
  
-   在欄位中儲存想要的 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 並在所有 <xref:System.Windows.Threading.Dispatcher> 作業主體 (包括 UI 事件回呼處理常式) 中檢查已設定正確的 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>。  
  
-   因為 <xref:System.Threading.ExecutionContext> 的變更只會影響以 .NET Framework 4.6 或 .NET Framework 4.6.1 為目標的 WPF 應用程式，所以只要以 .NET Framework 4.5.2 為目標或以 4.6.2 和之後的 .NET Framework 版本為目標，即可避開這項變更。  
  
## <a name="see-also"></a>另請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
