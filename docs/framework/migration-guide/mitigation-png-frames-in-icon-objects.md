---
title: 緩和：圖示物件中的 PNG 畫面格
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: 1a4ae0c069a4cd6d53bce77e64822ebf3fbb5361
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457877"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="92fd2-102">緩和：圖示物件中的 PNG 畫面格</span><span class="sxs-lookup"><span data-stu-id="92fd2-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="92fd2-103">從 .NET Framework 4.6 開始， <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 方法可將具有 PNG 畫面格的圖示成功轉換成 <xref:System.Drawing.Bitmap> 物件。</span><span class="sxs-lookup"><span data-stu-id="92fd2-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="92fd2-104">在以 .NET Framework 4.5.2 (含) 之前版本為目標的應用程式中，如果 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 物件具有 PNG 畫面格， <xref:System.ArgumentOutOfRangeException> 方法會擲回 <xref:System.Drawing.Icon> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="92fd2-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="92fd2-105">影響</span><span class="sxs-lookup"><span data-stu-id="92fd2-105">Impact</span></span>  
 <span data-ttu-id="92fd2-106">這項變更會影響重新撰寫之以 .NET Framework 4.6 為目標的應用程式，以及針對 <xref:System.ArgumentOutOfRangeException> 物件具有 PNG 畫面格時所擲回的 <xref:System.Drawing.Icon> 實作特殊處理的應用程式。</span><span class="sxs-lookup"><span data-stu-id="92fd2-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="92fd2-107">以 .NET Framework 4.6 執行時，轉換會成功，且不再擲回 <xref:System.ArgumentOutOfRangeException> ，因此不會再叫用例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="92fd2-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="92fd2-108">風險降低</span><span class="sxs-lookup"><span data-stu-id="92fd2-108">Mitigation</span></span>  
 <span data-ttu-id="92fd2-109">如果不需要這項行為，您可以將下列元素加入至 app.config 檔案的 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 區段，以保留舊版行為：</span><span class="sxs-lookup"><span data-stu-id="92fd2-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="92fd2-110">如果 app.config 檔案已經包含 `AppContextSwitchOverrides` 元素，則應以下列程式碼將新值與 `value` 屬性合併：</span><span class="sxs-lookup"><span data-stu-id="92fd2-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="92fd2-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="92fd2-111">See also</span></span>

- [<span data-ttu-id="92fd2-112">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="92fd2-112">Application compatibility</span></span>](application-compatibility.md)
