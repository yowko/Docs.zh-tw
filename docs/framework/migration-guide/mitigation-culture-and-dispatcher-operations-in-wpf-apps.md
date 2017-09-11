---
title: "風險降低：WPF 應用程式中的文化特性和發送器作業"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 41fc52679884d547809f1c1e9f47e29eb668cb8e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-culture-and-dispatcher-operations-in-wpf-apps"></a><span data-ttu-id="66d77-102">風險降低：WPF 應用程式中的文化特性和發送器作業</span><span class="sxs-lookup"><span data-stu-id="66d77-102">Mitigation: Culture and Dispatcher Operations in WPF Apps</span></span>
<span data-ttu-id="66d77-103">在以 .NET Framework 4.6 和 .NET Framework 4.6.1 為目標的應用程式中，在 <xref:System.Windows.Threading.Dispatcher> 中對 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 屬性進行的變更，會於發送器作業結束時遺失。</span><span class="sxs-lookup"><span data-stu-id="66d77-103">In apps that target the .NET Framework 4.6 and the .NET Framework 4.6.1, changes to the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> properties that are made within a <xref:System.Windows.Threading.Dispatcher> are lost at the end of that dispatcher operation.</span></span> <span data-ttu-id="66d77-104">同樣地，在發送器作業之外對 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 所做的變更，可能不會在執行該作業時反映出來。</span><span class="sxs-lookup"><span data-stu-id="66d77-104">Similarly, changes to <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> made outside of a dispatcher operation may not be reflected when that operation executes.</span></span>  
  
 <span data-ttu-id="66d77-105">這是因為在 <xref:System.Threading.ExecutionContext> 中導致 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 的變更要儲存在執行內容中。</span><span class="sxs-lookup"><span data-stu-id="66d77-105">This is due to a change in <xref:System.Threading.ExecutionContext> that causes the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> to be stored in the execution context.</span></span> <span data-ttu-id="66d77-106">WPF 發送器作業會儲存用來開始作業的執行內容，並在作業完成時還原先前的內容。</span><span class="sxs-lookup"><span data-stu-id="66d77-106">WPF dispatcher operations store the execution context used to begin the operation and restore the previous context when the operation is completed.</span></span> <span data-ttu-id="66d77-107">因為 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 現在是該內容的一部分，所以在發送器作業內對其進行的變更不會保留到作業外。</span><span class="sxs-lookup"><span data-stu-id="66d77-107">Because <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> are now part of that context, changes to them within a dispatcher operation are not persisted outside of the operation.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="66d77-108">影響</span><span class="sxs-lookup"><span data-stu-id="66d77-108">Impact</span></span>  
 <span data-ttu-id="66d77-109">實務上，這表示對於 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 屬性的變更，可能不會在 WPF UI 回呼和 WPF 應用程式中其他程式碼之間流動。</span><span class="sxs-lookup"><span data-stu-id="66d77-109">Practically, this means that changes to the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> properties may not flow between WPF UI callbacks and other code in a WPF application.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="66d77-110">緩和</span><span class="sxs-lookup"><span data-stu-id="66d77-110">Mitigation</span></span>  
 <span data-ttu-id="66d77-111">受此變更影響的應用程式可透過下列任一種方式應變：</span><span class="sxs-lookup"><span data-stu-id="66d77-111">Apps affected by this change may work around it in either of two ways:</span></span>  
  
-   <span data-ttu-id="66d77-112">在欄位中儲存想要的 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 並在所有 <xref:System.Windows.Threading.Dispatcher> 作業主體 (包括 UI 事件回呼處理常式) 中檢查已設定正確的 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="66d77-112">By storing the desired <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> in a field and checking in all <xref:System.Windows.Threading.Dispatcher> operation bodies (including UI event callback handlers) that the correct <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> is set.</span></span>  
  
-   <span data-ttu-id="66d77-113">因為 <xref:System.Threading.ExecutionContext> 的變更只會影響以 .NET Framework 4.6 或 .NET Framework 4.6.1 為目標的 WPF 應用程式，所以只要以 .NET Framework 4.5.2 為目標或以 4.6.2 和之後的 .NET Framework 版本為目標，即可避開這項變更。</span><span class="sxs-lookup"><span data-stu-id="66d77-113">Because the change to <xref:System.Threading.ExecutionContext> only affects WPF apps that target the .NET Framework 4.6 or the .NET Framework 4.6.1, this change can be avoided by targeting the .NET Framework 4.5.2 or by targeting a version of the .NET Framework starting with 4.6.2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66d77-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66d77-114">See Also</span></span>  
 [<span data-ttu-id="66d77-115">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="66d77-115">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

