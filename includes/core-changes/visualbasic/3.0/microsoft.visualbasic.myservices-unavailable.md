---
ms.openlocfilehash: d207a937917da78f6b902ad8ca4f02fa9a46c2e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116345"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="c99df-101">Microsoft 中的類型.VisualBasic.MyServices 命名空間不可用</span><span class="sxs-lookup"><span data-stu-id="c99df-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="c99df-102">命名空間中<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>的類型不可用。</span><span class="sxs-lookup"><span data-stu-id="c99df-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c99df-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="c99df-103">Version introduced</span></span>

<span data-ttu-id="c99df-104">.NET 核心 3.0 預覽 8</span><span class="sxs-lookup"><span data-stu-id="c99df-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="c99df-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="c99df-105">Change description</span></span>

<span data-ttu-id="c99df-106">命名空間中<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>的類型在某些 .NET Core 3.0 預覽版本中可用。</span><span class="sxs-lookup"><span data-stu-id="c99df-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="c99df-107">它們不再可用，從 .NET 核心 3.0 預覽 9 開始。</span><span class="sxs-lookup"><span data-stu-id="c99df-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="c99df-108">已刪除這些類型，以避免不必要的程式集依賴關係或後續版本中的中斷更改。</span><span class="sxs-lookup"><span data-stu-id="c99df-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c99df-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c99df-109">Recommended action</span></span>

<span data-ttu-id="c99df-110">如果您的代碼取決於**Microsoft.VisualBasic.MyServices**類型及其成員的使用，則 .NET 類庫中有相應的類型和成員。</span><span class="sxs-lookup"><span data-stu-id="c99df-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="c99df-111">以下是**Microsoft.VisualBasic.MyServices**的映射，其等效的 .NET 類庫類型：</span><span class="sxs-lookup"><span data-stu-id="c99df-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="c99df-112">微軟.視覺基礎.我的服務類型</span><span class="sxs-lookup"><span data-stu-id="c99df-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="c99df-113">.NET 類庫類型</span><span class="sxs-lookup"><span data-stu-id="c99df-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="c99df-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType>對於 WPF<xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType>應用程式，用於 Windows 表單應用程式</span><span class="sxs-lookup"><span data-stu-id="c99df-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="c99df-115">命名空間中<xref:System.IO>的類型</span><span class="sxs-lookup"><span data-stu-id="c99df-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="c99df-116">命名空間中的<xref:Microsoft.Win32>註冊表相關類型</span><span class="sxs-lookup"><span data-stu-id="c99df-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="c99df-117">類別</span><span class="sxs-lookup"><span data-stu-id="c99df-117">Category</span></span>

<span data-ttu-id="c99df-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c99df-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c99df-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c99df-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
