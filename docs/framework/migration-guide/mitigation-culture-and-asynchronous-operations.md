---
title: "風險降低：文化特性和非同步作業"
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
ms.assetid: d2cdb578-9923-47df-9ffd-5865333ac1a4
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: debcae8281c832d2815e1b9896fbbcb725c8ffc3
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-culture-and-asynchronous-operations"></a><span data-ttu-id="608d2-102">風險降低：文化特性和非同步作業</span><span class="sxs-lookup"><span data-stu-id="608d2-102">Mitigation: Culture and Asynchronous Operations</span></span>
<span data-ttu-id="608d2-103">對於以 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 和更新版本為目標的應用程式，<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 是儲存在執行緒的 <xref:System.Threading.ExecutionContext> 中，而它會在非同步作業之間流動。</span><span class="sxs-lookup"><span data-stu-id="608d2-103">For apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] and later versions, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> are stored in a thread's <xref:System.Threading.ExecutionContext>, which flows across asynchronous operations.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="608d2-104">影響</span><span class="sxs-lookup"><span data-stu-id="608d2-104">Impact</span></span>  
 <span data-ttu-id="608d2-105">基於這項變更，會在稍後非同步執行的工作中反映 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 變更。</span><span class="sxs-lookup"><span data-stu-id="608d2-105">As a result of this change, changes to the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> are reflected in tasks which are later run asynchronously.</span></span> <span data-ttu-id="608d2-106">這與舊版 .NET Framework 的行為不同，而舊版本會將 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 重設為所有非同步工作中的系統預設值。</span><span class="sxs-lookup"><span data-stu-id="608d2-106">This differs from the behavior of previous .NET Framework versions, which would reset <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> to the system default  in all asynchronous tasks.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="608d2-107">緩和</span><span class="sxs-lookup"><span data-stu-id="608d2-107">Mitigation</span></span>  
 <span data-ttu-id="608d2-108">受此變更影響的應用程式可透過下列任一種方式應變：</span><span class="sxs-lookup"><span data-stu-id="608d2-108">Apps affected by this change can work around it in either of two ways:</span></span>  
  
-   <span data-ttu-id="608d2-109">明確地將所需的 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 屬性設定為非同步工作的第一個作業。</span><span class="sxs-lookup"><span data-stu-id="608d2-109">By explicitly setting the desired <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> property as the first operation in an asynchronous task.</span></span>  
  
-   <span data-ttu-id="608d2-110">將下列 `AppContextSwitchOverrides` 項目新增至應用程式組態檔，以選擇未流動 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 的舊行為：</span><span class="sxs-lookup"><span data-stu-id="608d2-110">By opting into the old behavior of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> by adding the following `AppContextSwitchOverrides` element to the application's configuration file:</span></span>  
  
    ```xml  
    <configuration>  
        <runtime>  
            <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
        </runtime>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="608d2-111">以程式設計方式設定下列相容性參數，以選擇未流動 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 的舊行為：</span><span class="sxs-lookup"><span data-stu-id="608d2-111">By opting into the old behavior of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> by setting the following compatibility switch programatically:</span></span>  
  
    ```csharp  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);  
    ```  
  
    ```vb  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="608d2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="608d2-112">See Also</span></span>  
 [<span data-ttu-id="608d2-113">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="608d2-113">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

