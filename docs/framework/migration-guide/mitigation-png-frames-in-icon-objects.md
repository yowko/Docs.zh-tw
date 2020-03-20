---
title: 緩和：圖示物件中的 PNG 畫面格
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: d661e45bfbbe5e1c5ca5b7eb123e71aa32a096ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181213"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="b6c82-102">緩和：圖示物件中的 PNG 畫面格</span><span class="sxs-lookup"><span data-stu-id="b6c82-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="b6c82-103">從 .NET Framework 4.6 開始， <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 方法可將具有 PNG 畫面格的圖示成功轉換成 <xref:System.Drawing.Bitmap> 物件。</span><span class="sxs-lookup"><span data-stu-id="b6c82-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="b6c82-104">在以 .NET Framework 4.5.2 (含) 之前版本為目標的應用程式中，如果 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 物件具有 PNG 畫面格， <xref:System.ArgumentOutOfRangeException> 方法會擲回 <xref:System.Drawing.Icon> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b6c82-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b6c82-105">影響</span><span class="sxs-lookup"><span data-stu-id="b6c82-105">Impact</span></span>  
 <span data-ttu-id="b6c82-106">這項變更會影響重新撰寫之以 .NET Framework 4.6 為目標的應用程式，以及針對 <xref:System.ArgumentOutOfRangeException> 物件具有 PNG 畫面格時所擲回的 <xref:System.Drawing.Icon> 實作特殊處理的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b6c82-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="b6c82-107">以 .NET Framework 4.6 執行時，轉換會成功，且不再擲回 <xref:System.ArgumentOutOfRangeException> ，因此不會再叫用例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="b6c82-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="b6c82-108">降低</span><span class="sxs-lookup"><span data-stu-id="b6c82-108">Mitigation</span></span>  
 <span data-ttu-id="b6c82-109">如果此行為不可取，則可以通過將以下元素添加到應用的[\<運行時>](../configure-apps/file-schema/runtime/runtime-element.md)部分來保留以前的行為：</span><span class="sxs-lookup"><span data-stu-id="b6c82-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="b6c82-110">如果 app.config 檔已經包含 `AppContextSwitchOverrides` 項目，則應該如下所示將新值與 `value` 屬性合併：</span><span class="sxs-lookup"><span data-stu-id="b6c82-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6c82-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6c82-111">See also</span></span>

- [<span data-ttu-id="b6c82-112">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="b6c82-112">Application compatibility</span></span>](application-compatibility.md)
