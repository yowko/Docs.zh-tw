---
ms.openlocfilehash: c0a281b05f453b68495e6fa6fca45f3f36a204a3
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "50746227"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a><span data-ttu-id="8bf4a-101">如果使用複合索引鍵，而且一個索引鍵為空白，XSD 結構描述驗證現在會正確地偵測唯一條件約束的違規</span><span class="sxs-lookup"><span data-stu-id="8bf4a-101">XSD Schema validation now correctly detects violations of unique constraints if compound keys are used and one key is empty</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8bf4a-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8bf4a-102">Details</span></span>|<span data-ttu-id="8bf4a-103">.NET Framework 4.6 之前的版本有錯誤 (bug)，會導致 XSD 驗證在其中一個索引鍵為空白時，無法偵測複合索引鍵上的唯一條件約束。</span><span class="sxs-lookup"><span data-stu-id="8bf4a-103">Versions of the .NET Framework prior to 4.6 had a bug that caused XSD validation to not detect unique constraints on compound keys if one of the keys was empty.</span></span> <span data-ttu-id="8bf4a-104">在 .NET Framework 4.6 中，已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="8bf4a-104">In the .NET Framework 4.6, this issue is corrected.</span></span> <span data-ttu-id="8bf4a-105">這會導致更正確的驗證，但也可能會導致之前可驗證的某些 XML 無法驗證。</span><span class="sxs-lookup"><span data-stu-id="8bf4a-105">This will result in more correct validation, but it may also result in some XML not validating which previously would have.</span></span>|
|<span data-ttu-id="8bf4a-106">建議</span><span class="sxs-lookup"><span data-stu-id="8bf4a-106">Suggestion</span></span>|<span data-ttu-id="8bf4a-107">如果需要較鬆散的 .NET Framework 4.0 驗證，正在驗證的應用程式可以將目標設為 .NET Framework 4.5 版 (或舊版)。</span><span class="sxs-lookup"><span data-stu-id="8bf4a-107">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.5 (or earlier) of the .NET Framework.</span></span> <span data-ttu-id="8bf4a-108">不過，重定目標為 .NET Framework 4.6 時，應完成程式碼檢閱，以確保重複的複合索引鍵 (如本問題說明中所述) 不會導致無效。</span><span class="sxs-lookup"><span data-stu-id="8bf4a-108">When retargeting to .NET Framework 4.6, however, code review should be done to be sure that duplicate compound keys (as described in this issue's description) are not expected to validate.</span></span>|
|<span data-ttu-id="8bf4a-109">範圍</span><span class="sxs-lookup"><span data-stu-id="8bf4a-109">Scope</span></span>|<span data-ttu-id="8bf4a-110">Edge</span><span class="sxs-lookup"><span data-stu-id="8bf4a-110">Edge</span></span>|
|<span data-ttu-id="8bf4a-111">版本</span><span class="sxs-lookup"><span data-stu-id="8bf4a-111">Version</span></span>|<span data-ttu-id="8bf4a-112">4.6</span><span class="sxs-lookup"><span data-stu-id="8bf4a-112">4.6</span></span>|
|<span data-ttu-id="8bf4a-113">類型</span><span class="sxs-lookup"><span data-stu-id="8bf4a-113">Type</span></span>|<span data-ttu-id="8bf4a-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="8bf4a-114">Retargeting</span></span>|

