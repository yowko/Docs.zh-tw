---
title: "風險降低︰長路徑支援"
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
ms.assetid: 3cbe2d77-6e2c-4665-a6c5-7000b9ad6890
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 138e96c3d45b79ccf30f6a3d39f0af26a48c0117
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-long-path-support"></a><span data-ttu-id="6fa4c-102">風險降低︰長路徑支援</span><span class="sxs-lookup"><span data-stu-id="6fa4c-102">Mitigation: Long Path Support</span></span>
<span data-ttu-id="6fa4c-103">從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，如果路徑或完整檔案名稱超過 260 (或 `MAX_PATH`) 個字元，檔案系統 I/O 方法不會再自動擲回 <xref:System.IO.PathTooLongException>。</span><span class="sxs-lookup"><span data-stu-id="6fa4c-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)],  file system I/O methods not longer automatically throw a <xref:System.IO.PathTooLongException> if a path or fully qualified file name exceeds 260 (or `MAX_PATH`) characters.</span></span> <span data-ttu-id="6fa4c-104">現在可支援長達 32K 個字元的長路徑。</span><span class="sxs-lookup"><span data-stu-id="6fa4c-104">Instead, long paths of up to 32K characters are supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="6fa4c-105">影響</span><span class="sxs-lookup"><span data-stu-id="6fa4c-105">Impact</span></span>  
 <span data-ttu-id="6fa4c-106">重新編譯為以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式和先前因為路徑超過 260 個字元而自動擲回 <xref:System.IO.PathTooLongException> 的應用程式，現在只有在下列情況下才會擲回 <xref:System.IO.PathTooLongException>：</span><span class="sxs-lookup"><span data-stu-id="6fa4c-106">Apps recompiled to target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] and that previously threw a <xref:System.IO.PathTooLongException> automatically because a path exceeded 260 characters will now throw a <xref:System.IO.PathTooLongException> only under the following conditions:</span></span>  
  
-   <span data-ttu-id="6fa4c-107">路徑的長度大於 <xref:System.Int16.MaxValue?displayProperty=fullName> (32,767) 個字元。</span><span class="sxs-lookup"><span data-stu-id="6fa4c-107">The length of the path is greater than  <xref:System.Int16.MaxValue?displayProperty=fullName> (32,767) characters.</span></span>  
  
-   <span data-ttu-id="6fa4c-108">作業系統傳回 `COR_E_PATHTOOLONG` 或其對應項。</span><span class="sxs-lookup"><span data-stu-id="6fa4c-108">The operating system returns `COR_E_PATHTOOLONG` or its equivalent.</span></span>  
  
 <span data-ttu-id="6fa4c-109">以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和更舊版本為目標之應用程式的舊行為，是每當路徑超過 260 個字元時，執行階段就會自動擲回 <xref:System.IO.PathTooLongException>。</span><span class="sxs-lookup"><span data-stu-id="6fa4c-109">The legacy behavior for apps that target the[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier is that the runtime automatically throws a <xref:System.IO.PathTooLongException> whenever a path exceeds 260 characters.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="6fa4c-110">緩和</span><span class="sxs-lookup"><span data-stu-id="6fa4c-110">Mitigation</span></span>  
 <span data-ttu-id="6fa4c-111">對於以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式，如果不需要長路徑支援，您可以透過將下列內容加入至 app.config 檔案的 [\<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段以選擇退出︰</span><span class="sxs-lookup"><span data-stu-id="6fa4c-111">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], you can opt out of long path support if it is not desirable by adding the following to    to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />   
</runtime>  
```  
  
 <span data-ttu-id="6fa4c-112">對於以舊版 .NET Framework 為目標但卻在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 或更新版本上執行的應用程式，則可將下列內容加入至 app.config 檔案的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，以選擇加入長路徑支援：</span><span class="sxs-lookup"><span data-stu-id="6fa4c-112">For apps that target earlier versions of the .NET Framework but run on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later., you can opt in to long path support by adding the following to    to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6fa4c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fa4c-113">See Also</span></span>  
 [<span data-ttu-id="6fa4c-114">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="6fa4c-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)

