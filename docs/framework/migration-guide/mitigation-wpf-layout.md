---
title: "風險降低：WPF 版面配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1dcbe970281f3d9cf3b8ffe9adb543afc120ae6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="cdb09-102">風險降低：WPF 版面配置</span><span class="sxs-lookup"><span data-stu-id="cdb09-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="cdb09-103">WPF 控制項的版面配置可能略有不同。</span><span class="sxs-lookup"><span data-stu-id="cdb09-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="cdb09-104">影響</span><span class="sxs-lookup"><span data-stu-id="cdb09-104">Impact</span></span>  
 <span data-ttu-id="cdb09-105">此變更的結果：</span><span class="sxs-lookup"><span data-stu-id="cdb09-105">As a result of this change:</span></span>  
  
-   <span data-ttu-id="cdb09-106">項目寬度或高度的增減最多不超過一個像素。</span><span class="sxs-lookup"><span data-stu-id="cdb09-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
-   <span data-ttu-id="cdb09-107">物件的位置的位最多不超過一個像素。</span><span class="sxs-lookup"><span data-stu-id="cdb09-107">The placement of an object can move by at most one pixel.</span></span>  
  
-   <span data-ttu-id="cdb09-108">置中項目的垂直或水平位移最多不超過一個像素。</span><span class="sxs-lookup"><span data-stu-id="cdb09-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="cdb09-109">預設只有以 .NET Framework 4.6 為目標的應用程式才會啟用此新版面配置。</span><span class="sxs-lookup"><span data-stu-id="cdb09-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="cdb09-110">緩和</span><span class="sxs-lookup"><span data-stu-id="cdb09-110">Mitigation</span></span>  
 <span data-ttu-id="cdb09-111">由於此修改會停用高 DPI 之 WPF 控制項右側或底端的裁剪功能，因此，應用程式若是以舊版 .NET Framework 為目標，但要在 .NET Framework 4.6 上執行，可將下行加入 app.config 檔案中的 `<runtime>` 區段來選擇使用此新行為：</span><span class="sxs-lookup"><span data-stu-id="cdb09-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="cdb09-112">應用程式若是以 .NET Framework 4.6 為目標，但想使用先前的配置演算法來呈現 WPF 控制項，可將下行加入 app.config 檔案中的 `<runtime>` 區段，以執行此作業：</span><span class="sxs-lookup"><span data-stu-id="cdb09-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdb09-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="cdb09-113">See Also</span></span>  
 [<span data-ttu-id="cdb09-114">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="cdb09-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
