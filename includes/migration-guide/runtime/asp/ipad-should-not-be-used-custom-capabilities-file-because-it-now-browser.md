---
ms.openlocfilehash: 84f570cbbd97be79426e117d4c97ec182a397fd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379692"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a><span data-ttu-id="72282-101">IPad 不應用於自訂功能檔案，因為現在它是一種瀏覽器功能</span><span class="sxs-lookup"><span data-stu-id="72282-101">IPad should not be used in custom capabilities file because it is now a browser capability</span></span>

|   |   |
|---|---|
|<span data-ttu-id="72282-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="72282-102">Details</span></span>|<span data-ttu-id="72282-103">從 .NET Framework 4.5 開始，iPad 是預設 ASP.NET 瀏覽器功能檔案中的識別碼，所以不應將其用於自訂功能檔案</span><span class="sxs-lookup"><span data-stu-id="72282-103">Beginning in .NET Framework 4.5, iPad is an identifier in the default ASP.NET browser capabilities file, so it should not be used in a custom capabilities file</span></span>|
|<span data-ttu-id="72282-104">建議</span><span class="sxs-lookup"><span data-stu-id="72282-104">Suggestion</span></span>|<span data-ttu-id="72282-105">如果需要 iPad 特定功能，則必須以修改 iPad 行為，方法是在預先定義的閘道 refID &quot;IPad&quot; 上設定功能　，而不是透過使用者代理程式比對產生新的 &quot;IPad&quot; 識別碼。</span><span class="sxs-lookup"><span data-stu-id="72282-105">If iPad-specific capabilities are required, it is necessary to modify iPad behavior by setting capabilities on the pre-defined gateway refID &quot;IPad&quot; instead of by generating a new &quot;IPad&quot; ID by user agent matching.</span></span>|
|<span data-ttu-id="72282-106">範圍</span><span class="sxs-lookup"><span data-stu-id="72282-106">Scope</span></span>|<span data-ttu-id="72282-107">Edge</span><span class="sxs-lookup"><span data-stu-id="72282-107">Edge</span></span>|
|<span data-ttu-id="72282-108">版本</span><span class="sxs-lookup"><span data-stu-id="72282-108">Version</span></span>|<span data-ttu-id="72282-109">4.5</span><span class="sxs-lookup"><span data-stu-id="72282-109">4.5</span></span>|
|<span data-ttu-id="72282-110">類型</span><span class="sxs-lookup"><span data-stu-id="72282-110">Type</span></span>|<span data-ttu-id="72282-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="72282-111">Runtime</span></span>|
