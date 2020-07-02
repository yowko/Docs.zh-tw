---
ms.openlocfilehash: d587e542a72d584502ac3ac892619cc38b88ef77
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619923"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="af513-101">HttpUtility.JavaScriptStringEncode 會逸出 & 符號</span><span class="sxs-lookup"><span data-stu-id="af513-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="af513-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="af513-102">Details</span></span>

<span data-ttu-id="af513-103">從 .NET Framework 4.5 開始，<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> 會逸出 &amp; 字元。</span><span class="sxs-lookup"><span data-stu-id="af513-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="af513-104">建議</span><span class="sxs-lookup"><span data-stu-id="af513-104">Suggestion</span></span>

<span data-ttu-id="af513-105">如果您的應用程式相依於此方法的舊版行為，您可以將 aspnet:JavaScriptDoNotEncodeAmpersand 設定新增至組態檔中的 [ASP.NET appSettings 項目](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="af513-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="af513-106">名稱</span><span class="sxs-lookup"><span data-stu-id="af513-106">Name</span></span>    | <span data-ttu-id="af513-107">值</span><span class="sxs-lookup"><span data-stu-id="af513-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="af513-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="af513-108">Scope</span></span>   |<span data-ttu-id="af513-109">Minor</span><span class="sxs-lookup"><span data-stu-id="af513-109">Minor</span></span>|
|<span data-ttu-id="af513-110">版本</span><span class="sxs-lookup"><span data-stu-id="af513-110">Version</span></span>|<span data-ttu-id="af513-111">4.5</span><span class="sxs-lookup"><span data-stu-id="af513-111">4.5</span></span>|
|<span data-ttu-id="af513-112">類型</span><span class="sxs-lookup"><span data-stu-id="af513-112">Type</span></span>|<span data-ttu-id="af513-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="af513-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="af513-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="af513-114">Affected APIs</span></span>

-<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
