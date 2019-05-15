---
title: 風險降低：產品版本控制
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e75b838a2c6126fe82e97faac624a9ad6b7ea132
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626222"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="598cc-102">風險降低：產品版本控制</span><span class="sxs-lookup"><span data-stu-id="598cc-102">Mitigation: Product Versioning</span></span>
<span data-ttu-id="598cc-103">在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 和更新版本中，舊版 .NET Framework (.NET Framework 4、4.5、4.5.1 和 4.5.2) 的產品版本均有所變更。</span><span class="sxs-lookup"><span data-stu-id="598cc-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>  
  
## <a name="product-versioning-changes"></a><span data-ttu-id="598cc-104">產品版本變更</span><span class="sxs-lookup"><span data-stu-id="598cc-104">Product versioning changes</span></span>  
 <span data-ttu-id="598cc-105">以下是詳細的變更：</span><span class="sxs-lookup"><span data-stu-id="598cc-105">The following are the detailed changes:</span></span>  
  
- <span data-ttu-id="598cc-106">`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` 機碼中的 `Version` 項目值已變更為 `4.6.`*xxxxx* (.NET Framework 4.6 及其點發行版本)，以及 `4.7.`*xxxxx* (.NET Framework 4.7)。</span><span class="sxs-lookup"><span data-stu-id="598cc-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="598cc-107">在 .NET Framework 4.5、4.5.1 和 4.5.2 中，其格式為 `4.5.`*xxxxx*。</span><span class="sxs-lookup"><span data-stu-id="598cc-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>  
  
- <span data-ttu-id="598cc-108">.NET Framework 檔案的檔案和產品版本已從舊版配置 `4.0.30319.x` 變更為 `4.6.X.0` (.NET Framework 4.6 及其點發行版本)，以及 `4.7.X.0` (.NET Framework 4.7 及其點發行版本)。</span><span class="sxs-lookup"><span data-stu-id="598cc-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="598cc-109">當您以滑鼠右鍵按一下檔案後再檢視檔案的 [屬性] 時，會看到這些新值。</span><span class="sxs-lookup"><span data-stu-id="598cc-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>  
  
- <span data-ttu-id="598cc-110">Managed 組件的 <xref:System.Reflection.AssemblyFileVersionAttribute> 和 <xref:System.Reflection.AssemblyInformationalVersionAttribute> 屬性，對於 .NET Framework 4.6 及其點版本，其 <xref:System.Version> 值的格式為 `4.6.X.0`，對於 .NET Framework 4.7，格式則為 `4.7.X.0`。</span><span class="sxs-lookup"><span data-stu-id="598cc-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>  
  
- <span data-ttu-id="598cc-111">在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]、4.6.1、4.6.2 和 4.7 中，<xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性會傳回固定的版本字串 `4.0.30319.42000`。</span><span class="sxs-lookup"><span data-stu-id="598cc-111">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2, and 4.7, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="598cc-112">在 .NET Framework 4、4.5、4.5.1 和 4.5.2 中，其會以 `4.0.30319.xxxxx` 格式傳回版本字串 (例如 "4.0.30319.18010")。</span><span class="sxs-lookup"><span data-stu-id="598cc-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="598cc-113">請注意，建議應用程式程式碼與 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性有任何新的相依性。</span><span class="sxs-lookup"><span data-stu-id="598cc-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>  
  
### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="598cc-114">處理產品版本變更</span><span class="sxs-lookup"><span data-stu-id="598cc-114">Handling the product versioning changes</span></span>  
 <span data-ttu-id="598cc-115">一般而言，應用程式需要具備可偵測 .NET Framework 的執行階段版本和安裝目錄等項目的建議技術：</span><span class="sxs-lookup"><span data-stu-id="598cc-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>  
  
- <span data-ttu-id="598cc-116">若要偵測 .NET Framework 的執行階段版本，請參閱[如何：判斷安裝的 .NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="598cc-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>  
  
- <span data-ttu-id="598cc-117">若要判斷 .NET Framework 的安裝路徑，請使用 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` 機碼中的 `InstallPath` 項目值。</span><span class="sxs-lookup"><span data-stu-id="598cc-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="598cc-118">子機碼名稱是 `NET Framework Setup`，不是 `.NET Framework Setup`。</span><span class="sxs-lookup"><span data-stu-id="598cc-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>  
  
- <span data-ttu-id="598cc-119">若要判斷 .NET Framework Common Language Runtime 的目錄路徑，請呼叫 <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="598cc-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="598cc-120">若要取得 CLR 版本，請呼叫 <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="598cc-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="598cc-121">針對 .NET Framework 4 及其點發行版本 (.NET Framework 4.5、4.5.1、4.5.2 以及 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]、4.6.1、4.6.2 和 4.7)，該方法會傳回字串 `v4.0.30319`。</span><span class="sxs-lookup"><span data-stu-id="598cc-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="598cc-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="598cc-122">See also</span></span>

- [<span data-ttu-id="598cc-123">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="598cc-123">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
