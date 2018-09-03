---
title: 風險降低︰路徑正規化
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa31641cc325f15b9afe677038deb33c57e77fd1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43388348"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="697d4-102">風險降低︰路徑正規化</span><span class="sxs-lookup"><span data-stu-id="697d4-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="697d4-103">從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，.NET Framework 中的路徑正規化已有所變更。</span><span class="sxs-lookup"><span data-stu-id="697d4-103">Starting with apps the target  the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="697d4-104">路徑正規化是什麼？</span><span class="sxs-lookup"><span data-stu-id="697d4-104">What is path normalization?</span></span>  
 <span data-ttu-id="697d4-105">路徑正規化牽涉到修改識別路徑或檔案的字串，使其符合目標作業系統上的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="697d4-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="697d4-106">正規化通常牽涉到︰</span><span class="sxs-lookup"><span data-stu-id="697d4-106">Normalization typically involves:</span></span>  
  
-   <span data-ttu-id="697d4-107">規範化元件和目錄分隔符號。</span><span class="sxs-lookup"><span data-stu-id="697d4-107">Canonicalizing component and directory separators.</span></span>  
  
-   <span data-ttu-id="697d4-108">將目前的目錄套用到相對路徑。</span><span class="sxs-lookup"><span data-stu-id="697d4-108">Applying the current directory to a relative path.</span></span>  
  
-   <span data-ttu-id="697d4-109">評估路徑中的相對目錄 (`.`) 或上層目錄 (`..`)。</span><span class="sxs-lookup"><span data-stu-id="697d4-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
-   <span data-ttu-id="697d4-110">修剪指定的字元。</span><span class="sxs-lookup"><span data-stu-id="697d4-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="697d4-111">變更</span><span class="sxs-lookup"><span data-stu-id="697d4-111">The changes</span></span>  
 <span data-ttu-id="697d4-112">從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，路徑正規化在以下方面已有所變更：</span><span class="sxs-lookup"><span data-stu-id="697d4-112">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization has changed in the following ways:</span></span>  
  
-   <span data-ttu-id="697d4-113">執行階段會延後至作業系統的 [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) 函式再進行路徑正規化。</span><span class="sxs-lookup"><span data-stu-id="697d4-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
-   <span data-ttu-id="697d4-114">正規化不再涉及修剪目錄區段的結尾 (例如目錄名稱結尾的空格)。</span><span class="sxs-lookup"><span data-stu-id="697d4-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
-   <span data-ttu-id="697d4-115">支援完全信任的裝置路徑語法，包括 `\\.\` 以及適用於 mscorlib.dll 中之檔案 I/O API 的 `\\?\`。</span><span class="sxs-lookup"><span data-stu-id="697d4-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
-   <span data-ttu-id="697d4-116">執行階段不會驗證裝置語法路徑。</span><span class="sxs-lookup"><span data-stu-id="697d4-116">The runtime does not validate device syntax paths.</span></span>  
  
-   <span data-ttu-id="697d4-117">支援使用裝置語法存取替代資料流。</span><span class="sxs-lookup"><span data-stu-id="697d4-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="697d4-118">影響</span><span class="sxs-lookup"><span data-stu-id="697d4-118">Impact</span></span>  
 <span data-ttu-id="697d4-119">對於以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 或更新版本為目標的應用程式，這些變更預設為開啟。</span><span class="sxs-lookup"><span data-stu-id="697d4-119">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later, these changes are on  by default.</span></span> <span data-ttu-id="697d4-120">它們應該可以改善效能，同時允許方法存取先前無法存取的路徑。</span><span class="sxs-lookup"><span data-stu-id="697d4-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
 <span data-ttu-id="697d4-121">此變更不會影響以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和舊版為目標但執行於 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 或更新版本下的應用程式。</span><span class="sxs-lookup"><span data-stu-id="697d4-121">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions but are running under the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="697d4-122">緩和</span><span class="sxs-lookup"><span data-stu-id="697d4-122">Mitigation</span></span>  
 <span data-ttu-id="697d4-123">以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 或更新版本為目標的應用程式可透過在應用程式組態檔的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段加入下列內容來選擇退出此變更，以使用舊版正規化：</span><span class="sxs-lookup"><span data-stu-id="697d4-123">Apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 <span data-ttu-id="697d4-124">以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 或舊版為目標但在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 或更新版本上執行的應用程式，只要在應用程式組態檔的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段加入下列程式行，就能啟用路徑正規化的變更：</span><span class="sxs-lookup"><span data-stu-id="697d4-124">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or earlier but are running on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="697d4-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="697d4-125">See Also</span></span>  
 [<span data-ttu-id="697d4-126">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="697d4-126">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
