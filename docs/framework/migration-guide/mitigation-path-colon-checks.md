---
title: 風險降低︰路徑冒號檢查
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: ee71f6ef1e70509e772aee2cc75d00c33122a92e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126224"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="ddd50-102">風險降低︰路徑冒號檢查</span><span class="sxs-lookup"><span data-stu-id="ddd50-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="ddd50-103">從以 .NET Framework 4.6.2 為目標的應用程式開始，為了支援先前不支援的路徑 (就長度和格式兩方面) 而有數項變更。</span><span class="sxs-lookup"><span data-stu-id="ddd50-103">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="ddd50-104">特別是提供更正確的適當磁碟機分隔符號語法 (冒號) 檢查。</span><span class="sxs-lookup"><span data-stu-id="ddd50-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ddd50-105">影響</span><span class="sxs-lookup"><span data-stu-id="ddd50-105">Impact</span></span>  
 <span data-ttu-id="ddd50-106">這些變更會封鎖 <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> 和 <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> 方法先前支援的一些 URI 路徑。</span><span class="sxs-lookup"><span data-stu-id="ddd50-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ddd50-107">風險降低</span><span class="sxs-lookup"><span data-stu-id="ddd50-107">Mitigation</span></span>  
 <span data-ttu-id="ddd50-108">若要解決 <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> 和 <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> 方法不再支援的先前可接受路徑問題，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ddd50-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="ddd50-109">從 URL 手動移除配置。</span><span class="sxs-lookup"><span data-stu-id="ddd50-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="ddd50-110">例如，從 URL 移除 `file://`。</span><span class="sxs-lookup"><span data-stu-id="ddd50-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="ddd50-111">將 URI 傳遞給 <xref:System.Uri> 建構函式，並擷取 <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ddd50-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="ddd50-112">藉由將 `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> 參數設定為 `true`，以選擇退出新的路徑正規化。</span><span class="sxs-lookup"><span data-stu-id="ddd50-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ddd50-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="ddd50-113">See also</span></span>

- [<span data-ttu-id="ddd50-114">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="ddd50-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-2.md)
