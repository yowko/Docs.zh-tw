---
title: 風險降低：產品版本
description: 在本文中，您將瞭解如何 .NET Framework 4.6 和更新版本的產品版本已從舊版變更。
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 442c06446e763758d3a150ee9ff884a616541c07
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475394"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="cc108-103">風險降低：產品版本</span><span class="sxs-lookup"><span data-stu-id="cc108-103">Mitigation: Product Versioning</span></span>

<span data-ttu-id="cc108-104">在 .NET Framework 4.6 和更新版本中，舊版 .NET Framework (.NET Framework 4、4.5、4.5.1 和 4.5.2) 的產品版本均有所變更。</span><span class="sxs-lookup"><span data-stu-id="cc108-104">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="cc108-105">產品版本變更</span><span class="sxs-lookup"><span data-stu-id="cc108-105">Product versioning changes</span></span>

<span data-ttu-id="cc108-106">以下是詳細的變更：</span><span class="sxs-lookup"><span data-stu-id="cc108-106">The following are the detailed changes:</span></span>

- <span data-ttu-id="cc108-107">`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` 機碼中的 `Version` 項目值已變更為 `4.6.`*xxxxx* (.NET Framework 4.6 及其點發行版本)，以及 `4.7.`*xxxxx* (.NET Framework 4.7)。</span><span class="sxs-lookup"><span data-stu-id="cc108-107">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="cc108-108">在 .NET Framework 4.5、4.5.1 和 4.5.2 中，其格式為 `4.5.`*xxxxx*。</span><span class="sxs-lookup"><span data-stu-id="cc108-108">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="cc108-109">.NET Framework 檔案的檔案和產品版本已從舊版配置 `4.0.30319.x` 變更為 `4.6.X.0` (.NET Framework 4.6 及其點發行版本)，以及 `4.7.X.0` (.NET Framework 4.7 及其點發行版本)。</span><span class="sxs-lookup"><span data-stu-id="cc108-109">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="cc108-110">在檔案上按一下滑鼠**右鍵之後，** 您就可以看到這些新值。</span><span class="sxs-lookup"><span data-stu-id="cc108-110">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="cc108-111">Managed 組件的 <xref:System.Reflection.AssemblyFileVersionAttribute> 和 <xref:System.Reflection.AssemblyInformationalVersionAttribute> 屬性，對於 .NET Framework 4.6 及其點版本，其 <xref:System.Version> 值的格式為 `4.6.X.0`，對於 .NET Framework 4.7，格式則為 `4.7.X.0`。</span><span class="sxs-lookup"><span data-stu-id="cc108-111">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="cc108-112">從 .NET Framework 4.6 開始，<xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性會傳回固定的版本字串 `4.0.30319.42000`。</span><span class="sxs-lookup"><span data-stu-id="cc108-112">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="cc108-113">在 .NET Framework 4、4.5、4.5.1 和 4.5.2 中，其會以 `4.0.30319.xxxxx` 格式傳回版本字串，其中 `xxxxx` 會小於 42000 (例如 "4.0.30319.18010")。</span><span class="sxs-lookup"><span data-stu-id="cc108-113">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="cc108-114">請注意，建議應用程式程式碼與 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性有任何新的相依性。</span><span class="sxs-lookup"><span data-stu-id="cc108-114">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="cc108-115">處理產品版本變更</span><span class="sxs-lookup"><span data-stu-id="cc108-115">Handling the product versioning changes</span></span>

<span data-ttu-id="cc108-116">一般而言，應用程式需要具備可偵測 .NET Framework 的執行階段版本和安裝目錄等項目的建議技術：</span><span class="sxs-lookup"><span data-stu-id="cc108-116">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="cc108-117">若要偵測 .NET Framework 的執行階段版本，請參閱[如何：判斷安裝的 .NET Framework 版本](how-to-determine-which-versions-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="cc108-117">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="cc108-118">若要判斷 .NET Framework 的安裝路徑，請使用 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` 機碼中的 `InstallPath` 項目值。</span><span class="sxs-lookup"><span data-stu-id="cc108-118">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="cc108-119">子機碼名稱是 `NET Framework Setup`，不是 `.NET Framework Setup`。</span><span class="sxs-lookup"><span data-stu-id="cc108-119">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="cc108-120">若要判斷 .NET Framework Common Language Runtime 的目錄路徑，請呼叫 <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="cc108-120">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="cc108-121">若要取得 CLR 版本，請呼叫 <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="cc108-121">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="cc108-122">針對 .NET Framework 4 及其點發行版本 (.NET Framework 4.5、4.5.1、4.5.2 以及 .NET Framework 4.6、4.6.1、4.6.2 和 4.7)，該方法會傳回字串 `v4.0.30319`。</span><span class="sxs-lookup"><span data-stu-id="cc108-122">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc108-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc108-123">See also</span></span>

- [<span data-ttu-id="cc108-124">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="cc108-124">Application compatibility</span></span>](application-compatibility.md)
