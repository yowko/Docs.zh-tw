---
title: 風險降低：WPF 版面配置
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 7a074698fd203d0c5f9b799bfee8a6a9cb40800e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457777"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="2ca30-102">風險降低：WPF 版面配置</span><span class="sxs-lookup"><span data-stu-id="2ca30-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="2ca30-103">WPF 控制項的版面配置可能略有不同。</span><span class="sxs-lookup"><span data-stu-id="2ca30-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="2ca30-104">影響</span><span class="sxs-lookup"><span data-stu-id="2ca30-104">Impact</span></span>  
 <span data-ttu-id="2ca30-105">此變更的結果：</span><span class="sxs-lookup"><span data-stu-id="2ca30-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="2ca30-106">項目寬度或高度的增減最多不超過一個像素。</span><span class="sxs-lookup"><span data-stu-id="2ca30-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="2ca30-107">物件的位置的位最多不超過一個像素。</span><span class="sxs-lookup"><span data-stu-id="2ca30-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="2ca30-108">置中項目的垂直或水平位移最多不超過一個像素。</span><span class="sxs-lookup"><span data-stu-id="2ca30-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="2ca30-109">預設只有以 .NET Framework 4.6 為目標的應用程式才會啟用此新版面配置。</span><span class="sxs-lookup"><span data-stu-id="2ca30-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="2ca30-110">風險降低</span><span class="sxs-lookup"><span data-stu-id="2ca30-110">Mitigation</span></span>  
 <span data-ttu-id="2ca30-111">由於此修改會停用高 DPI 之 WPF 控制項右側或底端的裁剪功能，因此，應用程式若是以舊版 .NET Framework 為目標，但要在 .NET Framework 4.6 上執行，可將下行加入 app.config 檔案中的 `<runtime>` 區段來選擇使用此新行為：</span><span class="sxs-lookup"><span data-stu-id="2ca30-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="2ca30-112">應用程式若是以 .NET Framework 4.6 為目標，但想使用先前的配置演算法來呈現 WPF 控制項，可將下行加入 app.config 檔案中的 `<runtime>` 區段，以執行此作業：</span><span class="sxs-lookup"><span data-stu-id="2ca30-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ca30-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="2ca30-113">See also</span></span>

- [<span data-ttu-id="2ca30-114">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="2ca30-114">Application compatibility</span></span>](application-compatibility.md)
