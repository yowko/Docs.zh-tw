---
ms.openlocfilehash: 6f22d6211ec9238fd1c7786643ca95db02bfca64
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496278"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="148ba-101">MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式</span><span class="sxs-lookup"><span data-stu-id="148ba-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

#### <a name="details"></a><span data-ttu-id="148ba-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="148ba-102">Details</span></span>

<span data-ttu-id="148ba-103">從 .NET Framework 4.5 開始，MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式 (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 物件)。</span><span class="sxs-lookup"><span data-stu-id="148ba-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> object).</span></span> <span data-ttu-id="148ba-104">嘗試序列化 MEF 目錄會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="148ba-104">Trying to serialize a MEF catalog throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="148ba-105">建議</span><span class="sxs-lookup"><span data-stu-id="148ba-105">Suggestion</span></span>

<span data-ttu-id="148ba-106">無法再使用 MEF 建立序列化程式</span><span class="sxs-lookup"><span data-stu-id="148ba-106">Can no longer use MEF to create a serializer</span></span>

| <span data-ttu-id="148ba-107">名稱</span><span class="sxs-lookup"><span data-stu-id="148ba-107">Name</span></span>    | <span data-ttu-id="148ba-108">值</span><span class="sxs-lookup"><span data-stu-id="148ba-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="148ba-109">範圍</span><span class="sxs-lookup"><span data-stu-id="148ba-109">Scope</span></span>   |<span data-ttu-id="148ba-110">主要</span><span class="sxs-lookup"><span data-stu-id="148ba-110">Major</span></span>|
|<span data-ttu-id="148ba-111">版本</span><span class="sxs-lookup"><span data-stu-id="148ba-111">Version</span></span>|<span data-ttu-id="148ba-112">4.5</span><span class="sxs-lookup"><span data-stu-id="148ba-112">4.5</span></span>|
|<span data-ttu-id="148ba-113">類型</span><span class="sxs-lookup"><span data-stu-id="148ba-113">Type</span></span>|<span data-ttu-id="148ba-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="148ba-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="148ba-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="148ba-115">Affected APIs</span></span>

<span data-ttu-id="148ba-116">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="148ba-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
