---
title: 風險降低︰路徑正規化
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 1e7b540975b84320d099ca004df5b6a87aa60f6a
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457893"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="5512a-102">風險降低︰路徑正規化</span><span class="sxs-lookup"><span data-stu-id="5512a-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="5512a-103">從以 .NET Framework 4.6.2 為目標的應用程式開始，.NET Framework 中的路徑正規化已有所變更。</span><span class="sxs-lookup"><span data-stu-id="5512a-103">Starting with apps the target  the .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="5512a-104">路徑正規化是什麼？</span><span class="sxs-lookup"><span data-stu-id="5512a-104">What is path normalization?</span></span>  
 <span data-ttu-id="5512a-105">路徑正規化牽涉到修改識別路徑或檔案的字串，使其符合目標作業系統上的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="5512a-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="5512a-106">正規化通常牽涉到︰</span><span class="sxs-lookup"><span data-stu-id="5512a-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="5512a-107">規範化元件和目錄分隔符號。</span><span class="sxs-lookup"><span data-stu-id="5512a-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="5512a-108">將目前的目錄套用到相對路徑。</span><span class="sxs-lookup"><span data-stu-id="5512a-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="5512a-109">評估路徑中的相對目錄 (`.`) 或上層目錄 (`..`)。</span><span class="sxs-lookup"><span data-stu-id="5512a-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="5512a-110">修剪指定的字元。</span><span class="sxs-lookup"><span data-stu-id="5512a-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="5512a-111">變更</span><span class="sxs-lookup"><span data-stu-id="5512a-111">The changes</span></span>  
 <span data-ttu-id="5512a-112">從以 .NET Framework 4.6.2 為目標的應用程式開始，路徑正規化在下列方面已有所變更：</span><span class="sxs-lookup"><span data-stu-id="5512a-112">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="5512a-113">執行階段會延後至作業系統的 [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) 函式再進行路徑正規化。</span><span class="sxs-lookup"><span data-stu-id="5512a-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="5512a-114">正規化不再涉及修剪目錄區段的結尾 (例如目錄名稱結尾的空格)。</span><span class="sxs-lookup"><span data-stu-id="5512a-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="5512a-115">支援完全信任的裝置路徑語法，包括 `\\.\` 以及適用於 mscorlib.dll 中之檔案 I/O API 的 `\\?\`。</span><span class="sxs-lookup"><span data-stu-id="5512a-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="5512a-116">執行階段不會驗證裝置語法路徑。</span><span class="sxs-lookup"><span data-stu-id="5512a-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="5512a-117">支援使用裝置語法存取替代資料流。</span><span class="sxs-lookup"><span data-stu-id="5512a-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="5512a-118">影響</span><span class="sxs-lookup"><span data-stu-id="5512a-118">Impact</span></span>  

<span data-ttu-id="5512a-119">對於以 .NET Framework 4.6.2 或更新版本為目標的應用程式，這些變更預設為開啟。</span><span class="sxs-lookup"><span data-stu-id="5512a-119">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="5512a-120">它們應該可以改善效能，同時允許方法存取先前無法存取的路徑。</span><span class="sxs-lookup"><span data-stu-id="5512a-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="5512a-121">此變更不會影響以 .NET Framework 4.6.1 和舊版為目標但執行於 .NET Framework 4.6.2 或更新版本下的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5512a-121">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="5512a-122">風險降低</span><span class="sxs-lookup"><span data-stu-id="5512a-122">Mitigation</span></span>  
 <span data-ttu-id="5512a-123">以 .NET Framework 4.6.2 或更新版本為目標的應用程式，可透過在應用程式組態檔的[\<執行階段>](../configure-apps/file-schema/runtime/runtime-element.md) 區段中新增下列內容來選擇退出此變更，並使用舊版行為：</span><span class="sxs-lookup"><span data-stu-id="5512a-123">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
<span data-ttu-id="5512a-124">以 .NET Framework 4.6.1 或更早版本為目標，但在 .NET Framework 4.6.2 或更新版本上執行的應用程式，可以藉由在應用程式組態檔的[\<執行階段>](../configure-apps/file-schema/runtime/runtime-element.md) 區段新增下行，就能啟用路徑正規化的變更：</span><span class="sxs-lookup"><span data-stu-id="5512a-124">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5512a-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="5512a-125">See also</span></span>

- [<span data-ttu-id="5512a-126">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="5512a-126">Application compatibility</span></span>](application-compatibility.md)
