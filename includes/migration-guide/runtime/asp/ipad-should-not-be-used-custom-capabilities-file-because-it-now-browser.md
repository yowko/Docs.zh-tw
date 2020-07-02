---
ms.openlocfilehash: af10716fe5f4c07091e8605cdf620e4a499fb1e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619941"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a><span data-ttu-id="f570d-101">IPad 不應用於自訂功能檔案，因為現在它是一種瀏覽器功能</span><span class="sxs-lookup"><span data-stu-id="f570d-101">IPad should not be used in custom capabilities file because it is now a browser capability</span></span>

#### <a name="details"></a><span data-ttu-id="f570d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f570d-102">Details</span></span>

<span data-ttu-id="f570d-103">從 .NET Framework 4.5 開始，iPad 是預設 ASP.NET 瀏覽器功能檔案中的識別碼，所以不應將其用於自訂功能檔案</span><span class="sxs-lookup"><span data-stu-id="f570d-103">Beginning in .NET Framework 4.5, iPad is an identifier in the default ASP.NET browser capabilities file, so it should not be used in a custom capabilities file</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f570d-104">建議</span><span class="sxs-lookup"><span data-stu-id="f570d-104">Suggestion</span></span>

<span data-ttu-id="f570d-105">如果需要 iPad 特定功能，則必須以修改 iPad 行為，方法是在預先定義的閘道 refID &quot;IPad&quot; 上設定功能　，而不是透過使用者代理程式比對產生新的 &quot;IPad&quot; 識別碼。</span><span class="sxs-lookup"><span data-stu-id="f570d-105">If iPad-specific capabilities are required, it is necessary to modify iPad behavior by setting capabilities on the pre-defined gateway refID &quot;IPad&quot; instead of by generating a new &quot;IPad&quot; ID by user agent matching.</span></span>

| <span data-ttu-id="f570d-106">名稱</span><span class="sxs-lookup"><span data-stu-id="f570d-106">Name</span></span>    | <span data-ttu-id="f570d-107">值</span><span class="sxs-lookup"><span data-stu-id="f570d-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f570d-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="f570d-108">Scope</span></span>   |<span data-ttu-id="f570d-109">Edge</span><span class="sxs-lookup"><span data-stu-id="f570d-109">Edge</span></span>|
|<span data-ttu-id="f570d-110">版本</span><span class="sxs-lookup"><span data-stu-id="f570d-110">Version</span></span>|<span data-ttu-id="f570d-111">4.5</span><span class="sxs-lookup"><span data-stu-id="f570d-111">4.5</span></span>|
|<span data-ttu-id="f570d-112">類型</span><span class="sxs-lookup"><span data-stu-id="f570d-112">Type</span></span>|<span data-ttu-id="f570d-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="f570d-113">Runtime</span></span>|
