---
ms.openlocfilehash: 598df2121b480d411dac9c5571772a4a8d22b5ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620036"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="9bb9d-101">MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式</span><span class="sxs-lookup"><span data-stu-id="9bb9d-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

#### <a name="details"></a><span data-ttu-id="9bb9d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9bb9d-102">Details</span></span>

<span data-ttu-id="9bb9d-103">從 .NET Framework 4.5 開始，MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式 (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 物件)。</span><span class="sxs-lookup"><span data-stu-id="9bb9d-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> object).</span></span> <span data-ttu-id="9bb9d-104">嘗試序列化 MEF 目錄會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9bb9d-104">Trying to serialize a MEF catalog throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9bb9d-105">建議</span><span class="sxs-lookup"><span data-stu-id="9bb9d-105">Suggestion</span></span>

<span data-ttu-id="9bb9d-106">無法再使用 MEF 建立序列化程式</span><span class="sxs-lookup"><span data-stu-id="9bb9d-106">Can no longer use MEF to create a serializer</span></span>

| <span data-ttu-id="9bb9d-107">名稱</span><span class="sxs-lookup"><span data-stu-id="9bb9d-107">Name</span></span>    | <span data-ttu-id="9bb9d-108">值</span><span class="sxs-lookup"><span data-stu-id="9bb9d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9bb9d-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="9bb9d-109">Scope</span></span>   |<span data-ttu-id="9bb9d-110">主要</span><span class="sxs-lookup"><span data-stu-id="9bb9d-110">Major</span></span>|
|<span data-ttu-id="9bb9d-111">版本</span><span class="sxs-lookup"><span data-stu-id="9bb9d-111">Version</span></span>|<span data-ttu-id="9bb9d-112">4.5</span><span class="sxs-lookup"><span data-stu-id="9bb9d-112">4.5</span></span>|
|<span data-ttu-id="9bb9d-113">類型</span><span class="sxs-lookup"><span data-stu-id="9bb9d-113">Type</span></span>|<span data-ttu-id="9bb9d-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="9bb9d-114">Runtime</span></span>|
