---
ms.openlocfilehash: 416590c7bd959eea011b7e7c5db48f22d349d0f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615620"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a><span data-ttu-id="8fc62-101">透過 ClickOnce 發行的應用程式，這些應用程式使用可能會在 Windows 2003 上失敗的 SHA-256 程式碼簽署憑證</span><span class="sxs-lookup"><span data-stu-id="8fc62-101">Apps published with ClickOnce that use a SHA-256 code-signing certificate may fail on Windows 2003</span></span>

#### <a name="details"></a><span data-ttu-id="8fc62-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8fc62-102">Details</span></span>

<span data-ttu-id="8fc62-103">這個可執行檔使用 SHA256 簽署。</span><span class="sxs-lookup"><span data-stu-id="8fc62-103">The executable is signed with SHA256.</span></span> <span data-ttu-id="8fc62-104">之前，不論程式碼簽署憑證為 SHA-1 或 SHA-256，都會使用 SHA1 簽署。</span><span class="sxs-lookup"><span data-stu-id="8fc62-104">Previously, it was signed with SHA1 regardless of whether the code-signing certificate was SHA-1 or SHA-256.</span></span> <span data-ttu-id="8fc62-105">這適用於：</span><span class="sxs-lookup"><span data-stu-id="8fc62-105">This applies to:</span></span>

- <span data-ttu-id="8fc62-106">使用 Visual Studio 2012 (含) 以後版本建置的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="8fc62-106">All applications built with Visual Studio 2012 or later.</span></span>
- <span data-ttu-id="8fc62-107">使用 Visual Studio 2010 (含) 以前版本，在具有 .NET Framework 4.5 的系統上建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="8fc62-107">Applications built with Visual Studio 2010 or earlier on systems with the .NET Framework 4.5 present.</span></span>
<span data-ttu-id="8fc62-108">此外，如果有 .NET Framework 4.5 (含) 以後版本，也會針對 SHA-256 憑證使用 SHA-256 來簽署 ClickOnce 資訊清單，而不論編譯的 .NET Framework 版本為何。</span><span class="sxs-lookup"><span data-stu-id="8fc62-108">In addition, if the .NET Framework 4.5 or later is present, the ClickOnce manifest is also signed with SHA-256 for SHA-256 certificates regardless of the .NET Framework version against which it was compiled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8fc62-109">建議</span><span class="sxs-lookup"><span data-stu-id="8fc62-109">Suggestion</span></span>

<span data-ttu-id="8fc62-110">對簽署 ClickOnce 可執行檔所做的變更只會影響 Windows Server 2003 系統；這些變更需要安裝 KB 938397。</span><span class="sxs-lookup"><span data-stu-id="8fc62-110">The change in signing the ClickOnce executable affects only Windows Server 2003 systems; they require that KB 938397 be installed.</span></span> <span data-ttu-id="8fc62-111">對使用 SHA-256 簽署資訊清單所做的變更還會引進 .NET Framework 4.5 (含) 以後版本的執行階段相依性，即使應用程式是以 .NET Framework 4.0 (含) 以前版本為目標亦然。</span><span class="sxs-lookup"><span data-stu-id="8fc62-111">The change in signing the manifest with SHA-256 even when an app targets the .NET Framework 4.0 or earlier versions introduces a runtime dependency on the .NET Framework 4.5 or a later version.</span></span>

| <span data-ttu-id="8fc62-112">名稱</span><span class="sxs-lookup"><span data-stu-id="8fc62-112">Name</span></span>    | <span data-ttu-id="8fc62-113">值</span><span class="sxs-lookup"><span data-stu-id="8fc62-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8fc62-114">影響範圍</span><span class="sxs-lookup"><span data-stu-id="8fc62-114">Scope</span></span>   | <span data-ttu-id="8fc62-115">Edge</span><span class="sxs-lookup"><span data-stu-id="8fc62-115">Edge</span></span>        |
| <span data-ttu-id="8fc62-116">版本</span><span class="sxs-lookup"><span data-stu-id="8fc62-116">Version</span></span> | <span data-ttu-id="8fc62-117">4.5</span><span class="sxs-lookup"><span data-stu-id="8fc62-117">4.5</span></span>         |
| <span data-ttu-id="8fc62-118">類型</span><span class="sxs-lookup"><span data-stu-id="8fc62-118">Type</span></span>    | <span data-ttu-id="8fc62-119">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="8fc62-119">Retargeting</span></span> |
