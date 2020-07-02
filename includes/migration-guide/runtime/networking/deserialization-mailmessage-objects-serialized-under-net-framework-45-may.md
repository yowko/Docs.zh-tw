---
ms.openlocfilehash: ad953a1562db407c04d7860c60eb5964fe6fe2ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620037"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="8bd1e-101">將在 .NET Framework 4.5 下序列化的 MailMessage 物件還原序列化可能會失敗</span><span class="sxs-lookup"><span data-stu-id="8bd1e-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

#### <a name="details"></a><span data-ttu-id="8bd1e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8bd1e-102">Details</span></span>

<span data-ttu-id="8bd1e-103">從 .NET Framework 4.5 開始，<xref:System.Web.Mail.MailMessage> 物件可以包含非 ASCII 字元。</span><span class="sxs-lookup"><span data-stu-id="8bd1e-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="8bd1e-104">在 .NET Framework 4 中，僅支援 ASCII 字元。</span><span class="sxs-lookup"><span data-stu-id="8bd1e-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="8bd1e-105">包含非 ASCII 字元且在 .NET Framework 4.5 或更新版本下序列化的 <xref:System.Web.Mail.MailMessage> 物件，無法在 .NET Framework 4 下還原序列化。</span><span class="sxs-lookup"><span data-stu-id="8bd1e-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8bd1e-106">建議</span><span class="sxs-lookup"><span data-stu-id="8bd1e-106">Suggestion</span></span>

<span data-ttu-id="8bd1e-107">請確定您的程式碼在將 <xref:System.Web.Mail.MailMessage> 物件還原序列化時，會提供例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="8bd1e-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>

| <span data-ttu-id="8bd1e-108">名稱</span><span class="sxs-lookup"><span data-stu-id="8bd1e-108">Name</span></span>    | <span data-ttu-id="8bd1e-109">值</span><span class="sxs-lookup"><span data-stu-id="8bd1e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8bd1e-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="8bd1e-110">Scope</span></span>   |<span data-ttu-id="8bd1e-111">Minor</span><span class="sxs-lookup"><span data-stu-id="8bd1e-111">Minor</span></span>|
|<span data-ttu-id="8bd1e-112">版本</span><span class="sxs-lookup"><span data-stu-id="8bd1e-112">Version</span></span>|<span data-ttu-id="8bd1e-113">4.5</span><span class="sxs-lookup"><span data-stu-id="8bd1e-113">4.5</span></span>|
|<span data-ttu-id="8bd1e-114">類型</span><span class="sxs-lookup"><span data-stu-id="8bd1e-114">Type</span></span>|<span data-ttu-id="8bd1e-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="8bd1e-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8bd1e-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8bd1e-116">Affected APIs</span></span>

-<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
