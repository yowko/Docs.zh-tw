---
ms.openlocfilehash: 2c44c2e1658f8de556d3f7222de3fa6d4594163a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496617"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="df1d9-101">將在 .NET Framework 4.5 下序列化的 MailMessage 物件還原序列化可能會失敗</span><span class="sxs-lookup"><span data-stu-id="df1d9-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

#### <a name="details"></a><span data-ttu-id="df1d9-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="df1d9-102">Details</span></span>

<span data-ttu-id="df1d9-103">從 .NET Framework 4.5 開始，<xref:System.Web.Mail.MailMessage> 物件可以包含非 ASCII 字元。</span><span class="sxs-lookup"><span data-stu-id="df1d9-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="df1d9-104">在 .NET Framework 4 中，僅支援 ASCII 字元。</span><span class="sxs-lookup"><span data-stu-id="df1d9-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="df1d9-105">包含非 ASCII 字元且在 .NET Framework 4.5 或更新版本下序列化的 <xref:System.Web.Mail.MailMessage> 物件，無法在 .NET Framework 4 下還原序列化。</span><span class="sxs-lookup"><span data-stu-id="df1d9-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="df1d9-106">建議</span><span class="sxs-lookup"><span data-stu-id="df1d9-106">Suggestion</span></span>

<span data-ttu-id="df1d9-107">請確定您的程式碼在將 <xref:System.Web.Mail.MailMessage> 物件還原序列化時，會提供例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="df1d9-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>

| <span data-ttu-id="df1d9-108">名稱</span><span class="sxs-lookup"><span data-stu-id="df1d9-108">Name</span></span>    | <span data-ttu-id="df1d9-109">值</span><span class="sxs-lookup"><span data-stu-id="df1d9-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="df1d9-110">範圍</span><span class="sxs-lookup"><span data-stu-id="df1d9-110">Scope</span></span>   |<span data-ttu-id="df1d9-111">Minor</span><span class="sxs-lookup"><span data-stu-id="df1d9-111">Minor</span></span>|
|<span data-ttu-id="df1d9-112">版本</span><span class="sxs-lookup"><span data-stu-id="df1d9-112">Version</span></span>|<span data-ttu-id="df1d9-113">4.5</span><span class="sxs-lookup"><span data-stu-id="df1d9-113">4.5</span></span>|
|<span data-ttu-id="df1d9-114">類型</span><span class="sxs-lookup"><span data-stu-id="df1d9-114">Type</span></span>|<span data-ttu-id="df1d9-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="df1d9-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="df1d9-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="df1d9-116">Affected APIs</span></span>

- <xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.Mail.MailMessage`

-->
